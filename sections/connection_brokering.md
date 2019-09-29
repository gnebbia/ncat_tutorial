
One of ncat's most useful and unique abilities is called "
connection brokering". A listening ncat in broker mode accepts
connections from multiple clients. In this mode, anything
received from one of the clients is sent back out to all the
others. In this way an Ncat broker acts like a network hub,
broadcasting all traffic to everyone connected. We can activate
broker mode with the "--broker" option, which must be combined
with the "--listen", since it wouldn't make any sense for a client
to be a broker. Brokering can be used even for:

- Transfer files through restrictive firewalls
- Multi-user chat rooms

