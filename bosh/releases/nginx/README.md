
## Nginx Release

### Prerequisite

Go to [https://bosh.io/docs/bosh-lite/](https://bosh.io/docs/bosh-lite/) and setup Bosh Lite on your local system and update the cloud config too.

### Steps

Follow the following steps to run and deploy the Nginx release:

1.Clone the repository using the following steps:
```
git clone https://github.com/Talha345/tmp-homework-tm.git
cd tmp-homework-tm/bosh/releases/nginx
```


2.Upload Ubuntu Jammy Stemcell.
```
bosh upload-stemcell --sha1 399a544080b9e1c37bd3fd7fe2c653c02ddc3b20 \
  https://bosh.io/d/stemcells/bosh-warden-boshlite-ubuntu-jammy-go_agent?v=1.18
```

3.Upload the release to the director.
```
bosh -e vbox upload-release nginx_1.22.0.tgz
```

4.Deploy the release
```
bosh -e vbox -d nginx deploy manifests/nginx.yml
```
5.Test the release using the following steps:
- Visit [http://10.244.0.34/](http://10.244.0.34/).
- Enter the following credentials:
  - username: admin
  - password: admin
- You will be greeted by the Nginx welcome page.