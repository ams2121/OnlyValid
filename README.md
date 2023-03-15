# OnlyValid
Thunderbird Extension to ID and retain only email that is valid and matters

Notes and Comments:
This is notes, ideas and work to build a Thunderbird add on that follows the below logic.

Goal:

Change how spam is handeled

Logic:

**Statement 1) Friends - Show email from people to whom I send email**

* If I send email to an address (to/cc/bcc), it is likely someone I know and with whom I converse
* If I send email to an address, show me email recieved from this address (High Trust)
* The more email I sesnd to an address, the more I probably trust it
* If the email is from a first hop that the sender normally uses, trust them more (ie. my mail server is likley always the same or similar)


**Statement 2) Friends of Friends - Show email from people who also get email, from the people to whom I send email **

* If an address I trust (Statement 1) sends email to someone (To/CC), I probably trust that recipient and want to see email from them.
* Email addresses in email I recieve from people I trust, I have some level of trust with and will trust (medium?) the people they put on the To/CC line
* *MAYBE* The more I see the "friends of friends" the more I trust the email


**Statement 3) I want to read email threads in which I participate**

* If I have sent email and there is a message thread responding (or I respond in the middle of a thread), I want all the email in the thread.  headers of "References:" "In-Reply-To:"
* I especially care about messages replying to / referencing a "Message-Id: " of a message I sent
* I also trust (Medium) people in the To/CC line of these messages.


**Statement 4) I want to read email from people in my addressbook / contacts**

* In theory, the people in my addressbook I want to see email from
* **ISSUE** Thunderbird auto saves addresses at some condition to parts of my address book



----------------------------------------------

Interesting Code

* Good Addon 
  * An addon which pulls "sender" from all of your email.  This is a good code example to start pulling data
  * https://github.com/CicadaCinema/get-all-senders
  * https://github.com/CicadaCinema/get-all-senders/blob/master/mainPopup/popup.js
* Good References
  * Pulling from a pages (of emails)/index - https://developer.thunderbird.net/add-ons/hello-world-add-on/using-a-background-page
  * Message Lists - https://webextension-api.thunderbird.net/en/91/how-to/messageLists.html
  * Message Header object - https://webextension-api.thunderbird.net/en/91/messages.html#messageheader
  * Message Display command to get contents - https://webextension-api.thunderbird.net/en/91/messageDisplay.html

----------------------------------------------

Order of Work

* Retrieve all senders / To / CC / BCC / message ID / Reply To / references
* ID all message-IDs I've sent (email threads)
* ID all people I've sent email to (friends)
* Find all recipients in emails people ive sent email to have sent (friends of friends)

0---------1---------2---------3---------4---------5---------6---------7---------8
