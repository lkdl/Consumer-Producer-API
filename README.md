Consumer/Producer API: data transport library for NDN
=================================================================================
Consumer abstraction model supports the following application patterns:







This library implements Simple Data Retrieval (SDR), Unreliable Data Retrieval (UDR) and Reliable Data Retrieval (RDR)
[Consumer / Producer Communication with Application Level Framing in Named Data Networking](http://conferences2.sigcomm.org/acm-icn/2015/proceedings/p99-moiseenko.pdf), and Infomax (IDR) protocol [InfoMax: An Information Maximizing Transport Layer Protocol for Named Data Networks](http://ieeexplore.ieee.org/xpl/login.jsp?tp=&arnumber=7288420).

Consumer/Producer API uses [ndn-cxx](https://github.com/named-data/ndn-cxx) library as NDN development library.

Consumer/Producer API is an open source project licensed under GPL 3.0 (see `COPYING.md` for more detail). We highly welcome all contributions to the Consumer/Producer code base, provided that they can licensed under GPL 3.0+ or other compatible license.

Feedback
--------

Please submit any bugs or issues to the **Consumer/Producer API** issue tracker:

* http://redmine.named-data.net/projects/consumer-producer-api

Installation instructions
-------------------------

### Prerequisites

Required:

* [ndn-cxx and its dependencies (e.g Boost, etc.)](http://named-data.net/doc/ndn-cxx/)

### Build

To build Consumer/Producer API from the source:

    ./waf configure
    ./waf
    sudo ./waf install

To build on memory constrained platform, please use `./waf -j1` instead of `./waf`. The
command will disable parallel compilation.

If configured with examples: `./waf configure --with-examples`), the above commands will also
generate test applications in `./build/examples`

Test applications must be run in the following pairs:
--------

* Example of single-threaded non-blocking parallel consumption: async-producer & async-consumer

* Example of changing the forwarding strategy for a specific namespace: broadcast-producer & broadcast-consumer

* Example of Infomax Data Retrieval: idr-producer & dir-consumer 

* Example of embedding manifests (with no signature given): manifest-producer & manifest-consumer

* Example of embedding manifest with a real signature: manifest-signing-performance & manifest-verification-performance

* Example of chaining consume calls (consume() within another consume()): rdr-chaining-producer & rdr-chaining-consumer
  
* Example of RDR built-in exclusion of content with invalid signature: rdr-exclude-producer & rdr-exclude-consumer

* Example of RDR built-in processing of application Nacks: rdr-nack-delay-producer & rdr-nack-delay-consumer

* Example of signing and verifying content: rdr-signing-performance & rdr-verification-performance

* Example of using Simple Data Retrieval: sdr-producer & sdr-consumer

* Example of manual exclusion using Simple Data Retrieval: sdr-exclude-producer & sdr-exclude-consumer 

* Example of sequential (in the loop) content production and consumption: sequential-producer & sequential-consumer

* Example of using Unreliable Data Retrieval: udr-producer & udr-consumer 

* Example demonstrating fast retransmission in UDR: udr-fastretx-producer & udr-fastretx-consumer


