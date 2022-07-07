# secret-causal-unicast

Optimization to the buffer protocol:

* If a message in the output buffer has a *different destination* than preceding messages in the OB, then it can be "eagerly" sent (`send_eager`) and later followed up with a `send_release` message.  The receiver cannot *send* anything until receiving the `send_release` messagem but it can take internal actions and receive messages.
* The sender sends the `send_release` message for a given `send_eager` message after getting acks for *all* messages it sent prior to the `send_eager` message.

How could we state Proposition 1 in the buffer protocol paper to apply to this optimized buffer protocol?  (Which version of `send` should it be about?)
