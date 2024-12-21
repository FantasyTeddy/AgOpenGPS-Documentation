UDP is the network protocol that is used to pass data between AgIO, AgOpenGPS and your physical board. It uses standard ethernet cables and it highly resilient to interruption (unlike USB which can get upset if the connection drops/reconnects).

Your tablet and your board will need to have the usual ethernet style connections you see around the house (in your router, back of your smart TV etc), similar to this:

![image](https://user-images.githubusercontent.com/9885921/225015451-0abf02f7-c87f-4516-a7ce-0d991b60f2b9.png)

You can think of UDP akin to passing a message to a friend via postcard; it's not secure in that anyone can read it, and you've no way of knowing if it was delivered. For AOG purposes, this is ideal; the data doesn't leave your machine, so security isn't much of a worry, and having any app on the system able to read it is a good thing.