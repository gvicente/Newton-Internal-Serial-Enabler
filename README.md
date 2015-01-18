License & Disclaimer
--------------------

This program is licensed under the GPL v2.  A copy is included with this
distribution in the LICENCE.md file.

BECAUSE THE PROGRAM IS LICENSED FREE OF CHARGE, THERE IS NO WARRANTY FOR
THE PROGRAM, TO THE EXTENT PERMITTED BY APPLICABLE LAW. EXCEPT WHEN OTHERWISE
STATED IN WRITING THE COPYRIGHT HOLDERS AND/OR OTHER PARTIES PROVIDE THE PROGRAM
"AS IS" WITHOUT WARRANTY OF ANY KIND, EITHER EXPRESSED OR IMPLIED, INCLUDING,
BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A
PARTICULAR PURPOSE. THE ENTIRE RISK AS TO THE QUALITY AND PERFORMANCE OF THE
PROGRAM IS WITH YOU. SHOULD THE PROGRAM PROVE DEFECTIVE, YOU ASSUME THE COST OF
ALL NECESSARY SERVICING, REPAIR OR CORRECTION.

IN NO EVENT UNLESS REQUIRED BY APPLICABLE LAW OR AGREED TO IN WRITING
WILL ANY COPYRIGHT HOLDER, OR ANY OTHER PARTY WHO MAY MODIFY AND/OR REDISTRIBUTE
THE PROGRAM AS PERMITTED ABOVE, BE LIABLE TO YOU FOR DAMAGES, INCLUDING ANY
GENERAL, SPECIAL, INCIDENTAL OR CONSEQUENTIAL DAMAGES ARISING OUT OF THE USE OR
INABILITY TO USE THE PROGRAM (INCLUDING BUT NOT LIMITED TO LOSS OF DATA OR DATA
BEING RENDERED INACCURATE OR LOSSES SUSTAINED BY YOU OR THIRD PARTIES OR A
FAILURE OF THE PROGRAM TO OPERATE WITH ANY OTHER PROGRAMS), EVEN IF SUCH HOLDER
OR OTHER PARTY HAS BEEN ADVISED OF THE POSSIBILITY OF SUCH DAMAGES.

This program toggles low level hardware signals using undocumented ROM functions.
It is intended for developer use.  You should know what you're doing, as this
could do damage to your hardware.

Limitations
-----------

I have tried to include support for the German variant of the MessagePad 2x00,
however, I do not have one to test against.  It is possible that I could have
made typos or errors in the code that would prevent it from working properly on
a German version.  Proceed at your own risk.

Purpose
-------

The Newton MessagePad 2x00 has an internal slot that was intended for an 
internal modem accessory that was never made.  The connector exposes several
capabilities, including three serial channels, power, audio, and a GPIO pin.

http://www.unna.org/unna/apple/documentation/n2platform/n2-issdg.pdf

For more information on the internal serial slot, you can see some content
I posted to blogspot at the following address.

Credits
-------

Eckhart Köppen, author of Blunt (the bluetooth stack for the Newton), as 
posted some sorce code for toggling the SerialPortSelect signal for Serial 
Channel 3. 

This code serves as an excellent primer for calling arbirary functions in ROM.

At its heart, this app would not be possible were it not for Eckhart's template
to follow.

Eckhart calls the WriteDIOPins function to directly toggle the pin at 0x22 for
SerialPortSel3.  Instead, I have called SerialPort3LineDriverConfig to perform
this same function.  In the end, its about the same.

There is also a SerialPort0LineDriverConfig function for toggling the 
SerPortSel0 signal.  This application also directly calls the GPIO functions
for accessing pin 26 (the General Purpose I/O pin)


