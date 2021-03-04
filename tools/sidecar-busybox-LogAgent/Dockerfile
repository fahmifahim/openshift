FROM busybox:latest
#I am using busybox v.1.32.1

COPY ./rsync /bin/rsync
#Don't forget to prepare your rsync binary file
CMD ["/bin/rsync"]

#Notes:
#You need to prepare for all related library to fully execute the rsync command
#Check the related library with: ldd $(which rsync) on your Linux machine
#Then, put the related library to your busybox image
