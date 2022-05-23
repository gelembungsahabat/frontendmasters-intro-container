## Tags

So far we've just been running containers with random tags that I chose. If you run `docker run -it node` the tag implicitly is using the `latest` tag. When you say `docker run -it node`, it's the same as saying `docker run -it node:latest`. The `:latest` is the tag. This allows you to run different versions of the same container, just like you can install React version 15 or React version 16: some times you don't want the latest. Let's say you have a legacy application at your job and it depends on running on Node.js 8 (update your app, Node.js is already past end-of-life) then you can say :

`docker run -it node:8 bash`

Once in the shell, run `node --version` and you'll see the Node.js version is 8..! Neat! This is helpful because now we can fix our Node.js version to the one our app expects. Hop back over to the [Docker Hub page](https://hub.docker.com/_/node/) for the node container. Take a look at all the version of the node container you can download. 