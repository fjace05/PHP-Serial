PHP Serial
==========

This version of PHP Serial has been modernized in as much as errors are throw as catchable exceptions, the class
 has been namespaced and the native class destructor is utilized to clean up when the class goes out of scope.

It *should* be backwards compatible with the original version of Xowap/PHP-Serial.



Example
-------

```php
<?php
include 'PhpSerial.php';
use Hyperthese\PhpSerial;

// Let's start the class
$serial = new PhpSerial;

// First we must specify the device. This works on both linux and windows (if
// your linux serial device is /dev/ttyS0 for COM1, etc)
$serial->deviceSet("COM1");

// We can change the baud rate, parity, length, stop bits, flow control
$serial->confBaudRate(2400);
$serial->confParity("none");
$serial->confCharacterLength(8);
$serial->confStopBits(1);
$serial->confFlowControl("none");

try {
// Then we need to open it
$serial->deviceOpen();

// To write into
$serial->sendMessage("Hello !");
}
catch(Exception $e){
  die("Uhoh, something didn't work. " . $e->getMessage());
}
```



Licence
-------

PHP Serial
Copyright (C) 2007-2014 PHP Serial's contributors (see CONTRIBUTORS file)

This program is free software; you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation; either version 2 of the License, or
(at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License along
with this program; if not, write to the Free Software Foundation, Inc.,
51 Franklin Street, Fifth Floor, Boston, MA 02110-1301 USA.
