# JavaMail

 1.INTRODUCTION
An email server is a computer that manages the sending and receiving of email messages. When you send an email, it is first sent to an email server, which then routes the message to the recipient's email server. The recipient's email server then delivers the message to their email inbox. Email servers use a set of standardized protocols to communicate with each other, including SMTP (Simple Mail Transfer Protocol) for sending messages and IMAP (Internet Message Access Protocol) or POP (Post Office Protocol) for receiving messages. Most email providers, such as Google, Microsoft, and Yahoo, maintain their own email servers to manage the delivery of email for their users. 


1.1.SMTP:
	SMTP (Simple Mail Transfer Protocol) is a protocol for sending email messages between servers. Most email systems that send mail over the Internet use SMTP to send messages from one server to another, and to deliver messages to local mail clients like Microsoft Outlook or Apple Mail. SMTP is a text-based protocol, and uses a series of commands and responses to transmit messages between servers. For example, when a client connects to an SMTP server to send an email message, the server responds with a "220" code to indicate that it is ready to receive the message. The client then sends a series of commands to specify the sender and recipient of the message, the message body, and any attachments, and the server responds with additional codes to indicate the success or failure of each command

  




1.2 IMAP:
IMAP (Internet Message Access Protocol) is a protocol for accessing email messages on a remote email server. Unlike the more widely used POP (Post Office Protocol), which downloads messages to a local email client, IMAP allows users to access their messages and other email data from any device or location, by keeping the data on the email server. This allows users to access their email messages, folders, and other information from multiple devices, and ensures that changes made on one device are reflected on all other devices. IMAP also provides additional features, such as the ability to search for messages on the server, and to access and manipulate the user's email folders.  
 
    			

1.3 POP:
	POP (Post Office Protocol) is a protocol for retrieving email messages from a remote mail server. When you use an email client, such as Microsoft Outlook or Apple Mail, to access your email, the client connects to the mail server using POP and downloads the messages to your computer. Once the messages are downloaded, they are usually removed from the server, unless you have configured the client to leave a copy of the messages on the server. POP is a simple protocol that does not provide many of the features available with other protocols, such as IMAP (Internet Message Access Protocol), which allow users to access their email from multiple devices and locations, and to access and manipulate their email folders. However, POP is still widely used because it is simple to implement and requires minimal resources. Most modern email clients support both POP and IMAP, so you can choose which protocol to use when setting up your email account.



	




1.5 GMAIL:
	Gmail is a free email service provided by Google, and is available at the gmail.com domain. However, users can also create custom email addresses using their own domain name with Gmail, such as info@example.com or sales@example.com. This is known as a Google Workspace account, formerly known as G Suite. With a Google Workspace account, users can create and manage multiple email addresses for their domain, as well as use other Google Workspace services, such as Google Drive and Google Calendar. These services are designed for businesses and organizations, and offer additional features and tools for collaboration and communication. If you're interested in using a custom domain with Gmail, you can sign up for a Google Workspace account and follow the instructions to set up your domain and email addresses.
1.6 JAVAMAIL:
	JavaMail is a Java API that provides classes for sending and receiving email messages. It can be used with Gmail and other email services that support the IMAP (Internet Message Access Protocol) and SMTP (Simple Mail Transfer Protocol) protocols. To use JavaMail with Gmail, you'll need to download the JavaMail API library and add it to your Java project. You'll also need to provide the following information to connect to the Gmail IMAP,POP and SMTP servers: 
IMAP server: imap.gmail.com 
IMAP port: 993
IMAP SSL: true
SMTP server: smtp.gmail.com 
SMTP port: 465 
SMTP SSL: true 
POP server: pop.gmail.com 
POP port: 995 
POP SSL: true 
You'll also need to provide your Gmail email address and password to authenticate with the server. With this information, you can use the JavaMail API to connect to the Gmail server and send and receive email messages using Java. You can find more detailed instructions and examples on the JavaMail website.




2. IMPLEMENTATION:
2.1 BUILDING THE GUI APPLICATIONS:
Install an IDE in your local machine.
Download necessary .jar files for imports.
Create two GUI’s,one for sender and another for Receiver.
Sender GUI should have from,password for the mail,to,subject,message and attachment to be sent.
Receiver GUI should have two buttons,one for IMAP and another for POP,and one textarea to display the retrieved message.
Write code for send button and attach button in the Sender GUI so that it get input from the 4 textfields and attachment file, and send it to the server through SMTP.
Write code for IMAP and POP button in the Receiver GUI so that it retrives message from inbox through respective protocols.
Run the applications simuntaneously, Send a mail through SMTP and receive it through POP and IMAP.













2.2 WORKING OF APPLICATION:
This Application uses JavaMail modules such as javax packages which gives us access to import all the necessary imports such as Message,Session,Transport,Inet Address,Mime packages and etc.Using Netbeans IDE create a graphical user interface one for sender and another for receiver.
For Sender there are 4 textfields to get input of from mail id,from password,to mail id,subject and a textarea for message.When attachment button is clicked,file to be attached can be choosed from the local machine.When send button is clicked data is taken from the fields.Using Properties function protocol,port,authentication and TLS are set as Host:smtp.gmail.com, Port:587, Authentication:True, Starttls.enable:True.Then by using Session we get default instance of property and authenticator.Using Password Authenticator from javax package we check whether given mail and password is valid or not.If valid then Mime Message object is created now we set from using inet address and we set subject then we create a multipart and bodypart object to get message and attachment.Now using data handler we add the data to parts and set content and send it via Transport class.
For Receiver two buttons are created one to receive using IMAP and other to receive using POP.If IMAP button is pressed we create properties object and session object to get default instance.Now we initialize store object using session , Server Host:imap.gmail.com.Using connect method connect host,mail id and password.Create a folder inbox using getfolder method then we open inbox.Then we create message array by getmessages then we fix a directory as “D:/Attachment”.Now we get subject,content and we extract the multipart object.From multipart we save the file in attachment folder and print the message in textarea.Finally all text is displayed in the text area.Now do the same for POP using server host:pop.gamil.com.
2.3 ANALYSIS THROUGH WIRESHARK:
	After clicking send in Sender we capture packets through applying SMTP filter and if we check I/O Graph there is a sudden spike which indicates that packets are sent through SMTP protocol. Now in Flow Graph we can see the Ack’s sent,received and retransmitted packets.
After click IMAP/POP in receiver we capture packets through tcp.port==993(IMAP) and tcp.port==995(POP).
5.CONCLUSION
From the above analysis we can clearly see that SMTP is clean as Transmission rate is linearly increasing and there is no packet loss. And also from the above analysis we can clearly see that POP is way faster than IMAP. But is speed only enough for to determine a protocol.If you use multiple devices to access your mail then IMAP is the best option as IMAP keeps your email account consistent across devices so need not to worry about being out of date or differing from device to device.Whereas if u only use single device to access your mails then POP is the best.If you want to conserve space then POP is the best option because POP deletes the data from server once it sends it to the device.Whereas IMAP stores all data in the server so we use lots of space.IMAP allows the user to sync emails but POP does not allow to sync emails.In POP all messages are downloaded at once whereas in IMAP message header can be viewed in prior to downloading.POP is unidirectional IMAP is bidirectional.I would recommend IMAP over POP because even though POP is fast IMAP is more efficient.In this modern era we use multiple devices to access everything including email therefore IMAP is efficient in many ways than POP.



