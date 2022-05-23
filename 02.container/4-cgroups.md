## cgroups

Okay, so now we've hidden the processes from Eve so Bob and Alice can engage in commerce in privacy and peace. So we're all good, right? They can no longer mess each other, right? Not quite. We're almost there.

So now say it's Black Friday, Boxing Day or Singles' Day (three of the biggest shopping days in the year, pick the one that makes the most sense to you 😄) and Bob and Alice are gearing up for their biggest sales day of the year. Everything is ready to go and at 9:00AM their site suddenly goes down without warning. What happened!? They log on to their chroot'd, unshare'd shell on your server and see that the CPU is pegged at 100% and there's no more memory available to allocate! Oh no! What happened?

The first explanation could be that Eve has her site running on another server and simple logged on and ran a program that ate up all the available resources so that Bob and Alice so that their sites would go down and Eve would be the only site that was up, increasing her sales.

However another, possibly more likely explanation is that both Bob's and Alice's sites got busy at the same time and that in-and-of-itself took all the resources without any malice involved, taking down their sites and everyone else on the server. Or perhaps Bob's site had a memory leak and that was enough to take all the resources available.

Suffice to say, we still have a problem. Every isolated environment has access to all physical resources of the server. There's no isolation of physical components from these environments.

Enter the hero of this story: cgroups, or control groups. Google saw this same problem when building their own infrastructure and wanted to protect runaway processes from taking down entire servers and made this idea of cgroups so you can say "this isolated environment only gets so much CPU, so much memory, etc. and once it's out of those it's out-of-luck, it won't get any more."

