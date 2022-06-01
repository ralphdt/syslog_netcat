echo '<14>sourechost message text' | nc -v -t -w 1 192.168.1.248 514

INSTALL LOGSTASH SYSLOG OUTPUT PLUGIN >>

/usr/share/logstash/bin/logstash-plugin install logstash-output-syslog

COPY THIS FILE INTO >>

/usr/share/logstash/logstash.conf

input {
 syslog {
  type => syslog
  port => 5514
 }
}

filter { }

output {
 syslog {
  host => "192.168.1.248"
  port => 514
  protocol => "tcp"
  rfc => "rfc3164"
 }
}
