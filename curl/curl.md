# CURL

 - [docs](https://curl.se/docs/projdocs.html)

 - *curl is used in command lines or scripts to transfer data. It is also used in cars, television sets, routers, printers,     audio equipment, mobile phones, tablets, settop boxes, media players and is the internet transfer backbone for thousands of software applications affecting billions of humans daily.*

 - *Curl is essentially utility that allows you to transfer data to or from a network server using one of those supported protocols. Protocall that it support our http, https,ftp, ftps, sftp, tftp etc.*


| man curl                                                                                                | get the descriptions and details manual            |
|---------------------------------------------------------------------------------------------------------|----------------------------------------------------|
| curl --help                                                                                             | commands helps                                     |
| curl https://inkscape.org                                                                               | returns content of entire webpage                  |
| curl -o Documents/Web-Linux-Essential-Docs/curl/inkscape.html https://inkscape.org                      | Extract complete webpage in a html file            |
| curl -o inkscape.AppImage https://media.inkscape.org/dl/resources/file/Inkscape-3bc2e81-x86_64.AppImage | Download a file and rename                         |
| curl -O https://media.inkscape.org/dl/resources/file/Inkscape-3bc2e81-x86_64.AppImage                   | Download with original name                        |
| curl -L http://inkscape.org/                                                                            | Redirect to appropate web page                     |
| curl -I http://inkscape.org/                                                                            | Get response of particular web server              |
| curl -v https://inkscape.org/                                                                           | TLS handshake .  Make the operation more talkative |
| curl --data "log=admin&pwd=password" https://wordpress.com/wp-login.php                                 | Wordpress login with curl                          |
