# The Hardware of Networks

cover:
excerpt:
tags: Network Programming, Beginner
prerequisites:

## Introduction

We study network programming but not enough about the actual hardware underneath—not complicated components, but the wires themselves. That is what this article will talk about.

## Sending Bits

BTW this is a network programming article and we're talking about wires in this section so we're talking about Ethernet, which is primarily used for local area networks (LAN). We'll talk about wifi after.

What is the purpose of wires? It's an easy answer to guess but a difficult question to think of. The purpose of wires, as you might have guessed, is to send bits from one node (component of a computer, or the computer itself) to another. But then things get a bit weird. Thinking of how to send a "1" is easy, you just send voltage through the thing. However how do you send a "0"? Just keep the wire off? 

Nope. Good guess tho that was my guess. So how it works is when you send a 1, you actually send a specific range of voltage. Your computer sends between 2V and 5V to send a 1 bit, and sends between 0V to 0.8V to send a 0 bit. 

The reason for these ranges is that electricity is just unreliable in general—and there's a lot of variance over long distances, voltages drop and fall and we have to account for that, hence the 0s and 1s—if we had 2s and 3s and 4s it would be very hard to set these boundaries and have them be very accurate at scale. 

(Oh yeah btw the range between 0.8V and 2V is like a dead man's zone or something where computers just label it undefined and ignore it or something)

Then lets say in a very unfortunate circumstance the computer can't generate something like 0.5V or something and just continuously "generates" 0V. Then what happens? How does the receiving end know if that's just the computer that's inactive or if it's actually sending 0 bits? 

So there's multiple solutions, and when you understand the answers this question actually becomes kinda dumb. But I'm ignorant, and you're ignorant, and these are the questions I asked so that's what I'm writing about. 

1) When the computer is inactive, it's not actually just sitting there at 0V. It's sending an idle state signal to stay connected but idle. The standard for 10 Mbps Ethernet (unc ahh ethernet. super old) the idle state signal was literally a heartbeat, sending a short voltage blip every 16 milliseconds. This was called a "Normal Link Pulse", and would send about 2.2V to 2.8V peak. The 16 milliseconds thing is irrelevant you don't have to know why it was just like 

2) The computer actually doesn't even understand anything / rejects everything that isn't actually recognized as a packet. If you don't know the internet works with "packets", not just a continuous stream of bits everywhere. It's the same as sending actual physical mail—you wouldn't just send a stream of letters to the post office, you would write it on one paper, put it into a labeled envelope, and THEN give it to the post office.

The computer STARTS actually even TRYING to interpret the message once 
