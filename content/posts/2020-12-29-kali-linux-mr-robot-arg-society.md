---
title: "Kali Linux Mr Robot ARG Society"
date: Tue, 29 Dec 2020 00:00:00 +0000
draft: false
type: posts
---
# Kali Linux Mr Robot ARG Society

https://www.kali.org/blog/mr-robot-arg-society/images/kali-mr-robot-augmented-reality-game-1.jpg



Many of you may have known about the show Mr Robot and its unique connection to Kali Linux. But there is a little bit more that we have not talked about due to NDAs. But it appears the mystery is over, the red tape has been removed, and we now

Many of you may have known about the show [Mr Robot](https://www.usanetwork.com/mr-robot) and its unique connection to Kali Linux. But there is a little bit more that we have not talked about due to NDAs. But it appears the mystery is over, the red tape has been removed, and we now wanted to take a moment to share it with everyone.

We had a relationship with Mr Robot, which started during the filming of the 2nd season. While the 1st season was running, we were approached at BlackHat 2015 to give our permission to use Kali in the show. We worked out the legal parts of things (it’s legal to use Kali in media, we don’t care, but studios want that in writing), and starting in the 2nd season from time to time the production staff would reach out to us to ask us questions, have us provide them graphics, provide them with specific versions of Kali that were public on specific dates, and similar to keep the show accurate. We were very impressed with the efforts to keep the show grounded while still carrying on a strong hacking focused narrative.

Mr Robot has an “Alternative Reality Game (ARG)” that has been part of the show from the [start](https://wiki.gamedetectives.net/index.php?title=Mr._Robot_ARG). The idea is that as you watch the show, you watch for clues and the clues from the show go into the game and you solve puzzles etc. The production staff wanted us to be part of this ARG and help them on their final step of the puzzle to be tied into the last episode. The final episode aired December 2019, but the puzzle was only recently finally solved.

You can read the gory details of the [final answer](https://www.reddit.com/r/ARGsociety/wiki/index#wiki_post_season_4_.2F_series) if you are interested. The idea was, we would do a commit to the Kali Git repository that would include a number of items, but also have a surprise. The commit we made was the initial commit of the “[Legacy Wallpapers](https://gitlab.com/kalilinux/packages/kali-legacy-wallpapers)” where we took the [old Kali](https://www.kali.org/docs/introduction/kali-linux-history/) and [BackTrack](https://www.backtrack-linux.org/) wallpapers and made them available to everyone. However, [embedded in one of the images](https://gitlab.com/kalilinux/packages/kali-legacy-wallpapers/blob/kali/master/kali-1.1/kali-1.1-1280x1024.jpg/) was a steganographic message which was a private SSH key. This is the same background image that was used throughout the show’s filming.

With a password, the SSH key could be extracted from that image. Then with that, players of the ARG could use it to connect to a “final target”.

How would anyone find that one graphic? The clues in the ARG that lead them to it included a call out to “OffSec”, the Kali GitLab group ID, the project ID for the Legacy Wallpapers, and the specific commit where we had uploaded the special wallpaper.

Now the mystery is over, the final problem is solved, and the last door on Mr Robot is finally closed. It was awesome being even a small part of the show, and we loved the respect that the show paid to keeping everything based in reality.

Goodbye friend.

#### Mr. Robot ARG Society

Any show would be nothing without an audience to watch it. Mr Robot is no exception, and after millions of people watched it, communities started to formed (either online or in person). People would discuss previous episodes, predict theories of where the show was going to go, and have watching parties. Its not un-common for shows to have “Easter eggs” embedded in them (these can be are little gems hidden in plain sight, which may give a “head nod” to something, or a spoiler for a up coming event). They are hunted after by people, and adds another level of excitement to re-watch a show. Mr Robot has plenty of them. But where Mr Robot is unique to any other show out, there is _(for the time being)_ an various online elements which links beautifully back into the show. In a sense, these are mini “spin offs” to the show, allowing for people to go further, get interactive and solve challenges in the Mr Robot universe. One _(of a few)_ domains is “[Who Is Mr Robot](https://www.whoismrrobot.com/)”, which is where there was a lot of focus to solve its challenge(**s**). This was made up of a collection of virtual terminals all from the show, which has a series of technical challenges to solve.

There were multiple groups of people working towards _(either group of friends doing it privately, or people who started out to be strangers coming together doing it publicly)_, a lot of people started trying to answer, but not many made it all the way to the end of Season 4. Finally after over a year of trying, someone got the final part, ARGSociety. We want to reach out and get their view of the show & challenges. We found their [subreddit](https://www.reddit.com/r/ARGsociety/) and later joined their [discord](https://discord.com/invite/2ERCJa2). It was immediately apparent how close of a community these people are, not only how active but how passionate they are about the show (and still are). People didn’t know each other before joining, but they were all welcoming, humble, and they all had a part to play in solving the puzzle. After chatting to everyone one of the members, [BK](https://twitter.com/B4815162342K), was selected to be in interviewed on behalf of everyone in the group.

* * *

**Q.) Why the show Mr Robot?**

> Mr Robot shouted out to the world: I am here now, and “your democracy has been hacked”. The premise was enough to make me curious. Myself and the other leaders of this crazy community (Carnage Beam and Risk), had no clue what any of us were about to get into.

**Q.) Did you start watching it from the start?**

> I hadn’t even seen so much as a trailer for this show when I started it. Aside from a poster of this dude in a hoodie, I went in blind. But USA network allowed the pilot episode to be viewed about a month or so earlier than its on air premiere date. So by the time the pilot had aired, I think I had already rewatched that single episode 4 or 5 times.

**Q.) What was your favorite season from the TV show?**

> Picking a favorite season of Mr Robot is like trying to pick a favorite family member. I love them all in their own unique ways.
> 
> Season 1 offered us a hacking adventure show, almost fit with our very own “hack of the week” (usually a procedural trope I mostly loath). And as someone who wasn’t familiar with the hacking world, I walked into Mr Robot season 1 as an undergrad and by episode 10, I felt like I had my degree. At the same time it became evident as each episode aired, that this was so much more than a hack of the week show. It was the character driven drama that kept me week to week.
> 
> Season 2 became a mirror into the soul; Elliot’s soul, and ours. It was slower paced, and with Elliot unable to hack for about half the season, Esmail was able to take deep dives into his characters’ minds. Season 2 was polarizing, but for those that stuck with it, perhaps the most rewarding.
> 
> Season 3 became this high octane combination of season 1 and 2. We stood and watched as we got hacks, evil antagonists with master plans, all the tears, and most importantly, we got deeper into the psychology of Elliot Alderson. As Elliot hacked his way through season 3, we learned more and more about who this Elliot guy really was.
> 
> Then Sam delivered season 4. Fulfilling a show long promise that we the audience would finally understand the “whys” for everything that had transpired on the show.
> 
> How could I ever pick one member of the family over another?

**Q.) Did you watch the show by yourself or with people in the same room or virtually?**

> I had broken my foot and was subsequently dumped that same summer Mr Robot first aired. So for season 1, I was watching alone in a bed with my leg in a boot (I honestly think Sam Esmail would agree this method of watching helped me live inside Elliot’s brain a bit more). At the time, I browsed Reddit for other shows I watched like “The Leftovers” or “LOST”. And I found the Mr Robot subreddit sometime in the middle of that summer. It’s where I first learned people were catching background items in the show that I had seen as well and trying to group think just what those items may mean overall. I was hooked.

**Q.) Hacking is such a boring thing to watch, how did the shot make it interesting to you?**

