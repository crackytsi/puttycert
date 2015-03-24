Documentation of puttycert:

This is a patched version of PuTTY. 
puttycert enables (as puttywincrypt) the user to use any private key related to a certificate in the user personal
 certificate store to perform public key ssh authentication. 
As long as there exists a certificate in the user personal certificate store that has a corresponding private key it 
should be possible to use the key to perform a public key ssh authentication. 

This enables the use of smart cards in PuTTY and Pageant, as long as the smart card is supported by Windows. 
PuTTY is found at: http://www.chiark.greenend.org.uk/~sgtatham/putty/ 

REQUIREMENTS
Windows XP or later. No other requirements. 


USAGE - PuTTY
To use a key backed by Windows please specify this key in the "Private key file for authentication:" text box
found in puttycert. This text box is found at Connection > SSH > Auth. 
To select ANY key backed by Windows type (in the text box): 
cert://* In order to select a specific key by certificate thumbprint type: 
cert://thumbprint=<thumbprint_in_hex> In order to select a specific key by part of certificate common name type: 
cert://cn=<part_of_common_name_to_search_for> Searching for all certificates may take a long time and "hang" 
puttycert if there exist many certificates on slow smart cards in the certificate store. 

USAGE - Pageant
Start Pageant by clicking on it. To add a key stored in Windows crypto API right click on Pageant in the 
systray and select "Add Certificate" in the menu. Whenever the private key is accessed the user may or may noti
 be prompted by Windows to enter a passphrase/PIN depending on whether the key is protected or not. 
Please note that it is not possible to add keys backed by Windows from the Pageant main GUI at i
the moment, only from the systray menu. 
To export the public key in the ssh authorized_keys format load the key into Pageant and double click on it.
 The public key will be copied into the clipboard in the authorized_keys format. 
BACKGROUND¶The puttycert patch was written in order to ease the use of public key ssh authentication with
 smart cards. The easiest way to go with this seemed to be using the windows crypto api for this. 
This enabled puttycert to function without bothering with any direct card drivers and pkcs#11 implementations. 



DIFFERENCES puttycert to wincrypt
* puttycert version of pageant stores the selected certificates in the registry and automatically loads them during 
  start process
* puttycert has a confirmation inclueded, whenever the smartcard signature operation happens (during authentication process)
* puttycert has some gui modification, for better user interaction
* puttycert has additional buttons for easier operations
* puttycert can be merged to the latest putty snapshot


Details of Wincrypt can be found here:
http://code.google.com/p/puttywincrypt/

Thanks to krzysiek... developer of wincrypt

Wincrypt is released with MIT License:
The MIT License (MIT). 

Copyright (c) <year> <copyright holders>

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.

