---
title: "Offering downloads without giving away the cow"
author: "Nic Ollis"
date: 2017-02-22T15:02:01.783Z
lastmod: 2023-01-19T07:12:09-06:00

description: "So I had an interesting user story the other day. I was asked to implement a new system that would allow users to pay for and download some of our templates.  This is all pretty well and easy thanks…"

subtitle: "Masking storage url of paid for content behind your own custom url."

image: "/posts/2017-02-22_offering-downloads-without-giving-away-the-cow/images/1.jpeg" 
images:
 - "/posts/2017-02-22_offering-downloads-without-giving-away-the-cow/images/1.jpeg"


aliases:
    - "/offering-downloads-without-giving-away-the-cow-910998abf21"

---

![image](/posts/2017-02-22_offering-downloads-without-giving-away-the-cow/images/1.jpeg#layoutTextWidth)


So I had an interesting user story the other day. I was asked to implement a new system that would allow users to pay for and download some of our templates.

This is all pretty well and easy thanks to Stripe and their Rails API. However we needed a way to allow users to download the templates using a key that expires a week after purcahse and doesn’t provide the user with the storage URL of the template. So thats what I wanted to show a way you can provide the download without giving away the proverbial cow.

Starting off with this we are going to assume a few things. We are using Ruby on Rails, Uploading is done via CarrierWave (although most of what we will show it doesn’t matter), and we are using Pundit for Authorization.

Let’s first talk about the routes we will be working with. Our coding is pretty easy. For the scope of this post we will just focus on the download page logic and nothing to do with purchaing.

*   /template/:id/download/:purchase_key # Secured page with download buttons
*   /template/:id/download/:purchase_key/[pdf/psd] # route responsaible for serving up the requested document`resources :template, only [:show, :update] do  
  resources :download, only [:show] do  
    collection do  
      get &#39;:id/pdf&#39; =&gt; download#pdf, as: :pdf  
      get &#39;:id/psd&#39; =&gt; download#psd, as: :psd  
    end  
  end  
end`

With the routes shown above we should be linked to our controller where all the action happens. First thing we will want to do is ensure the use has a valid key to even be on our downloads page.

`before_action :find_purchase`
`def find_purchase  
  unless  (@purchase = PurchaseRecord.find_by(key: param[:id])  
    flash[:error] = &#34;Can&#39;t find purchase.&#34;  
    redirect_to template_path  
  end  
end`

This is a quick and easy check for the purchase record and if one is not found we just send the user somewhere else. However if one is found we make it an instance varable so we have access to it in the rest of our calls.

It’s also worth noting we will be using pundit for authorizing the downloads. All pundit is doing is verifying the purchase experation date has not passed if so we do a simlar redirect like above but with a flash message that reflects the expired key.

Now for the part you have probably scrolled down to the bottom to get to as my rambling has gotten the best of you.

To do the secure download we can use a few different methods. The easiest would be either send_data or send_file. I prefer send_data as we can just stream the data to the user. If we go with the send_file method we would need to download the template to our server via a tmp file then send that over. To me this seems like wasted stress on the system.

As we have two methods that need to use simliar code I decided to dry it out with its own method that they both can call. An example for the PSD would be.
`def psd  
  authorize @purchase  
  send_template @purchase.psd_template.url, @purchase.psd_template_identifier  
end`

This sends our private url and the file name over to the method send_template to handle the buffer. Sending via the buffer is extremely easy.
`def send_template(url, filename)  
  data = open(url)  
  send_data data.read, filename: filename, disposition: &#39;inline&#39;, stream: &#39;true&#39;, buffer_size: &#39;4096&#39;  
end`

With this method we now have an easy way to send the file over without the user ever seeing the real url of the file. While we take a small hit to facilitate the download over all its not to bad for the security of the file. If we also decide for more analitics we can also add in a tracker to the psd and pdf methods so we can track how often they are being downloaded and get some alalitics on our downloads that we couldn’t get before with the old method of giving the users links that we didn’t control.

As a bonus if you are using CarrierWave with something like S3 storage you can override the fog_public method in your PDF/PSD uploaders to make the files private in your bucket to only allow your server to grab them.
`def fog_public  
  false  
end`

By putting this method in just your uploader your other uploaders like avatar and general images wont be locked down as they would be if you made this change in the CarrierWave documentation.

As always thanks for reading, and follow me on [twitter](https://twitter.com/nic_ollis) for more daily updates, live stream alerts, and post on my journey of software development. Subscribe to the Program Practical channel on [YouTube](https://www.youtube.com/c/Programpracticaltv). Feel free to ask any questions in the comments below, and don’t forget it’s always a good time to start to #LearnToCode
