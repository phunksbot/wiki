---
description: if you feel Phunky and want to be Creative
---

# ▫ MEDIA KIT

## CryptoPhunk Viewer

Start by clicking on "Run Pen", change scale to 0.25x for compact preview and enter your Phunk ID.\
You can also change background colour by choosing one below, download will only extract phunk not the background. You can always zoom in and screenshot it.&#x20;

{% embed url="https://codepen.io/phunksbot/pen/LYeLeWp" %}
PHUNK VIEWER
{% endembed %}

{% hint style="info" %}
For Phunk Custom PFP (Profile Picture) use [**Phunk Box**](../../nll/notlarvalabs/tutorials.md#tutorials) by [**NotLarvaLabs**](../../nll/notlarvalabs/).
{% endhint %}

## Phunk Collage

All 10'000 Phunks in one Collage, this collage is very scalable when viewed locally on your PC. \
Just Right Click and Save, then zoom in to the max.

![PHUNK COLLAGE](../../.gitbook/assets/phunks-all.png)

## Download All

Here is tutorial how to download all 10'000 Phunks each as a separate jpeg with Phunk #ID \
in 24x24 and in 192x192 (8x) format.

{% embed url="https://old.reddit.com/r/CryptoPunksDev/comments/s4hyny/q_how_can_i_generate_10_000_leftlooking_phunks_in" %}

Change the loop in the [phunks script](https://github.com/cryptopunksnotdead/cryptopunks/blob/master/phunks/phunks.rb) from:

```
punks.each do |punk|
  phunks << punk.mirror    #¹ 
end
```

to save the phunks one-by-one in 24x24 and in 192x192 (with 8x zoom) try:

```
punks.each_with_index do |punk,i| phunk = punk.mirror
  phunk.save( "phunk-#{i}.png" ) 
  phunk.zoom(8).save( "phunk-#{i}@8x.png" )
  phunks << phunk ## add to composite
end 
```

(Re)run the script and voila - you will get 20 000 phunk images in two series in the 24x24 and 192x192 (with 8x zoom) format e.g. `phunk-0.png`, `phunk-0@8x.png`, `phunk-1.png`, `phunk-1@8x.png`, and so on.

[Questions and comments welcome.](https://old.reddit.com/r/CryptoPunksDev/comments/s4hyny/q\_how\_can\_i\_generate\_10\_000\_leftlooking\_phunks\_in/)
