Created with https://jekyllrb.com/

# Deployment

``` bash
# install s3_website gem
# https://github.com/laurilehmijoki/s3_website
gem install s3_website
s3_website cfg create

# comment out entries for s3_id and s3_secret
# create access key for jekyll user in AWS console
export AWS_ACCESS_KEY_ID=access_key_id
export AWS_SECRET_ACCESS_KEY=secret_access_key

# install openjdk version 8
# download .pkg from https://adoptopenjdk.net/archive.html?variant=openjdk8&jvmVariant=hotspot
export PATH=/Library/Java/JavaVirtualMachines/adoptopenjdk-8.jdk/Contents/Home/bin:$PATH

# deploy website to S3
s3_website push
```