> This, I thought, would be the easiest question to answer. Because I do represent that part of the audience that has NO CLUE how to hack. It’s foreign to me in every way. Yet there I was week after week, trying to understand more and more of just how Elliot could pull some of these hacks off. There are three different types of viewers out there: Those who can hack, those who cant but understand what’s going on, and those who don’t know how to use hotkeys. I was the latter. I think the most important thing Esmail did for the hacking world and how it is represented on TV was–he didn’t sugar coat anything. He showed us EXACTLY what hacking was. No TRON city file directories in this show. He didn’t need to spice up or dumb down what hacking was to deliver it to his audience–no need. The respect he showed carried over to me as an ignorant audience member.

**Q.) What’s your favorite hack from the show?**

> My favorite hack was one of the more simple in all of the show’s hacks (rich coming from someone who cant hack to call anything done in this show simple). There’s a moment at the end of season 1 (I won’t spoil it in case some people have been living under a rock) where Elliot needs to hack a blank CD with audio files. This rudimentary hack was shot beautifully with Rami’s amazing acting center stage. Then the music kicks into high gear as we are with Elliot in the moment. He cried–we all cried. It was this moment near the end of season 1–I realized this show was gonna change things about TV.

**Q.) Would you call yourself a hacker (pre or post show)? What do you do for your day job?**

> I would not call myself a hacker. I think every single person in the Mr Robot ARG community would attest that I was the quintessential non-hacker of the community. Carnage Beam and Risk on the other hand were our experts, in addition to being part of the leadership team.
> 
> When the show started I was still in professional sports advertising. By the time the show ended, I moved back to Los Angeles to be a writer.

**Q.) Had you used Kali Linux before?**

