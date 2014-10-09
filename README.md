faggot-io - Real-time log monitoring in your browser [![Build Status](https://travis-ci.org/faggot-io/faggot-io.svg?branch=master)](https://travis-ci.org/faggot-io/faggot-io)
=================================================

Powered by [node.js](http://nodejs.org) + [socket.io](http://socket.io)

## How does it work?

*Harvesters* watch log files for changes, send new log messages to the *server* via TCP, which broadcasts to *web clients* via socket.io.

Log streams are defined by mapping file paths to a stream name in harvester configuration.

Users browse streams and nodes in the web UI, and activate (stream, node) pairs to view and search log messages in screen widgets.

## Install Server & Harvester

### Docker
Check our [Docker faggot-io server image](https://registry.hub.docker.com/u/muchweb/faggot-io-arch/).

### NPM

> Please note that you will require `coffee-script` installed
> ```
> npm install -g coffee-script
> ```

---

> Please also note that on GNU operation system, you will require `node-gyp` dependencies:
>
> - `python2`
> - `make`
> - `gcc`
>
> These can be installed via your package manager

---

1. Install via NPM

    ```bash
    npm install -g faggot-io --user "ubuntu"
    ```

2. Run server

    ```bash
    faggot-io-server
    ```

3. Configure harvester

    ```bash
    nano ~/.faggot-io/harvester.conf
    ```

4. Run harvester

    ```bash
    faggot-io-harvester
    ```

5. Browse to [http://localhost:28778](http://localhost:28778) to see live logs

## Server TCP Interface

Harvesters connect to the server via TCP, and write properly formatted strings to the socket.  Third party harvesters can send messages to the server using the following commands:

Send a log message

    +log|my_stream|my_node|info|this is log message\r\n

Register a new node

    +node|my_node\r\n

Register a new node, with stream associations

    +node|my_node|my_stream1,my_stream2\r\n

Remove a node

    -node|my_node\r\n


## Building

Global NPM dependencies: `coffee-script`, `mocha`, `less` and `browserify`

    npm install
    cake build

### Building documentation

Global NPM dependency: `yuidocjs`

    cake docs

Then navigate to `docs/index.html`

Theme was based on [yuidoc-bootstrap-theme](https://www.npmjs.org/package/yuidoc-bootstrap-theme).

## Testing

Global NPM dependencies: `nodeunit`

    npm test

## Credits

Based on [NarrativeScience/Log.io](https://github.com/NarrativeScience/Log.io).

- Mike Smatherzs &lt;msmathers@narrativescience.com&gt; ([msmathers](http://github.com/msmathers))
- Narrative Science http://narrativescience.com ([NarrativeScience](http://github.com/NarrativeScience))
- muchweb ([muchweb](http://github.com/muchweb))

## Acknowledgements

- Jeremy Ashkenas ([jashkenas](https://github.com/jashkenas))
- Guillermo Rauch &lt;guillermo@learnboost.com&gt; ([Guille](http://github.com/guille))
- Ryan Dahl &lt;ry at tiny clouds dot org&gt; ([ry](https://github.com/ry)) + Joyent http://www.joyent.com/ ([joyent](https://github.com/joyent/))
- [turtlebender](http://github.com/turtlebender)
- [jdrake](http://github.com/jdrake)

## :free: License

This program is free software: you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with this program.  If not, see <http://www.gnu.org/licenses/>.