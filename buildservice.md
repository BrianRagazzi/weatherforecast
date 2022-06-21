
# Use with Tanzu Build Service:

## Create secret for local repo (destination)
```
kp secret create harbor-creds --registry harbor.lab.brianragazzi.com --registry-user "harboradmin@ragazzilab.com"
```

## Create secret for GitHub (source)
```
kp secret create git-creds --git-url https://github.com --git-user BrianRagazzi
```

## Create image
```
kp image create weatherforecast-service-api --tag harbor.lab.brianragazzi.com/library/weatherforecast-service-api --git https://github.com/BrianRagazzi/weatherforecast.git --sub-path src/weatherforecast-service/ --registry-ca-cert-path ca.crt --git-revision main --wait
```

# Check our work
```
kp image list
kp build status weatherforecast-service-api
kp image status weatherforecast-service-api
kp build logs weatherforecast-service-api
```