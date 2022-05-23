## chroot

I've heard people call this "cha-root" and "change root". I'm going to stick to "change root" because I feel less ridiculous saying that. It's a Linux command that allows you to set the root directory of a new process. In our container use case, we just set the root directory to be where-ever the new container's new root directory should be. And now the new container group of processes can't see anything outside of it, eliminating our security problem because the new process has no visibility outside of its new root.
