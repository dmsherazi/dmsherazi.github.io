---
ID: 3256
post_title: >
  convert a decimal value to its binary
  representation ( string )
author: Dost Muhammad Shah
post_excerpt: ""
layout: post
permalink: >
  http://dostmuhammad.com/blog/convert-a-decimal-value-to-its-binary-representation-string/
published: true
post_date: 2015-04-02 14:42:50
---
Wanted to share this snippet of code which I used to display a decimal numbers binary representation. It is quite self explanatory and easy to understand.

<pre>
/**
  * Turns a decimal value to its binary representation
  */
char* dec2binWzerofill(unsigned long Dec, unsigned int bitLength){
    return dec2binWcharfill(Dec, bitLength, '0');
}

char* dec2binWcharfill(unsigned long Dec, unsigned int bitLength, char fill){
  static char bin[64];
  unsigned int i=0;
unsigned int j;
  while (Dec > 0) {
    bin[32+i++] = ((Dec & 1) > 0) ? '1' : fill;
    Dec = Dec >> 1;
  }

  for ( j = 0; j< bitLength; j++) {
    if (j >= bitLength - i) {
      bin[j] = bin[ 31 + i - (j - (bitLength - i)) ];
    }else {
      bin[j] = fill;
    }
  }
  bin[bitLength] = ' ';

  return bin;
}
</pre>