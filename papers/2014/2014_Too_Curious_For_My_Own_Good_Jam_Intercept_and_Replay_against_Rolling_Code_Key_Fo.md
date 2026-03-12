---
title: "Too Curious For My Own Good: Jam Intercept and Replay against Rolling Code Key Fob (RTL-SDR)"
year: "2014"
authors: "Spencer Whyte (blog)"
topics: "RKE RollJam Rolling Code RTL-SDR 315 MHz ASK GNU Radio Blog"
url: "http://spencerwhyte.blogspot.com/2014/03/delay-attack-jam-intercept-and-replay.html"
source: web
---

# Too Curious For My Own Good: Jam Intercept and Replay against Rolling Code Key Fob (RTL-SDR)

- **Year:** 2014  
- **Authors:** Spencer Whyte (blog)  
- **URL:** http://spencerwhyte.blogspot.com/2014/03/delay-attack-jam-intercept-and-replay.html

---

Too Curious For My Own Good: Jam Intercept and Replay Attack against Rolling Code Key Fob Entry Systems using RTL-SDR

Too Curious For My Own Good

Saturday, 15 March 2014

Jam Intercept and Replay Attack against Rolling Code Key Fob Entry Systems using RTL-SDR

For the past 6 months I have been developing a proof of concept attack against rolling code key fob entry systems. Some examples of affected systems would be the key fob you use to unlock your car. Or the key fob you use to disarm your home security system. Or even open the garage door. The oscillators used in these key fobs are typically low cost, meaning that they may not operate at exactly their design frequency throughout the full temperature range. For this reason, the receiver in the car, or home security system is designed to accept signals within a certain pass band. The trick of the attack is for the adversary to jam at some frequency within the receivers passband, but not too close to the frequency of the remote. If you jam in this manor, when the victim presses the unlock button on their key fob, nothing will happen because the receiver is being jammed by an adversary. The adversary can then use a SDR such as the RTL-SDR, to record the whole transaction. The following GNU Radio flow graph could be used in conjunction with the RTL-SDR. GNURadio makes it easy to filter out the jamming signal and obtain the authorized remote signal. The signal obtained is the Nth rolling code, it is still valid because the receiver has not yet received the Nth rolling code. Therefore the adversary can replay the signal at a later time and unlock the car. But how does one replay the signal on the cheap? The system that was constructed looks as follows from a high level. The signal in this case was ASK (Amplitude Shift Keying) encoded data which was decoded using GNU Radio's "AM Demod" block as follows. The demodulated signal was then played back through the audio interface of the computer. The signal was then fed into a LM386 op amp to bring the signal from line level (~1V), up to TTL (~3V). The TTL signal was then fed into an ASK RF module operating at the same frequency as the authorized remote. The schematic for the constructed circuit follows. And the final product was soldered onto some prototyping board. The board here is powered by USB, and has a switch on the back right portion of the board. This switch allows you to put the board in either "Jamming" mode, or "Signal Replay" mode. In "Jamming" mode, the RF module will continuously transmit bogus data at the carrier frequency. In&nbsp;"Signal Replay" mode, it will transmit the data provided through the audio jack as an ASK encoded signal at the carrier frequency.&nbsp;A 315 MHz ASK module was used, but this module is inexpensive and could easily be swapped out for say a 400 MHz FSK module. A list of the parts used in it's constructed follows. Does this system actually work? Frighteningly, yes it does. I was able to test this attack against two economy cars and one van, all of which use rolling code security.&nbsp; The attack was successful against all three rolling code secured automobiles. I will finish this post by describing a scenario that is of far greater concern.

In a rolling code garage door system, imagine the following sequence of events. The victim presses the button on the RF remote to initiate the closing of the garage door. The adversary jams and intercepts the signal. The garage door therefore does not close. The victim presses the button on the RF remote again. The adversary jams and intercepts the signal again, but then replays the first signal he/she intercepted. The garage door closes, and the victim leaves the area assuming that their garage door is secure. The adversary then replays the second signal he/she intercepted and the garage door opens again.
