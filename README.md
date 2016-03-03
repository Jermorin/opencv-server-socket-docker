<big><h1 align="center">opencv-server-socket-docker</h1></big>

<a href="https://travis-ci.org/Jermorin/opencv-server-socket-docker">
  <img src="https://img.shields.io/travis/Jermorin/opencv-server-socket-docker.svg?style=flat-square"
       alt="Build Status">
</a>


- Opencv [socket server](https://github.com/Jermorin/opencv-server-socket) in docker who emit faces position
- See also : [client example](https://github.com/Jermorin/opencv-react-electron)
- [dockerHub](https://hub.docker.com/r/jermorin/opencv-server-socket/)
- Docker from [jermorin/node-opencv](https://github.com/Jermorin/docker-node-opencv)

## Install

```sh
docker pull jermorin/opencv-server-socket
```

## Usage

```sh
docker run jermorin/opencv-server-socket
```

###client

```js
import socket from 'socket.io-client';

const serverUrl = 'http://localhost:3000';

const socketOptions = {
  transports: ['websocket'],
  'force new connection': true
};

const imageUrl = {url: 'https://pixabay.com/static/uploads/photo/2016/01/09/08/38/india-1129953_960_720.jpg'};
const base64 = {base64: 'kekekdi888'};
const path = {path: '../server/path'};

const client = socket.connect(serverUrl, socketOptions);

client.on('connect', () => {
  console.log('connection to server');
  client.emit('image', imageUrl);
  client.on('faces', faces => console.log(faces));
});
```
## License

MIT © [Jérémy Morin](http://jermor.in)
