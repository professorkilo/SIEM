﻿index=pan_logs sourcetype=pan:traffic earliest=-1h
| stats dc(dest_ip) as dest_ip_count values(dest_ip) as dest_ips by index, src_ip
| where dest_ip_count > 10
| table index, src_ip, dest_ips, dest_ip_count