<h2>secure-passphrase/lib</h2>

Lightweight libraries for generating secure passphrases and converting passphrases to/from cryptographic keys.

Default dictionary used here is an 8K short common english word condensate of Alan Beale's public domain ("2 of 12") dictionary.  Any dictionary can be used - see link below for custome dictionary creation tool.

Key to phrase and phrase to key conversion follows RFC1751 conventions.

Currently implemented is a Javascript library.

<h4>lib/js Overview</h4>

1. Create random passphrase from words in a dictionary
 
  <code>pass = Passphrase.random( [keylen [, dictionary]] )</code>

  The key length indicates the # bytes in an equivalent numeric key.
   
  <code>Passphrase.randomNum</code> is the random number generator used. Is expected to return a number between 0 and 1.  Math.random is default. Can and should be set to a function that uses SecureRandom if available.

2. Create passphrase from numeric key and vise-versa
  
  <code>pass = Passphrase.fromKey( key [, dictionary] )</code>

  <code>key = Passphrase.toKey( pass [, keylen [, dictionary]] )</code>

For all functions:
 
  <code>keylen</code>: key length; if ommitted or null, 32 bytes (256 bits) is used 

  <code>key</code>: a numeric byte array

  <code>pass</code>: a string of words from the dictionary

  <code>dictionary</code>: array of words; if omitted, <code>Passphrase.defaultDictionary</code> is used
 
Example: a 32 byte key and 8K (8192) word dictionary will produce 20 word passphrase (13 bits per word).

Dictionary length should be a power of 2, otherwise some of the words will not be used.  For example, only the first 4K words will be used from a dictionary containing 6K words.

Test tool:
    http://secure-passphrase.github.com/tools/test.html

Custom dictionary creation tool:
    http://secure-passphrase.github.com/tools/dictionary.html

