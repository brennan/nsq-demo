Simple node server that subscribes to NSQ topics on localhost.

# Usage

## Install and Run NSQ

`brew install nsq`

`nsqlookupd`

Sample output:

```shell
[nsqlookupd] 2021/03/26 09:31:07.501600 INFO: nsqlookupd v1.2.0 (built w/go1.13.5)
[nsqlookupd] 2021/03/26 09:31:07.502282 INFO: TCP: listening on [::]:4160
[nsqlookupd] 2021/03/26 09:31:07.502315 INFO: HTTP: listening on [::]:4161
```

`nsqd -data-path=/usr/local/var/nsq -lookupd-tcp-address localhost:4160`

Sample output:

```shell
[nsqd] 2021/03/26 09:36:48.796461 INFO: TCP: listening on [::]:4150
[nsqd] 2021/03/26 09:36:48.796859 INFO: HTTP: listening on [::]:4151
```

## Start Server

`yarn install && node server.js`

Then, send a post request to `localhost:4151/pub?topic=<your_topic>`; any JSON payload can be provided as the message body, such as `{"text": "something"}`.

Sample `server.js` output:

```shell
Received message [0ebaa4ac2754b000]: text=something
```

To view your topics and payloads in a browser:

`nsqadmin --lookupd-http-address localhost:4161`

Then, navigate to `localhost:4171`.
