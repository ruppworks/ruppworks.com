# Instructions to update and deploy as of 2026-03-08

``` bash
aws --profile ruppworks sso login
mkdir /tmp/ruppworks.com
cd /tmp/ruppworks.com
aws --profile ruppworks s3 sync s3://ruppworks.com .
# make changes
aws --profile ruppworks s3 sync . s3://ruppworks.com
aws --profile ruppworks cloudfront list-distributions
# find distribution ID; DistributionList.Items[0].Id
aws --profile ruppworks cloudfront create-invalidation --distribution-id E2URGNHKOTRLEU --paths "/*"

# ALT: use Jekyll + GitHub repo
cd ~/Developer/ruppworks.com
# make changes
jekyll build
cd _site
# sync to S3 and invalidate CloudFront as described above
```

## ARCHIVE
### previous instructions
Created with https://jekyllrb.com/

### Deployment

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
