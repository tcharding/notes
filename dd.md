making disk images
------------------

Maybe we should be using ddrescue instead?  

First zero the disk by creating a file of zero's and deleting it
* dd if=/dev/zero of=/tmp/delete.me bs=8M; rm delete.me

Next, create image and pipe it throup gzip
* dd if=/dev/hda conv=sync,noerror bs=4M | gzip -c > /mnt/sda1/hda.img.gz

Or over the network
* dd if/dev/hda | gzip -1 | ssh user@host dd of=/path/to/file.img.gz

To restore pipe gzip into dd (you can leave off conv arg)
* gunzip -c /mnt/sda1/hda.img.gz | dd of=/dev/hda conv=sync,noerror bs=4M

source:  http://www.linuxweblog.com/dd-image

skipping parts of image
* dd if=file.img of=/dev/sd*1 skip=NUM seek=NUM count=NUM
> NUM is blocks
> skip is NUM * 512 (or if bs=4M then  NUM * 512 * 8 (4M = 8*512) 

check dd progress
* pgrep -l '^dd$'

kill it
* kill -USR1 4295

