# alexa-youtube
**Unofficial YouTube skill for Alexa**

## Updates
* 2nd June 2018: The skill now handles playlists or channels where none of the videos exist (eg copyrighted deletions). It will now ask you if you want to try the next playlist or channel. If you have already created the skill, you will need to update the Interaction Model json file in your Alexa skill, ie step 7 under Setup Instructions.
* 22nd August 2018: Fixed a bug where channels turn up in video search results, eg in Play videos by The Beatles.
* 4th January 2019: Now works in 5 languages, thanks to everyone who helped!

## Features
* Play audio (currently no video) from YouTube videos
* Live videos are supported as much as possible

## Skill Commands

1. Play a video, eg "Alexa, ask YouTube to play Gangnam Style"
2. Play a playlist, eg "Alexa, ask YouTube to play playlist Ultimate Beyonce"
3. Play a channel, eg "Alexa, ask YouTube to play channel Fall Out Boy Vevo"
4. You can replace "play" with "shuffle" to get a randomized version of the search results/channel/playlist, eg "Alexa, ask YouTube to shuffle channel Nicki Minaj"
5. Next / Previous / Start Over / Pause / Resume should all work
6. Ask what is playing by "Alexa, ask YouTube what song is playing" (or just "Alexa, can you repeat that?" should tell you)

## Known issues

1. Some videos just fail, it's not clear why, they work locally. The skill just moves to the next video on the playlist, but this can mean sometimes she announces a video that doesn't play.
2. It doesn't play video, because I don't have an Echo Show or Echo Spot to test on. If you want to buy me one, get in touch!
3. Apparently it doesn't work on Sonos devices. Sorry about that, email Sonos and ask them to support mp4.

## Setup Instructions

1. Go to the Alexa Console (https://developer.amazon.com/alexa/console/ask)
2. If you have not registered as an Amazon Developer then you will need to do so. Fill in your details and ensure you answer "NO" for "Do you plan to monetize apps by charging for apps or selling in-app items" and "Do you plan to monetize apps by displaying ads from the Amazon Mobile Ad Network or Mobile Associates?"
3. Once you are logged into your account click "Create Skill" on the right hand side.
4. Give your skill any name, eg "My YouTube Skill". Set the language to whatever your Alexa is set to, but currently English (any), French, Italian, German and Spanish (any) are supported.
5. Choose "Custom" as your model, and click "Create Skill".
6. On the left hand side, click "JSON Editor".
7. Delete everything in the text box, and copy in the text from https://raw.githubusercontent.com/ndg63276/alexa-youtube/master/InteractionModel_en.json, (or use InteractionModel_fr.json, InteractionModel_it.json, InteractionModel_de.json, InteractionModel_es.json for French, Italian, German or Spanish)
8. Click "Save Model" at the top.
9. Click "Interfaces" in the menu on the left, and enable "Audio Player". Click "Save Interfaces".
10. Click "Endpoint" in the menu on the left, and select "AWS Lambda ARN". Under "Default Region", put:

```
arn:aws:lambda:eu-west-1:175548706300:function:YouTube
```

11. Click "Save Endpoints"
12. Click "Invocation" in the menu on the left.
13. If you want to call the skill anything other than "youtube", change it here. Click "Save Model" if you change anything.
14. Click "Build Model". This will take a minute, be patient. It should tell you if it succeeded.
15. **Important:** At the top, click "Test". Where it says "Test is disabled for this skill", change the dropdown from "Off" to "Development". 

That's it!

## Deploying yourself (optional, advanced)
This skill currently runs on my Lambda instance, hopefully it won't get too popular. If you want to, and know how, you can deploy it on your own Lambda, you just need the lambda_function.zip file, and a YouTube developer key. (See [here](https://www.slickremix.com/docs/get-api-key-for-youtube/)).

[tal9000v2](https://github.com/tal9000v2) has put together a handy guide for deploying yourself [here](https://github.com/ndg63276/alexa-youtube/issues/15#issuecomment-447684487).

## FAQ
* **Alexa tells me she can't find any supported video skills, what does that mean?**
Alexa is trying to be too clever, and not launching this skill. Start your request by saying 'Alexa, open YouTube' and then when she says 'Welcome to YouTube', ask for the video you want.
* **She still says she can't find any video skills.**
Make sure to follow step 15 above, enabling Testing for Development.
* **I am getting another issue, can you fix it?**
Hopefully. Create an issue on github, with the exact wording of what you ask Alexa, so I can try and reproduce it.
* **Can you add another language?**
Yes, as long as you can translate for me. Click on 'Issues' at the top, then 'New Issue', and let me know what language you can help with, and I'll let you know what I need translating.
* **If I try and test in the Developer Console, it says 'Unsupported Directive. AudioPlayer is currently an unsupported namespace. Check the device log for more information.'**
That is normal, the Developer Console doesn't play audio. You just need to enable testing through the Developer Console, then you can use the skill through your Alexa device.