> I hadn’t so much as heard of Kali Linux, let alone used it prior to Mr Robot.

**Q.) What did you think of the ending?**

> This is like kicking a hornet’s nest. I loved the ending. I hated the ending. And then I loved it all over again. Endings are damn near impossible these days. Writing a mystery? Groupthink from Reddit most likely already figured it out 8 episodes ago. Writing an epic adventure? Better not have one of your big bads die with a glass of wine in their hand staring off in the distance. What Sam did in the final season was almost take the onus off the “ending”. He gave us answers throughout that final season, allowing us to just enjoy the final chapter of the story as best we could knowing it was all coming to an end.
> 
> Something the end of Mr robot captured was spirit. As Elliot’s journey was ending, ours was too. Despite all the crazy hacks, storylines and complex problems Elliot got himself into, most of all we all just wanted to see this crazy hacker find peace. I think Sam accomplished that with flying colors.

**Q.) How many times have you seen the show now?**

> Well you’re talking to a member of ARGsociety. I think the average member has rewatched each season at least 2 or 3 times. Personally I have seen each season anywhere from 15-20 times. I am a theorizer. A graduate with a PhD from the theory school of LOST. If the show really has meat on the bones, you’ll find yourself learning or catching something new each watch.
> 
> Now add in the puzzles. Scanning episodes over and over and over again, scrupulously looking for easter eggs or QR codes. Or looking for that one item Sam placed in the background to be found only upon a rewatch.

**Q.) Aware of any other easter eggs in the show?**

> Well, that was the beauty of this show. It demanded we look at, and question, everything. And that’s exactly what we did. The line blurred so much it was hard to tell what was an actual easter egg and what wasn’t.
> 
> Fun fact, Sam said there’s still an easter egg or two to be found from the show. Granted we may have already found whatever he’s talking about, or maybe not… but I think there will always be a mystery or two left to be solved in Mr Robot.

**Q.) When did you start to partake in solving the puzzle (WHoIsMrRobot.com)?**

> After the CD hack at the end of season 1. Seeing as I wasn’t a hacker, I wasn’t sure what it was I was actually seeing on screen in terms of interactive ARG material. It took watching Elliot do something as innocuous as the CD hack for me to wonder “hey what was that password he used? Am I supposed to figure it out?” I jumped on Reddit and found our group, ARGsociety, still in its infancy. Leading me to the infamous wimr (whoismrrobot.com).

**Q.) Can you explain what it was like when you solved any part of the challenges?**

> If I pretended to answer this like I myself solved any part of the puzzle, our community of thousands would collectively laugh their butt off. I helped when I could, but most of our solves were figured out together. We painstakingly would discuss what and where answers could be found. Fellow leadership would try and explain the fundamentals of different ciphers and how to spot them, in an effort to advance in the game. But this group of puzzle solvers was never satisfied until we beat each season as a whole. We never celebrated (or slept) until every single puzzle was solved and the story for that season’s ARG was complete.

**Q.) What was your favorite part of the interactive puzzle?**

> Personally for me, it was the world blending. According to the show we, the audience, were inside the mind of Elliot. The interactive ARG websites helped cement that notion. It felt like we were really living in Elliot’s universe with every URL or QR code we would find.

**Q.) Would you partake in solving another show’s interactive puzzle?**

> I would in principle. However it would need the perfect blend that Mr Robot provided. There’s a fine line between marketing material, simple interactive game, and world blending ARG. Other shows have tried to pass off superfluous marketing material as some kind of makeshift ARG and they’d lose me, Carnage, Beam, and Risk off the bat. In fact that kind of laziness in the world building would make me stop watching the show altogether. A few shows can get it half right and really do put time and effort into their ARG–but there’s no world blending. It just feels like you’re solving a game that has no bearing on the actual substance of the show you’re watching. Mr Robot captured the exact right amount of magic to make their ARG blossom.

**Q.) What advice would you give to a TV show/movie producer who is wanting to create an interactive “puzzle”?**

> Almost a see above answer here. I would repeat what I heard Sam Esmail say about his ARG: “If we’re gonna do this–we do it 100%”. Don’t half ass it. There is a unique opportunity for show creators and producers by developing an ARG world, one that I think a lot have shied away from.
> 
> On that token, I would also say Esmail could have done even more. To be clear: he gave us this game and we couldn’t be more grateful. He melded us into his universe with precision–he knowingly or unknowingly created a community of die hard fans for life. Ones that were hopping back to Amazon prime to rewatch an episode because they’re looking for 2 more digits to an IP address they missed. It doesn’t take a genius to know what that can mean for view counts, strategic advertising, and word of mouth. But by the end of the show, we kind of did feel left out in the dust a bit. 1000s of hours were invested into his universe, and I dare say we would all do it again in a heartbeat. But it felt like we were pen pals waiting for a letter that never came. This isn’t a slight against Sam or the larger audience as a whole. But there was only one group of a few thousand people walking, talking, sleeping, and breathing Mr Robot–that was ARGsociety. I know that when I write a TV show, those are the fans I’ll be giving back to the most.

