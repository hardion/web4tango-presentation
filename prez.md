class: center, middle

![maxiv](image/maxiv.png)
# Tango Specification and Experimentation

Tango Meeting 2019, DESY
 
By [Vincent Hardion](https://twitter.com/hardion), Antoine Dupré and Emil Rosenberg on the behalf of the [KITS team](https://github.com/orgs/MaxIV-KitsControls)


[Our MAX IV gitlab repository](https://gitlab.com/MaxIV)
---
# Specification

<iframe src="https://giphy.com/embed/E7otZZ9kes92w" width="480" height="270" frameBorder="0" class="giphy-embed" allowFullScreen></iframe><p><a href="https://giphy.com/gifs/difference-bulb-signals-E7otZZ9kes92w">TURN SIGNAL</a></p>
First codified in the 1949 Geneva Convention on Road Traffic  
---
# Specification
<video width="480" height="360" loop autoplay controls>
  <source src="https://i.kinja-img.com/gawker-media/image/upload/s--MhezjkxA--/c_scale,fl_progressive,q_80,w_800/18x3wjuyjiri5gif.mp4" type="video/mp4">
  Your browser does not support the video tag.
</video>


Does the implementation matter?
---

# Agenda 

#- CORBA
#- The ZeroMQ specification
#- Tango RFC
#- The mascot project

---
# Disclaimer

#  Is it a "Have to replace CORBA" talk?

---
# Disclaimer

#  Is it a "Have to replace CORBA" talk? YES

---
# Context

##  Tango v10 and CORBA, already in 2013 (ICALEPCS Talk)
##  Experimentation of other RPC protocol
##  The Tango kernel meeting at Solaris, Poland.
![kernel-meeting](https://www.tango-controls.org/media/filer_public_thumbnails/filer_public/5e/32/5e325337-2d34-41e2-a77b-6697f5a485b5/kernel_doc_camp_dinner_2019_1024x576.jpg__512x238_q85_subsampling-2_upscale.jpg)
---
#- CORBA
.pull-left[
# Common Object Request Broker Architecture
 - Distributed Protocol
 - Object oriented
 - Language agnostic
 - Use an Interface Definition Language
 - Standard since 1991

Several generation of distributed follow up till Micro Services]
.pull-right[
![corba](https://www.corba.org/images/CORBA-logo-346x332.gif)
]
---
#- CORBA

# Suit perfectly Tango
 - Distributed Protocol
 - Device oriented
 - Language agnostic

# ... or Tango inspired by CORBA

Tango Device was just a specific CORBA Object.

You were supposed to use raw CORBA to access/expose a Tango device. The libtango was just an helper.

One reason why it's so hard to replace CORBA.

---
#- CORBA
# ... but the relationship started to be more complex
The usage of CORBA changed by the time with a mix of RPC
  - Dserver
  - read/write several attributes at the same time
  - ...

Another reason why it so hard to replace CORBA.

---
#- CORBA
# So what define Tango at the end?

At the Tango kernel meeting there was a lot of discussion of Tango v10:
 - new architecture to abstract the protocol and more
 - backward compatibility

Andy commented to define specification before development.
Lorenzo gave this great idea to look at ZeroMQ.

---
#- The ZeroMQ specification
##  ABNF Augmented Backus-Naur form
Formal definition for protocol
``` ABNF
device-name = domain "/" family "/" member
domain = 1*VCHAR
family = 1*VCHAR
member = 1*VCHAR
```

## [C4](https://rfc.unprotocols.org/spec:1/C4/) is the change process
- Collective Code Construction Contract
- Each specfication has an editor
- Modification can be done by merge request in draft mode.

---
#- The ZeroMQ specification
## [Consensus Oriented Specification System](https://rfc.unprotocols.org/spec:2/COSS/)

A way to define specification that is:
- simple
- open, shareable
- collaborative

It avoid to turn the specification proprietary by introducing key component (protected by patent).

If you don't like it, fork it.

It allows to track changes in specification

---
#- Tango RFC Proposition

## Proposition to use the same specification system as ZeroMQ

## A prototype of Tango specification [tango-rfc](https://gitlab.com/MaxIV/tango-rfc).

Guide of implementation is just to guarantee the interoperability
 - Need to Guarantee the behaviour of client and server
 - Propose different scenarii of compatibility.

## One specification, several implementation
What are the fundamentals to make a new implementation of Tango?

We can think that Tango can be implemented in the same language but with a different architecture but still stay compatible. (consistency over entry cost level)

---
# The Tango Specification

![](https://cooperativelyyours.org/uploads/2014/06/join-us-colour1.jpg)
Don't bother with boring beach, join us this summer

---
# The Tango Specification

## Goal
- Focus on V9 to understand the change for V10
- Need volunteer: Editors, Writers

## Timeline 3-6 months
- budget for help writing the specification
- budget after for writing a first new C++ implementation 

---
# The Mascot project
.pull-left[
## Investigation with GRPC.
- The enums and structure are part of the IDL. That may be one reason why CORBA is so into the C++ implementation 
- Should we implement the wire protocol ourselves?
- Is there a tango protocol?
- Should we enforce the same name of class/enum in different implementation? Dev...

On the client side:
- Is the TangoDatabase and admin device are only a client abstraction?
]

.pull-right[
![GRPC](https://www.cncf.io/wp-content/uploads/2017/08/logo_grpc_padding-300x277.png)
]
---
# The Mascot project

![mascot](https://proxy.duckduckgo.com/iu/?u=http%3A%2F%2Ftopbet.eu%2Fnews%2Fwp-content%2Fuploads%2F2013%2F12%2Fracing-sausages.jpg&f=1)
#Demo

---
# Questions


