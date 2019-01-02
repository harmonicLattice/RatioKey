# RatioKey
The vintage Xcode project for RatioKey 1.1
The icon images are changed from what shipped as 1.1,
and there may be other changes, but the Xcode project
contained in this .zip file is essentially the same
as that which produced RatioKey 1.1.  That was a long
time ago, and many changes would be required to get
it running on a current version of Xcode and to compile
for a current version of iOS.  Notably, I used C structs
allocated on the heap and accessed by reference and
registered a callback directly with a Core Audio output
unit.  My understanding is that both of these are now
off-limits.  Moreover, many new APIs have come along in
the meantime, including AVAudioEngine and AUAudioUnits.
If you do attempt to get RatioKey running again, I'd
suggest not calling any Swift or Objective-C code from
within the callback block/function; keep it pure C, or
C++ if you're familiar with that language.  What I plan
on doing, if and when I get around to writing a new app
to replace RatioKey, is to not make *ANY* calls to ObjC
or Swift code from any C code, but only in the other
direction, passing in configuration and events through
C functions and doing all rendering in C.  I hope to
register a callback with the AUAudioUnit wrapped within
an AVAudioPlayerNode, but have not yet confirmed that
this is possible. - 02Jan2019
