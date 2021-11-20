# ISO_8583
ISO MIT &amp; additional information

# ISO - Message type indicator (MTI)
The first digit of the MTI indicates the ISO 8583 version in which the message is encoded.


**Code** | **Meaning** 
------------|----------- 
0xxx |	ISO 8583:1987
1xxx	|ISO 8583:1993
2xxx	|ISO 8583:2003
3xxx|	Reserved by ISO
4xxx| Reserved by ISO
5xxx| Reserved by ISO
6xxx| Reserved by ISO
7xxx| Reserved by ISO
8xxx	|National use
9xxx	|Private use

# ISO - Message class
Position two of the MTI specifies the overall purpose of the message.


**Code** | **Meaning** | **Usage** | **Note** 
------------|----------- |----------- |----------- 
x0xx|	Reserved by ISO	|
x1xx|	Authorization message	| Determine if funds are available, get an approval but do not post to account for reconciliation. Dual message system (DMS), awaits file exchange for posting to the account.
x2xx|	Financial messages	|Determine if funds are available, get an approval and post directly to the account. Single message system (SMS), no file exchange after this.
x3xx	|File actions message	|Used for hot-card, TMS and other exchanges|Hot Card means a Card which has been reported by the Cardholder as lost or stolen, or for which there is evidence of fraudulent use.
x4xx |	Reversal and chargeback messages	| Reversal (x4x0 or x4x1): Reverses the action of a previous authorization. Chargeback (x4x2 or x4x3): Charges back a previously cleared financial message. | Chargeback: Similar to refund but without prevention alerts for merchaint.
x5xx	|Reconciliation message|	Transmits settlement information message.
x6xx	| Administrative message	| Transmits administrative advice. Often used for failure messages (e.g., message reject or failure to apply).
x7xx	| Fee collection messages 
x8xx	| Network management message |	Used for secure key exchange, logon, echo test and other network functions.
x9xx | Reserved by ISO


# ISO - Message function
Position three of the MTI specifies the message function which defines how the message should flow within the system. Requests are end-to-end messages (e.g., from acquirer to issuer and back with time-outs and automatic reversals in place), while advices are point-to-point messages (e.g., from terminal to acquirer, from acquirer to network, from network to issuer, with transmission guaranteed over each link, but not necessarily immediately).



**Code** | **Meaning** |  **Note** 
------------|-----------  |----------- 
xx0x|	Request	 | Request from acquirer to issuer to carry out an action; issuer may accept or reject
xx1x	|Request response	 | Issuer response to a request
xx2x	|Advice | 	Advice that an action has taken place; receiver can only accept, not reject
xx3x	|Advice response | 	Response to an advice
xx4x	|Notification | 	Notification that an event has taken place; receiver can only accept, not reject
xx5x	|Notification acknowledgement | 	Response to a notification
xx6x	|Instruction |   ISO 8583:2003
xx7x	|Instruction acknowledgement |    ISO 8583:2003
xx8x | Reserved for ISO use |   Some implementations (such as MasterCard) use for positive acknowledgment.
xx9x | Reserved for ISO use |   Some implementations (such as MasterCard) use for negative acknowledgement.

# ISO - Message origin
Position four of the MTI defines the location of the message source within the payment chain.

**Code** | **Meaning** |  **Note** 
------------|-----------  |----------- 
xxx0  |Acquirer
xxx1	|Acquirer repeat
xxx2	|Issuer
xxx3	|Issuer repeat
xxx4	|Other
xxx5	|Other repeat
xxx6 | Reserved by ISO
xxx7  |Reserved by ISO
xxx8 | Reserved by ISO
xxx9  |Reserved by ISO

Given an MTI value of 0110, the following example lists what each position indicates:

0xxx → version of ISO 8583 (0 = 1987 version)  <br>
x1xx → class of the message (1 = authorization message) <br>
xx1x → function of the message (1 = response) <br>
xxx0 → who began the communication (0 = acquirer) <br>


###Reference
[Wikipedia - ISO 85835](https://en.wikipedia.org/wiki/ISO_8583#cite_note-4)