**Q.) What are you going to do now? After rewatching the show another time that is!**

> I’m going to continue to write my ass off until I feel like I somehow know what I am doing. Kind of like how I handled hacking and the ARG for Mr Robot! Then the next step is figuring out how to incorporate an ARG of my own into a show I have cooking up.

**Q.) At what stage did you create the community?**

> We began as a subreddit. I joined leadership at that stage–right around the start of 2017. We also had an IRC where we would try and chat in real time but it was never too effective in communication. We hit about 3 or 4 thousand members on the Reddit (most of which active) before we ballooned, prior to season 3. Each seasons’ ARG came with a prize. And the prize for solving season 2–was that your name would be put into the show on one of the many hacking screens we see. Some of us were lucky enough to be included in the Mr Robot universe for life–a prize no one can ever take away. A true honor. So once word of this very interactive prize spread–our numbers ballooned.
> 
> It was there we decided to move our puzzle solving from the post/reply world of Reddit to the real time organized conversation style of Discord. I’m a millennial in my mid 30s. Discord reminded me of the old school AOL chat rooms–and it felt like the perfect platform to solve ARGs with. As a leader of the community–I felt the move to discord would not only strengthen our puzzle solving abilities, but also allow the Mr Robot community as a whole, a place to meet and actually get to know one another.
> 
> Both our Reddit and discord have continued to grow beyond the show’s end. Between the two we have roughly 10,000 or so members.

**Q.) Would you say the people here are now good friends, keep in touch, friends for life?**|

> I’d say that varies with every member in the group, right? Lots of our numbers lurk in the background–yet keep an active status in the discord server. People come and go with discord servers all the time. Yet in ours, it seems people like to stay. Even some of the ARG team that developed the game itself, have become members of the community.
> 
> Those of us active every day, are friends for life. I don’t see anyone going anywhere anytime soon. We have people from all walks of life on that server. I don’t travel to other discord servers all too much, but I have to imagine we have one of the most inclusive servers in all of the internet. We have members on every continent, speaking 24 hours a day. Cis, trans, nerds, jocks, hackers, jokesters, drinkers, smokers, midnight tokers. Not only are we friends, but in this new COVID world we might even be the future.

**Q.) We like to give credit where its due. Who helped you?**

> Hmm, it was largely a group effort. Some key solvers–and by key I mean, without them, we might still be stuck on those puzzles they solved, even today… were @obafgkm, @cr4mb0, [RipVanWinkle](https://twitter.com/SteveRipple), @PunkAB, and [Bogie](https://twitter.com/bogie) among others. [Willvoid](https://www.reddit.com/user/willdroid8) did stellar work keeping the ARG map/timeline updated with every solve we made. Allowing new members easy access to catching up with where we presently were in the game. Every active member had a role in solving the ARG. Even down to those who just reminded us to focus when we were going off the rails. The names are too many to list.

**Q.) Anything else you would like to add?**

> I’d like to add that we as a community are ready for the next big ARG. The marvelous team at 5th column, and the work done behind the scenes by people we will never know about (but would have liked to), together led to a well deserved EMMY for best ARG in 2020. Frankly no other ARG came close to what the Mr Robot ARG has been year after year. I was glad to see the win come for them.
> 
> We’re ready for the future. But we’re gonna wait for the next show that deserves us.

* * *

From everyone on the Kali team, well done ARGSociety! It looks like you guys haven’t yet stop, and are hunting to the other Easter eggs still left to be found! If you want to know more, get involved, join their [subreddit](https://www.reddit.com/r/ARGsociety/) and [discord](https://discord.com/invite/2ERCJa2).

We will leave you now with a video by [Beamofoldlight](https://twitter.com/dafreqs) from ARGSociety in his down time put together this of them completing the [final puzzle](https://www.reddit.com/r/ARGsociety/wiki/index), which really shows just [how much effort](https://i.redd.it/enyq8z3ma6i51.jpg) went into [solving](https://www.reddit.com/r/ARGsociety/wiki/welcome) it [all](https://cdn.discordapp.com/attachments/581200568983355394/715015582197743636/arg-timeline-s4.pdf). Enjoy.

 Your browser does not support the video tag.

#### [Source](https://www.kali.org/blog/mr-robot-arg-society/)

