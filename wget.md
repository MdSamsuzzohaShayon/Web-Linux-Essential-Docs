# Wget
 - [Docs](https://www.computerhope.com/unix/wget.htm)
 - [ Download A Website With Wget The Right Way](https://simpleit.rocks/linux/how-to-download-a-website-with-wget-the-right-way/)
```
wget --wait=2 \
     --level=inf \
	 --limit-rate=20K \
	 --recursive \
	 --page-requisites \
	 --user-agent=Mozilla \
	 --no-parent \
	 --convert-links \
	 --adjust-extension \
	 --no-clobber \
	 -e robots=off \
	 https://example.com
```
 - `wget --wait=2 --level=inf --limit-rate=20K --recursive --page-requisites --user-agent=Mozilla --no-parent --convert-links --adjust-extension --no-clobber -e robots=off https://example.com`
