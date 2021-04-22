# Domain Setup

 - Go to aws management console -> services / products -> route 53 -> create hosted zone -> Enter domain name(with out http or www)
 - Create record set (required 2 recprd) -> name:blank, type: A-IPv4 Address, value: instance public ip (no www or http)
 - Create one more record -> name:www, type: CNAME - Canonical name, value: domainname.com
 - Set 4 type **NS** or name server in hosting -> From google domain -> dns -> use custom namesever -> paste 4 name server here
 - Go to instance -> right click -> instance setting -> get system log
 
 > register domain
 - If we registered using namecheap or