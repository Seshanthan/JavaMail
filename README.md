# JavaMail

Working Of Application:

This Application uses JavaMail modules such as javax packages which gives us 
access to import all the necessary imports such as Message, Session, Transport, Inet 
Address, Mime packages and etc. Using Netbeans IDE create a graphical user interface 
one for sender and another for receiver.
For Sender there are 4 textfields to get input of from mail id, from password, to 
mail id, subject and a textarea for message. When attachment button is clicked, file to be 
attached can be choosed from the local machine. When send button is clicked data is 
taken from the fields. Using Properties function protocol, port, authentication and TLS 
are set as Host:smtp.gmail.com, Port:587, Authentication :True, Starttls.enable:True.
Then by using Session we get default instance of property and authenticator .Using 
Password Authenticator from javax package we check whether given mail and password 
is valid or not. If valid then Mime Message object is created now we set from using inet 
address and we set subject then we create a multipart and bodypart object to get message 
and attachment. Now using data handler we add the data to parts and set content and send 
it via Transport class.
For Receiver two buttons are created one to receive using IMAP and other to 
receive using POP. If IMAP button is pressed we create properties object and session 
object to get default instance. Now we initialize store object using session , Server 
Host:imap.gmail.com. Using connect method connect host, mail id and password. Create 
a folder inbox using getfolder method then we open inbox. Then we create message array 
by getmessages then we fix a directory as “D:/Attachment”.Now we get subject, content 
and we extract the multipart object. From multipart we save the file in attachment folder 
and print the message in textarea. Finally all text is displayed in the text area. Now do the 
same for POP using server host:pop.gamil.com.


Analysis Through WireShark:

After clicking send in Sender we capture packets through applying SMTP filter 
and if we check I/O Graph there is a sudden spike which indicates that packets are sent 
through SMTP protocol. Now in Flow Graph we can see the Ack’s sent,received and 
retransmitted packets.After click IMAP/POP in receiver we capture packets through 
tcp.port==993(IMAP) and tcp.port==995(POP).Now we compare I/O Graph,Flow Graph 
and Rate of transmission of packets using Wireshark.
