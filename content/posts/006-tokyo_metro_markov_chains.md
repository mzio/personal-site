---
title: "Lost in Japan with Reflections and a Side Project"
date: 2019-01-22T23:18:03-05:00
draft: false
summary: "Remembering time in Tokyo with Markov chains..."
preview_image: "006-tokyo_metro_markov_models-preview.png"
project: false
project_date: January 22, 2019
project_link: "http://michaelzhang.xyz/tokyo-metro-markov-models/"
tags: ['data science', 'data visualization', 'personal']
---
Winter break's been a long one. By now I've gotten used to being out of school, but it's hard to think that four weeks ago I was in Japan. Family's been on a traveling kick lately, and this year we spent ten days between Tokyo, Kamakura, Hakone, Shanghai, and Beijing.

Although I'd been to Tokyo for some epsilon-long layovers before, and this time our time in Japan could probably still only be considered a layover (3 out of 10 days woo), I'd still consider the recent trip to be the first time I really got to see the country. 

<figure>
  <img src="/images/006-tokyo-shibuya.jpg"  />
  <figcaption style="text-align: center">
      <i>Wandering among the bright lights of Shibuya crossing one night</i>
  </figcaption>
</figure>

And it was a blast. For some reason, the combination of really great food and a new culture was just really fun. Sure there were similarities with Shanghai (bright lights, crowded streets, general feeling of being in the future). But the differences were also there in a readily-apparent-but-not-so-describable way. 

<!-- {{< figure src="/images/006-tokyo-daifuku.jpg" title="So much strawberry daifuku! Perhaps ironically taken at the Tsukiji outer fish market"  >}} -->

## Wow a popular song song reference?

Aside from the song title reference, perhaps unsurprisingly we actually did get lost on several occasions. Trying to fill up some time before our check-in at an onsen in Hakone, we decided to take a train to Kamakura along the way, a smaller city south of Tokyo right by the ocean. Depending on perspective I guess it could be called exploring, but essentially we were a lost group of foreigners wandering around a coastal town not exactly knowing what we were doing. 

<figure>
  <img src="/images/006-tokyo-kamakura.jpg"  />
  <figcaption style="text-align: center">
      <i>And the next just randomly in the streets of Kamakura</i>
  </figcaption>
</figure>

<!-- {{< figure src="/images/006-tokyo-kamakura.jpg" title="Streets of Kamakura" >}} -->

We also technically got lost immediately upon landing in Tokyo Narita International Airport. The [third definition on Dictionary.com](https://www.dictionary.com/browse/lost) involves "having gone astray or missed the way". You can imagine after enduring a 13 hour flight and passing through customs (which surprisingly wasn't that bad) how eager we were to finally get to our hotel, find some place to eat, and immediately... 

...step onto the wrong train.

<figure>
  <img src="/images/006-tokyo-lost_train.jpg"  />
  <figcaption style="text-align: center">
      <i>Google Maps said take something called the Skyliner, but apparently it's possible to think you're getting on and end up on something that's not the Skyliner?</i>
  </figcaption>
</figure>

<!-- {{< figure src="/images/006-tokyo-lost_train.jpg" title="Google Maps said take something called the Skyliner, but apparently it's possible to think you're getting on and end up on something that's not the Skyliner?" >}} -->

Needless to say, we got to know a lot of trains by the end of the trip. It's pretty amazing to me how extensive the subway system is in Tokyo, and you can take trains everywhere! I know this isn't unique to the city, but what is pretty cool is that at certain stations, trains will play these jingles, or "_eki-melo_" when they arrive. I actually knew about their existence from a [Great Big Story video](https://www.youtube.com/watch?v=nSG5IkRA9BE) (Minoru Mukaiya, the guy behind the songs, has made over 200 distinct melodies for over 110 stations!), so it was a lot of fun hearing them come on at various stops.

## Metros and Markov Models

While I've never been one to really hold myself accountable to New Year's Resolutions, two things I'm actively trying are being more active with this blog and do more side projects. Along these lines, I wanted to do something related to my time in Japan. 

Eki-melo really stood out, and while the coverage is pretty extensive, there's not exactly a uniquely melody for each station yet. I had thought about playing around with something like [MusicVAE](https://magenta.tensorflow.org/music-vae) to generate new tunes for stations without their unique songs yet (one idea: for each station without a unique melody learn a distribution that's essentially the interpolation between the first two neighboring stations with unique eki-melo). However, I also wanted to use open data, and deal with an extensive set of stations. While Tokyo's actually got a really exciting [repository of open data](http://www.data.go.jp/?lang=english), it'd take a little more work to find / purchase the eki-melo. At the same time, I actually hadn't made a moving particle map thing, although I've seen a lot of awesome examples, and so with past work as inspiration I created the visualization as a weekly side project.

The goal was pretty simple: use open transit data to inform a visualization about travel on a regular day. Ideally, tie in some stats or probability. So instead of just replaying back data, use the data to create some sort of simulation. I hope to go more into the technical details in a follow-up post, but the general idea I settled on was to assume some sort of Markov model for transit. Each station could be a node in a larger Markov chain, and so a task would be to infer transition probabilities to the neighboring stops. To consider changes in travel patterns over time, I'd switch between possible transition matrices depending on the hour. Finally, with D3 and React, I envisioned some sort of web app where particles representing travelers could randomly spawn at any stop, and go off moving to different neighboring stops following the larger transition matrix. 

<figure>
  <img src="/images/006-tokyo_metro_markov_models_demo.gif"  />
  <figcaption style="text-align: center">
      <i>Tokyo Metro Markov glowy bois</i>
  </figcaption>
</figure>

## Keeping up with these resolutions  
I spent about two days deciding what data to use and building up the models in Python, and the rest of a week playing around with D3, React, and pretty-ing things (although it's still not very mobile-optimized). It's up and running [here](http://michaelzhang.xyz/tokyo-metro-markov-models/), or click on the view project button on the project page.

I'd like to set a goal to do something low-key like this every week or every-other week this year, but something else tells me the semester might get super busy. Regardless, it was super fun, and a nice way to rediscover some of winter break.

<figure>
  <img src="/images/006-tokyo-daifuku.jpg"  />
  <figcaption style="text-align: center">
      <i>Ending with obligatory food pic related to time abroad. So much strawberry daifuku! Perhaps ironically taken at the <a href="https://www.japan-guide.com/e/e3021.html">Tsukiji outer fish market</a>.</i>
  </figcaption>
</figure>
<!-- 
{{< figure src="/images/006-tokyo_metro_markov_models_demo.gif" title="Tokyo Metro Markov glowy bois" >}} -->

