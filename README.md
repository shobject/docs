Shared Object Platform
----------------------

The `Shared Object Platform` (shobject) has an end goal of being a
protocol and libraries to help developers build distributed-first
applications, not by abstracting away the messy bits, but instead
creating re-usable building blocks to remove the monotony of networking
code and error handling, as well as having a solid core for the common
cases to build upon.

Sample Vision
=============

I meet up with a friend at a bar. After chatting, they would like to share
an always-updating album of baby pictures and the name of their
pediatrician with me.  We pull out our phones.

They generate a QR-code
providing a [magnet link](http://magnet-uri.sourceforge.net/) and
decryption key which provide read-only access to their private baby
pictures. I scan this QR Code and my phone begins grabbing the most
recent photos.

They then generate another QR Code that contains their phone's
[Hyperboria](https://hyperboria.net/) address, the URL, and a one-time
authentication code of the contact they wished to share.  I scan the
code and download the contact card, and file it with the cards I share
with my spouse.

We finish our drinks and head to our respective homes. Once there, my
phone connects to the local network and begins to sync the contact card
with my laptop, my spouse's laptop, and my spouse's phone.  My laptop
sees the album and begins to download the whole of it from the tracker.


Shoulders of Giants
===================

To do this, `shobject` itself will build upon tried-and-test platforms.
Part of the inital challenge will be choosing the smallest and most
minimal set of dependencies, while also handling all defined use-cases.

* Distributed, versioned object storage (i.e.
  [git](https://git-scm.com/),
  [mercurial](https://www.mercurial-scm.org/),
  [fossil](https://www.fossil-scm.org/))
* Networking (i.e. [0mq](http://zeromq.org/),
  [CJDNS](https://github.com/cjdelisle/cjdns))
* Distributed Hash Table (i.e. [BitTorrent](http://www.bittorrent.org/))
* Authentication and Encryption (i.e.
  [OpenSSL](https://www.openssl.org/), [NaCL](https://nacl.cr.yp.to/))
* Common types of objects predefiend (i.e.
  [Schema.org](http://schema.org/)) and serialization for said common
  types (i.e.
  [ProtcolBuffers](https://developers.google.com/protocol-buffers/),
  [Thrift](https://thrift.apache.org/), [BSON](http://bsonspec.org/),
  [JSON](http://www.json.org/), [XML](https://www.w3.org/XML/))

Some ideas
==========

Provide hooks for application writers to handle errors and other
situations without re-writing the world every time. For instance, if my
spouse and I both update someone's contact info, say I their birthday
and they their new address, the application, not `shobject` should
handle the merge.
