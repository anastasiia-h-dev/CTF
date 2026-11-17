# Walkthrough

Description of the challenge:
> Here we have a letter that was recovered from the estate of Dr. H. Aldous Whitmore. It was never posted.

> Along with the letter, a strange message was discovered. We have no doubt that Dr. Whitmore meant to keep it secret, given
> his... Association with occult societies that was discovered after his death. Despite this, the relationship to the letter
> remains unclear, but a connection cannot be discounted.

> Find the key the letter hides, and read what Whitmore could not bring himself to send.

The ciphertext that was given:
> LQROZ{2.1845.W2E6YP4GVC4IBO7T.4I5ILMQT7QF35JSI57HJ5P2ACS}

The format of the flag is "POCTF{..}" it will be helpful during decryption (with it we simply will be able to check it the prefix was decrypted correctly).

After some closer inspection of the letter we see that the word "Beaufort" was mentioned. Of course, in the letter it means surname of some admiral, but in the context of cryptography it may correspond to Beaufort Cipher.

_Beaufort cipher_ is a polyalphabetic cipher similar to _Vigenere cipher_. Encryption procedure is performed using the formula:
```
Ci = (Ki - Pi + n) mod n
```
, where `Ki` is the symbol of the key at index `i` and `Pi` is the plaintext symbol at the same index, `n` is the alphabet size. In the English language there are 26 letters, so in our case `n = 26`.

Decryption is performed using formula:
```
Pi = (Ki - Ci + n) mod n)
```


Now, only what's left is to find the key. On the image, we see some words on the margins and some of them are marked with a star. So, probably, we have to construct key from those marked words. The first(and successful) idea that came to my mind is to use the first letters of the words, starting from the top and going clockwise. The key I got is  `AETHER`.
For decryption I used site [https://cryptii.com/pipes/beaufort-cipher/](https://cryptii.com/pipes/beaufort-cipher/).

The flag is

```
POCTF{2.1845.V2W6GE4BJP4SDF7O.4W5JPSDO7OM35RML57AV5C2ACB}
```

