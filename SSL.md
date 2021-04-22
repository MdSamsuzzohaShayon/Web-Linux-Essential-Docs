### Securing websites
 - [install certbot](https://www.digitalocean.com/community/tutorials/how-to-set-up-let-s-encrypt-with-nginx-server-blocks-on-ubuntu-16-04) -> Let’s Encrypt is a Certificate Authority (CA) that provides an easy way to obtain and install free TLS/SSL certificates,
   ```
   sudo add-apt-repository ppa:certbot/certbot
   sudo apt-get update
   sudo apt install python3-certbot-nginx -y
   ```
 - Allowing HTTPS Through the Firewall (We did it previously - check once again)
   ```
   sudo ufw status
   # IF IT IS DISABLE - ENABLE ONCE AGAIN
   sudo ufw allow 'Nginx Full'
   sudo ufw delete allow 'Nginx HTTP'
   ```
 - Now obtain ssl certificate
   ```
   sudo certbot --nginx -d somedomain.com -d www.somedomain.com
   # IT WILL ASK FOR EMAIL ADDRESS ENT THAT 
   # A FOR AGREE
   # Choose redirect (2)
   ```