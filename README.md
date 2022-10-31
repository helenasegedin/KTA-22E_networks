# KTA-22E_networks
## Udacity e-kursus
### Ettevalmistus
* Google Cloud Shell: `sudo apt-get update && sudo apt-get install netcat-openbsd tcpdump traceroute mtr iputils-ping lsof -y`
(Teeb uuendused ja paigaldab vajalikud utiliidid.)
### Käsud
* `ip addr show eth0`
* `ip route show`
* `ping -c3 8.8.8.8` - Saadab 3 paketti Google teenusele aadressil 8.8.8.8, mis saadetakse tagasi, kui kõik toimib.
* `host -t aaaa google.com`
* `host -t mx udacity.com`
* `tcpdump -n -c5 -i eth0 port 22`
? "You don't have permission to capture on that device" ?
* `traceroute www.udacity.com`
* `mtr www.udacity.com`

* `printf 'HEAD / HTTP/1.1\r\nHost: www.udacity.com\r\n\r\n' | nc www.udacity.com 80` - saadab tagasi veebilehe http päise: status code, header fields, cookies
  * nc = netcat - võtab ühendust mis iganes hostiga, ei pea olema www aadress, vaid võib olla ka nt localhost port 22 või meiliserver
  * | - vertical bar pipe, võtab eelneva programmi väljundi ja kasutab järgneva programmi sisendina
  * 'HEAD / HTTP/1.1\r\nHost: www.udacity.com\r\n\r\n' on string, mis moodustab http päringu, nc käsk saadab selle määratud aadressile/pordile ja kuvab väljundi 
  * Host: www.udacity.com näitab, mis hosti kohta me infot tahame
* `man nc` - netcati juhend
* `nc -l 3456` - kuula porti 3456, `-l` tähendab "listen"

* http kasutab porti 80, ssh porti 22
* rst = reset package, kui server ei kuula porti ja ei vasta

* TCP ühendus (`nc -l 3456` ja `nc localhost 3456`) - mõlemad hostid saavad teisele sõnumeid saata; ühenduse sulgemiseks ctrl-D
