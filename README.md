# InfoLeak
Official write-up for a challenge in NasCon CTF '23

## Challenge
<b>Name</b><br/>
InfoLeak<br/><br/>
<b>Description</b><br/>
This guy freelanced for our company and disclosed one of our top-secret RSA encoding schemes somewhere in the wild. The only thing we know about him is his Instagram ID: @dingavinga. We need the exact link to where he posted the confidential scheme. (Format: https://{URL})
<br/><br/>
<b>Hint</b><br/>
Repositories aren't the only place you can store code.<br/>
	&#45; Github Admin

## Solve 
Since this is an OSINT challenge, we can take just about any route to this challenge. However, we will be covering 2 of those.
#### Identifying the Problem
We know with the problem statement that we need to find a piece of code since a whole "encoding scheme" was leaked. We also know the Instagram ID: [dingavinga](https://instagram.com/dingavinga)
#### Recon
The first step we take is visting the target's Instagram profile.<br/>
![image](https://user-images.githubusercontent.com/88616338/226379550-c0dfe014-42bb-4ca6-b0b5-474adb226c79.png)
<br/>To our surprise, the profile is private and there is probably no way of accessing his posts. However, we stumble upon the name of the target- Abdullah.

#### Route 1 (The know-it-all route)
Knowing that a piece of code was leaked, our best bet is [GitHub](https://github.com). We search for [dingavinga](https://github.com/dingavinga)...<br/>
![image](https://user-images.githubusercontent.com/88616338/226380446-bd3de36d-bfb0-47d2-bb69-5f2b5f44e646.png)<br/>
We notice the name and this is definitely not "Abdullah"'s profile. Maybe the username @dingavinga was taken at the time the target created his profile? We try and search for GitHub profiles keeping the keyword "dingavinga" in mind.
<br/>![image](https://user-images.githubusercontent.com/88616338/226381291-c5592883-21f0-4b05-84bc-f35ac93a348e.png)
<br/>
Woah! There's another profile with the username [dingavinga1](https://github.com/dingavinga1). We go ahead and open up this profile and... (skip route 2 to avoid suspense)

#### Route 2 (Noob)
We go ahead and search for "dingavinga abdullah" on Google and get the following results.<br/>
![image](https://user-images.githubusercontent.com/88616338/226383089-55ea56d2-9753-407d-9637-2af710d2307b.png)
<br/>
Out of LinkedIn, SoundCloud and GitHub, which platform is perfect for leaking code? You guessed it- Github. We go ahead and click it and...

#### Finding the flag
![image](https://user-images.githubusercontent.com/88616338/226381805-cd646cfe-a098-4e0e-be2a-670af994216e.png)
<br/>
We've found our guy! Now all we have to do is search for rsa in his repositories. Unfortunately, we get "no results returned" :(<br/>
![image](https://user-images.githubusercontent.com/88616338/226382292-a73db1e9-efbb-48fc-89d3-0038ca212b27.png)
<br/>
Just as we're about to lose all hope, a hint is uploaded (given above). The statement tries to derail us from our GitHub path. However, the last line says "Github Admin" which hints at the code being hidden on Github but not in a repository. As cyber-security professionals, we go to our best-friend [ChatGPT](https://chat.openai.com) and ask the question, "Where can you put code on Github while not using a repository?"<br/>
![image](https://user-images.githubusercontent.com/88616338/226386508-1595b345-3419-4d77-8226-f7e7c9a1e202.png)
<br/>
GitHub Gist? What the f**k is that? Anyway, we go ahead and look for [Gists by dingavinga1](https://gist.github.com/dingavinga1) and we see a familiar word. <br/>
![image](https://user-images.githubusercontent.com/88616338/226387142-1d9d6097-4fc8-477b-834e-494ce1d942ac.png)
<br/>Yes!!! We're looking for an RSA scheme. This is an RSA scheme. The flag is the URL of the leaked code, so we copy the link https://gist.github.com/dingavinga1/a8b1b48dcd63bfb85f31c2e04037429e and to our surprise, it works!

## Conclusion 
All hints are not rabbit holes.
