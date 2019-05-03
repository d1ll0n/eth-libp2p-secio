# eth-libp2p-secio

> Fork of [libp2p-secio](https://github.com/libp2p/js-libp2p-secio/) using eth-peer-id, eth-peer-info and libp2p-crypto-secp256k1.


## Table of Contents

- [Install](#install)
- [Usage](#usage)
- [API](#api)
- [Contribute](#contribute)
- [License](#license)

## Install

```sh
npm install eth-libp2p-secio
```

## Usage

```js
const secio = require('eth-libp2p-secio')
```

## API

### `.tag`

The current `secio` tag, usable in `multistream`.

### `const encryptedConnection = secio.encrypt(localPeerId, plainTextConnection [, remotePeerId] [, callback])`

- `localPeerId: PeerId` - A PeerId object containing the Private, Public and Id of our node.
- `plainTextConnection: Connection` - The insecure connection to be secured.
- `remotePeerId: PeerId` - A PeerId object containing the Public and/or Id of the node we are doing the SECIO handshake with.
- `callback: Function` - Optional, Called if an error happens during the initialization.

Returns an encrypted [Connection object](https://github.com/libp2p/interface-connection) that is the upgraded `plainTextConnection` with now having every byte encripted.

Both plainTextConnection and encryptedConnection are at their base, PullStreams.

### This module uses `pull-streams`

We expose a streaming interface based on `pull-streams`, rather then on the Node.js core streams implementation (aka Node.js streams). `pull-streams` offers us a better mechanism for error handling and flow control guarantees. If you would like to know more about why we did this, see the discussion at this [issue](https://github.com/ipfs/js-ipfs/issues/362).

You can learn more about pull-streams at:

- [The history of Node.js streams, nodebp April 2014](https://www.youtube.com/watch?v=g5ewQEuXjsQ)
- [The history of streams, 2016](http://dominictarr.com/post/145135293917/history-of-streams)
- [pull-streams, the simple streaming primitive](http://dominictarr.com/post/149248845122/pull-streams-pull-streams-are-a-very-simple)
- [pull-streams documentation](https://pull-stream.github.io/)

#### Converting `pull-streams` to Node.js Streams

If you are a Node.js streams user, you can convert a pull-stream to a Node.js stream using the module [`pull-stream-to-stream`](https://github.com/pull-stream/pull-stream-to-stream), giving you an instance of a Node.js stream that is linked to the pull-stream. For example:

```js
const pullToStream = require('pull-stream-to-stream')

const nodeStreamInstance = pullToStream(pullStreamInstance)
// nodeStreamInstance is an instance of a Node.js Stream
```

To learn more about this utility, visit https://pull-stream.github.io/#pull-stream-to-stream.

## Contribute

Feel free to join in. All welcome. Open an [issue](https://github.com/libp2p/eth-libp2p-secio/issues)!

This repository falls under the IPFS [Code of Conduct](https://github.com/ipfs/community/blob/master/code-of-conduct.md).

[![](https://cdn.rawgit.com/jbenet/contribute-ipfs-gif/master/img/contribute.gif)](https://github.com/ipfs/community/blob/master/contributing.md)

## License

[MIT](LICENSE)
