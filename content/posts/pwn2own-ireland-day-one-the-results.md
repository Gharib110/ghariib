---
title: "Pwn2Own Ireland Day One - The Results"
date: 2025-01-04
categories: 
  - "cybersecurity"
  - "security"
  - "vulnerabilities"
tags: 
  - "cybersecurity"
  - "security"
  - "zero_day"
  - "zeroday"
---

Welcome to the first day of Pwn2Own Ireland 2024! We have four tremendous days of research planned, including multiple SOHO attempts. We’ll be updating this blog in real time as results become available. We have a full schedule of attempts today, so stay tuned! All times are Irish Standard Time (GMT +1:00).

* * *

_That's a wrap on Day 1 of #Pwn2Own Ireland! We awarded $516,250\* for 52 unique 0-days. Viettel Cyber Security (@vcslab) has an early lead for Master of Pwn with 13 points, but there's a lot of contest left to go. Stay tuned for all of the latest results as Pwn2Own Ireland continues._

_\*The total increased from $486,250 to $516,250 after a recount._

![](https://images.squarespace-cdn.com/content/v1/5894c269e4fcb5e65a1ed623/f3fe3c06-0766-490c-a9ba-87043aa6ec07/P2O-Ireland+2024+Master+of+Pwn+Leaderboard-Day+1.jpg?format=1000w)

**SUCCESS** - phudq and namnp from Viettel Cyber Security (@vcslab) used a stack-based buffer overflow and an untrusted pointer deref to exploit the Lorex 2K WiFi camera. They earn $30,000 and 3 Master of Pwn points.

![](https://images.squarespace-cdn.com/content/v1/5894c269e4fcb5e65a1ed623/fa8b63d1-ba76-4d6a-b706-d57c98e849d6/Image+%2816%29.jpeg?format=1000w)

![](https://images.squarespace-cdn.com/content/v1/5894c269e4fcb5e65a1ed623/11da45b4-22ac-4094-b2e4-3999f6ff4993/Image+%2817%29.jpeg?format=1000w)

**FAILURE** - Unfortunately, Can Acar (@canacar\_t) was unable to get his exploit of the Synology TC500 camera working within the time allotted.

**SUCCESS** - Sina Kheirkhah (@SinSinology) of Summoning Team (@SummoningTeam) used a total of 9(!) different bugs to go from the QNAP QHora-322 through to the TrueNAS Mini X. His effort earns him $100,000 and 10 Master of Pwn points.

![](https://images.squarespace-cdn.com/content/v1/5894c269e4fcb5e65a1ed623/9d6f4392-252e-473a-ac57-c8766dcfd6e0/Sina-SOHO-Win.jpg?format=1000w)

**SUCCESS** - Jack Dates of RET2 Systems (@ret2systems) used a single Out-of-Bounds (OOB) write to exploit the Sonos Era 300 speaker. He earns himself $60,000 and 6 Master of Pwn points.

**SUCCESS** - Team Neodyme (@Neodyme ) used a stack-based buffer overflow to exploit the HP Color LaserJet Pro MFP 3301fdw printer. The earn $20,000 and 2 Master of Pwn points.

![](https://images.squarespace-cdn.com/content/v1/5894c269e4fcb5e65a1ed623/d51decde-7e17-4d04-9e63-447ae22a9023/Image+%2822%29.jpeg?format=1000w)

**FAILURE** - Unfortunately, Sina Kheirkhah (@SinSinology) of Summoning Team (@SummoningTeam) could not get his exploit of the QNAP TS-464 working within the time allotted.

**SUCCESS** - PHP Hooligans / Midnight Blue (@midnightbluelab) used a single bug to exploit the Canon imageCLASS MF656Cdw printer. They earn themselves $20,000 and 2 Master of Pwn points.

![](https://images.squarespace-cdn.com/content/v1/5894c269e4fcb5e65a1ed623/0b67e55f-0c41-4336-bbfa-4b403f7f3a20/PHPH-Canon-Win.jpg?format=1000w)

![](https://images.squarespace-cdn.com/content/v1/5894c269e4fcb5e65a1ed623/bee80020-0fd9-471f-a9a5-1728a40b8f6d/Image+%2821%29.jpeg?format=1000w)

**COLLISION** - The @Synacktiv team exploited the Lorex camera with two bugs, but one had previously been used in the contest. They still earn $11,250 and 2.25 Master of Pwn points.

![](https://images.squarespace-cdn.com/content/v1/5894c269e4fcb5e65a1ed623/ca32f88a-e1b4-41c8-8ee6-9018214d1d08/Image+%2820%29.jpeg?format=1000w)

![](https://images.squarespace-cdn.com/content/v1/5894c269e4fcb5e65a1ed623/c08d63b0-780b-459b-a98f-f665aaef4113/Image+%2818%29.jpeg?format=1000w)

**FAILURE** - Unfortunately, Sina Kheirkhah (@SinSinology) of Summoning Team (@SummoningTeam) could not get his exploit of the Synology BeeStation BST150-4T working within the time allotted.

**SUCCESS** - The Viettel Cyber Security (@vcslab) team combined 4 bugs - 2 in the router & 2 in the NAS - to going from the QNAP QHora-322 to the TrueNAS Mini X. Their combination of SQL injections and missing auth/exposed function bugs earn them $50K and 10 Master of Pwn points.

![](https://images.squarespace-cdn.com/content/v1/5894c269e4fcb5e65a1ed623/dd0d249f-9185-475a-8156-64af7b85c371/Viettel-Win-Cropped+1.png?format=1000w)

**SUCCESS** - ExLuck (@pivik\_) used four bugs, including an improper cert verification and a hardcoded cryptographic key, to exploit the QNAP TS-464 NAS device. They earn $40,000 and 4 Master of Pwn points.

![](https://images.squarespace-cdn.com/content/v1/5894c269e4fcb5e65a1ed623/184ca7f5-ddc2-4a7c-bae4-5299a3e76737/Multimedia.jpeg?format=1000w)

**FAILURE** - Unfortunately, Sina Kheirkhah (@SinSinology) of Summoning Team (@SummoningTeam) could not get his exploit of the Synology DiskStation DS1823xs+ working within the time allotted.

**FAILURE** - Unfortunately, PHP Hooligans / Midnight Blue (@midnightbluelab) could not get their exploit of the Lorex 2K Indoor Wi-Fi camera working within the time allotted.

**SUCCESS** - @dungnm, @dungdm, & @tunglth of Viettel Cyber Security (@vcslab) used a heap-based buffer overflow to exploit the Synology TC500. In doing so, they earn $30,000 and 3 Master of Pwn points.

![](https://images.squarespace-cdn.com/content/v1/5894c269e4fcb5e65a1ed623/a37cfdd1-1b82-4c0f-ac2d-4981ececf0f9/Image+%2823%29.jpeg?format=1000w)

**WITHDRAWN** - The PHP Hooligans / Midnight Blue (@midnightbluelab) have withdrawn their attempt targeting the Synology TC500 camera in the Surveillance category

**FAILURE** - Unfortunately, Sina Kheirkhah (@SinSinology) of Summoning Team (@SummoningTeam) could not get his exploit of the Lorex 2K Indoor Wi-Fi working within the time allotted.

**FAILURE** - Unfortunately, YingMuo (@YingMuo) of the DEVCORE Internship Program could not get his exploit of the Canon imageCLASS MF656Cdw working within the time allotted.

**SUCCESS** - The STEALIEN Inc. team \[Bongeun Koo(@kiddo\_pwn), Dohyun Kim(@d0now), Junyoung Choi(@insp3ct0r\_x), Wonbeen Im(@D0b6y), Juhyeop Lee(@leeju\_04), Juyeong Lee(@ju\_cheda), GuckHyeon Jin(@nang\_\_lam), Jongmin Kim(@slyfizz3)\] used a combination of bugs in their attack chain to exploit the Ubiquity AI Bullet and flash the lights (plus get a root shell). Their work earns them $30,000 and 3 Master of Pwn points.

**SUCCESS** - Most impressive! Ryan Emmons (@the\_emmons) and Stephen Fewer (@stephenfewer) of Rapid7 used an Improper Neutralization of Argument Delimiters bug to exploit the Synology DiskStation DS1823xs+ -- and it works or other Synology devices too! They earn $40,000 and 4 Master of Pwn points.

![](https://images.squarespace-cdn.com/content/v1/5894c269e4fcb5e65a1ed623/fafa5945-5e6b-43ee-a254-f48f649db1c6/Multimedia+%281%29.jpeg?format=1000w)

**Failure** - Unfortunately, the InfoSect (@infosectcbr) team could not get their exploit of the Synology TC500 camera working within the allotted time.

**SUCCESS** - The Synacktiv Team (@Synacktiv) used a combination of 3 different bug to exploit the Ubiquiti AI Bullet. All bugs were unique, so their second round win nets them $15,000 and 3 Master of Pwn points.

![](https://images.squarespace-cdn.com/content/v1/5894c269e4fcb5e65a1ed623/0f3b86be-3dfe-4fb1-b506-22d22ed28484/shared+image+%283%29.jpeg?format=1000w)

**SUCCESS** - Jack Dates of RET2 Systems (@ret2systems) used an OOB Write to get a shell and a modified login page on the Synology DiskStation DS1823xs+. His second round win nets him $20,000 and 4 Master of Pwn points.

![](https://images.squarespace-cdn.com/content/v1/5894c269e4fcb5e65a1ed623/08db6d18-31ce-4038-9ad2-d032333152e5/Multimedia+%282%29.jpeg?format=1000w)

![](https://images.squarespace-cdn.com/content/v1/5894c269e4fcb5e65a1ed623/5cc3fd1d-30a7-410c-9b96-38863fa2932f/Image+%2824%29.jpeg?format=1000w)

**SUCCESS** - Josh Foote (@BoredPentester) used a stack-based buffer overflow to exploit the Lorex 2K Wi-Fi camera. His second round win nets him $15,000 and 3 Master of Pwn points.

![](https://images.squarespace-cdn.com/content/v1/5894c269e4fcb5e65a1ed623/3ec372f4-fb4b-4254-850e-d77782597b71/Image+%2826%29.jpeg?format=1000w)

![](https://images.squarespace-cdn.com/content/v1/5894c269e4fcb5e65a1ed623/37563791-d366-4401-8f03-953026b141af/Image+%2827%29.jpeg?format=1000w)

Welcome to the first day of Pwn2Own Ireland 2024! We have four tremendous days of research planned, including multiple SOHO attempts. We’ll be updating this blog in real time as results become available. We have a full schedule of attempts today, so stay tuned! All times are Irish Standard Time (GMT +1:00).

* * *

_That's a wrap on Day 1 of #Pwn2Own Ireland! We awarded $516,250\* for 52 unique 0-days. Viettel Cyber Security (@vcslab) has an early lead for Master of Pwn with 13 points, but there's a lot of contest left to go. Stay tuned for all of the latest results as Pwn2Own Ireland continues._

_\*The total increased from $486,250 to $516,250 after a recount._

![](https://images.squarespace-cdn.com/content/v1/5894c269e4fcb5e65a1ed623/f3fe3c06-0766-490c-a9ba-87043aa6ec07/P2O-Ireland+2024+Master+of+Pwn+Leaderboard-Day+1.jpg?format=1000w)

**SUCCESS** - phudq and namnp from Viettel Cyber Security (@vcslab) used a stack-based buffer overflow and an untrusted pointer deref to exploit the Lorex 2K WiFi camera. They earn $30,000 and 3 Master of Pwn points.

![](https://images.squarespace-cdn.com/content/v1/5894c269e4fcb5e65a1ed623/fa8b63d1-ba76-4d6a-b706-d57c98e849d6/Image+%2816%29.jpeg?format=1000w)

![](https://images.squarespace-cdn.com/content/v1/5894c269e4fcb5e65a1ed623/11da45b4-22ac-4094-b2e4-3999f6ff4993/Image+%2817%29.jpeg?format=1000w)

**FAILURE** - Unfortunately, Can Acar (@canacar\_t) was unable to get his exploit of the Synology TC500 camera working within the time allotted.

**SUCCESS** - Sina Kheirkhah (@SinSinology) of Summoning Team (@SummoningTeam) used a total of 9(!) different bugs to go from the QNAP QHora-322 through to the TrueNAS Mini X. His effort earns him $100,000 and 10 Master of Pwn points.

![](https://images.squarespace-cdn.com/content/v1/5894c269e4fcb5e65a1ed623/9d6f4392-252e-473a-ac57-c8766dcfd6e0/Sina-SOHO-Win.jpg?format=1000w)

**SUCCESS** - Jack Dates of RET2 Systems (@ret2systems) used a single Out-of-Bounds (OOB) write to exploit the Sonos Era 300 speaker. He earns himself $60,000 and 6 Master of Pwn points.

**SUCCESS** - Team Neodyme (@Neodyme ) used a stack-based buffer overflow to exploit the HP Color LaserJet Pro MFP 3301fdw printer. The earn $20,000 and 2 Master of Pwn points.

![](https://images.squarespace-cdn.com/content/v1/5894c269e4fcb5e65a1ed623/d51decde-7e17-4d04-9e63-447ae22a9023/Image+%2822%29.jpeg?format=1000w)

**FAILURE** - Unfortunately, Sina Kheirkhah (@SinSinology) of Summoning Team (@SummoningTeam) could not get his exploit of the QNAP TS-464 working within the time allotted.

**SUCCESS** - PHP Hooligans / Midnight Blue (@midnightbluelab) used a single bug to exploit the Canon imageCLASS MF656Cdw printer. They earn themselves $20,000 and 2 Master of Pwn points.

![](https://images.squarespace-cdn.com/content/v1/5894c269e4fcb5e65a1ed623/0b67e55f-0c41-4336-bbfa-4b403f7f3a20/PHPH-Canon-Win.jpg?format=1000w)

![](https://images.squarespace-cdn.com/content/v1/5894c269e4fcb5e65a1ed623/bee80020-0fd9-471f-a9a5-1728a40b8f6d/Image+%2821%29.jpeg?format=1000w)

**COLLISION** - The @Synacktiv team exploited the Lorex camera with two bugs, but one had previously been used in the contest. They still earn $11,250 and 2.25 Master of Pwn points.

![](https://images.squarespace-cdn.com/content/v1/5894c269e4fcb5e65a1ed623/ca32f88a-e1b4-41c8-8ee6-9018214d1d08/Image+%2820%29.jpeg?format=1000w)

![](https://images.squarespace-cdn.com/content/v1/5894c269e4fcb5e65a1ed623/c08d63b0-780b-459b-a98f-f665aaef4113/Image+%2818%29.jpeg?format=1000w)

**FAILURE** - Unfortunately, Sina Kheirkhah (@SinSinology) of Summoning Team (@SummoningTeam) could not get his exploit of the Synology BeeStation BST150-4T working within the time allotted.

**SUCCESS** - The Viettel Cyber Security (@vcslab) team combined 4 bugs - 2 in the router & 2 in the NAS - to going from the QNAP QHora-322 to the TrueNAS Mini X. Their combination of SQL injections and missing auth/exposed function bugs earn them $50K and 10 Master of Pwn points.

![](https://images.squarespace-cdn.com/content/v1/5894c269e4fcb5e65a1ed623/dd0d249f-9185-475a-8156-64af7b85c371/Viettel-Win-Cropped+1.png?format=1000w)

**SUCCESS** - ExLuck (@pivik\_) used four bugs, including an improper cert verification and a hardcoded cryptographic key, to exploit the QNAP TS-464 NAS device. They earn $40,000 and 4 Master of Pwn points.

![](https://images.squarespace-cdn.com/content/v1/5894c269e4fcb5e65a1ed623/184ca7f5-ddc2-4a7c-bae4-5299a3e76737/Multimedia.jpeg?format=1000w)

**FAILURE** - Unfortunately, Sina Kheirkhah (@SinSinology) of Summoning Team (@SummoningTeam) could not get his exploit of the Synology DiskStation DS1823xs+ working within the time allotted.

**FAILURE** - Unfortunately, PHP Hooligans / Midnight Blue (@midnightbluelab) could not get their exploit of the Lorex 2K Indoor Wi-Fi camera working within the time allotted.

**SUCCESS** - @dungnm, @dungdm, & @tunglth of Viettel Cyber Security (@vcslab) used a heap-based buffer overflow to exploit the Synology TC500. In doing so, they earn $30,000 and 3 Master of Pwn points.

![](https://images.squarespace-cdn.com/content/v1/5894c269e4fcb5e65a1ed623/a37cfdd1-1b82-4c0f-ac2d-4981ececf0f9/Image+%2823%29.jpeg?format=1000w)

**WITHDRAWN** - The PHP Hooligans / Midnight Blue (@midnightbluelab) have withdrawn their attempt targeting the Synology TC500 camera in the Surveillance category

**FAILURE** - Unfortunately, Sina Kheirkhah (@SinSinology) of Summoning Team (@SummoningTeam) could not get his exploit of the Lorex 2K Indoor Wi-Fi working within the time allotted.

**FAILURE** - Unfortunately, YingMuo (@YingMuo) of the DEVCORE Internship Program could not get his exploit of the Canon imageCLASS MF656Cdw working within the time allotted.

**SUCCESS** - The STEALIEN Inc. team \[Bongeun Koo(@kiddo\_pwn), Dohyun Kim(@d0now), Junyoung Choi(@insp3ct0r\_x), Wonbeen Im(@D0b6y), Juhyeop Lee(@leeju\_04), Juyeong Lee(@ju\_cheda), GuckHyeon Jin(@nang\_\_lam), Jongmin Kim(@slyfizz3)\] used a combination of bugs in their attack chain to exploit the Ubiquity AI Bullet and flash the lights (plus get a root shell). Their work earns them $30,000 and 3 Master of Pwn points.

**SUCCESS** - Most impressive! Ryan Emmons (@the\_emmons) and Stephen Fewer (@stephenfewer) of Rapid7 used an Improper Neutralization of Argument Delimiters bug to exploit the Synology DiskStation DS1823xs+ -- and it works or other Synology devices too! They earn $40,000 and 4 Master of Pwn points.

![](https://images.squarespace-cdn.com/content/v1/5894c269e4fcb5e65a1ed623/fafa5945-5e6b-43ee-a254-f48f649db1c6/Multimedia+%281%29.jpeg?format=1000w)

**Failure** - Unfortunately, the InfoSect (@infosectcbr) team could not get their exploit of the Synology TC500 camera working within the allotted time.

**SUCCESS** - The Synacktiv Team (@Synacktiv) used a combination of 3 different bug to exploit the Ubiquiti AI Bullet. All bugs were unique, so their second round win nets them $15,000 and 3 Master of Pwn points.

![](https://images.squarespace-cdn.com/content/v1/5894c269e4fcb5e65a1ed623/0f3b86be-3dfe-4fb1-b506-22d22ed28484/shared+image+%283%29.jpeg?format=1000w)

**SUCCESS** - Jack Dates of RET2 Systems (@ret2systems) used an OOB Write to get a shell and a modified login page on the Synology DiskStation DS1823xs+. His second round win nets him $20,000 and 4 Master of Pwn points.

![](https://images.squarespace-cdn.com/content/v1/5894c269e4fcb5e65a1ed623/08db6d18-31ce-4038-9ad2-d032333152e5/Multimedia+%282%29.jpeg?format=1000w)

![](https://images.squarespace-cdn.com/content/v1/5894c269e4fcb5e65a1ed623/5cc3fd1d-30a7-410c-9b96-38863fa2932f/Image+%2824%29.jpeg?format=1000w)

**SUCCESS** - Josh Foote (@BoredPentester) used a stack-based buffer overflow to exploit the Lorex 2K Wi-Fi camera. His second round win nets him $15,000 and 3 Master of Pwn points.

![](https://images.squarespace-cdn.com/content/v1/5894c269e4fcb5e65a1ed623/3ec372f4-fb4b-4254-850e-d77782597b71/Image+%2826%29.jpeg?format=1000w)

![](https://images.squarespace-cdn.com/content/v1/5894c269e4fcb5e65a1ed623/37563791-d366-4401-8f03-953026b141af/Image+%2827%29.jpeg?format=1000w)

Go to Source
