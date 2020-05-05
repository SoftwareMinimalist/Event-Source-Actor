# Event Source Actor Template
Actor for LabVIEW Actor Framework implementing publisher subscriber model of communication with zero coupling

**Source LabVIEW Version:** 2020

**Author:** Piotr Kruczkowski

# Introduction 
I wanted to share with you a small example actor I wrote to help me with typical subscribing/registering actors.
With the introduction of interfaces in LV20 it is much easier to create uncoupled actor systems without using the legacy zero-coupling abstract messaging solution. 

The template shows how to design an example event source and how to create an example interface for messages being both received and sent from the source. The interfaces defined in the design are created for the purpose of defining messages and their core Send and Do VIs.

# Using the template
The template can be used to understand both publishing and non-publishing types of communication, because the interface design is similar.

General flow in designing a message-based API for an actor:
1. Understand what messages the actor needs to receive, and which methods will this trigger inside the actor. Define a public interface for the actor. 
2. Create messages based on the public interface of the actor, NOT the actor methods directly.
3. You should now have the actor, its abstract interface and the messages calling the methods of the interface.
4. For messages sent out from the actor you need to create a dummy receiver actor, for the purpose of designing the outgoing message interface.
5. Repeat the same process as in steps 1-3 but without creating the specific actor implementation of the interface.
6. In your actor, when conditions are met, send out the messages using the Receiver interface you defined.

