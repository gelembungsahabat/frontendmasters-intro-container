## namespaces 

While chroot is a pretty straightforward, namespaces and cgroups are a bit more nebulous to understand but no less important. Both of these next two features are for security and resource management.

Let's say you're running a big server that's in your home and you're selling space to other people (that you don't know) to run their code on your server. What sort of concerns would you have? Let's say you have Alice and Bob who are running e-commerce services dealing with lots of money. They themselves are good citizens of the servers and minding their own business. But then you have Eve join the server who has other intentions: she wants to steal money, source code, and whatever else she can get her hands on from your other tenants on the server. If just gave all three them root access to server, what's to stop Eve from taking everything? Or what if she just wants to disrupt their businesses, even if she's not stealing anything?

Your first line of defense is that you could log them into chroot'd environments and limit them to only those. Great! Now they can't see each others' files. Problem solved? Well, no, not quite yet. Despite the fact that she can't see the files, she can still see all the processes going on on the computer. She can kill processes, unmount filesystem and potentially even hijack processes.

Enter namespaces. Namespaces allow you to hide processes from other processes. If we give each chroot'd environment different sets of namespaces, now Alice, Bob, and Eve can't see each others' processes (they even get different process PIDs, or process IDs, so they can't guess what the others have) and you can't steal or hijack what you can't see!

There's a lot more depth to namespaces beyond what I've outlined here. The above is describing just the UTS (or UNIX Timesharing) namespace. There are more namespaces as well and this will help these containers stay isloated from each other.