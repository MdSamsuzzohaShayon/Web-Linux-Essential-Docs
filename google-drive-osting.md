# Google drive web hosting

[tutorial](https://www.youtube.com/watch?v=qtQ9TvQLKjc)

### hosting

 - upload project folder containing **index.html**
 - rename thr project folder -> make sure write **www** in front of project
 - Example: __www.md-shayon.com__
 - go to this address: __https://drv.tw/__ -> select google drive
 - sign in with the account containing my project
 - Website has been hosted they will give you the domain

### Changing domainname

 - login to domain provider website 
 - namecheap -> login -> purchase a domain 
 - domain list -> manage your domain
 - nameserver -> Namecheap BasicDNS
 - Advanced DNS -> Add new record -> CNAME Record 
 - host -> **www** 
 - target -> website url generated previously
 - remove https:// from beganning
 - remove all text after **on.drv.tw** 
 - Example: 
   
   Orginal __https://wthjc5ozxu4fhfxr2floxq-on.drv.tw/www.md-shayon.com__
   After edit __wthjc5ozxu4fhfxr2floxq-on.drv.tw__
	    
 - TTL -> 30 minutes

 - add new record -> url redirect record -> host: **@** -> Destination URL: __http://www.yourdomain.com__


 - Check dns propagation __whatsmydns.net/#ns/__
 - Proxy tool, Bypass Local __kproxy.com__

### Make website faster 

 - go to __cloudflase.com__ and create a account
 - Add site -> type domain -> next -> freeplan -> purchase
 - copy the value of cname
 - create a new txt record 
 - name: **www** -> click configure: value of cname and add **CRVTW=** at beganning
 - Save
 - Copy cloudflare dns and paste it in namecheap
 - namecheap -> nameserver -> custom dns -> paste it here
