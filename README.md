# Lernaean
**The task is to guess a password**
I identified that we are supplied purely with HTML that has no action, and simply comes straight back to the same page with 1 value - password

if you guess wrong it simply states ‘invalid password!’

I didn’t find any more clues so the only thing I could think to do was brute force it.  This seems to be correct since it says “please do not try to guess my password!”

I wrote two python scripts to try this.

First I tried to make a CURL POST request, and then I tried again using python requests

Pseudo code:
`import libs
suppress errors:
	for word in wordlist:
		make POST request to page, supplying the word as password attempt
		if there is a response and ‘invalid’ is not in it:
			print word`

Not managed to get this to work yet, however it does seem to be barking up the right tree.  Others suggest using Hydra (which ‘lernaean’ is a reference to) but that’s cheating!

---

My script seems to run for a reasonable amount of time without an answer, but I’m sure I’m on the right trail.

I am using Hydra to see if I can crack it that way and then check if the password is actually in my wordlist

`ydra
-l or -L <usernamelist>
-P <passwordlist>
url.url.com:port
http-post-form
“path/url.php:postVar=^USER^&postVar2=^PASS^:Errortext”`
seems like i was on the right track the whole time but i was ignoring the exceptions caused by EXCEEDING MAX RETRIES and this was causing my problem

hydra somehow gets around this??

I changed my code to use ‘with suppress(Exception)’ which then simply sleeps the loop for 1 second every time the exception occurs.  I’m not sure if this gets around the max retries error, but it’s running for a very long time...

#hackthebox #hacking #pentesting #exploitation #cracking
