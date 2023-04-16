# Quay Container Registry on Docker compose with SSL for any IP address

This is a docker-compose file to run a Quay Container Registry with SSL for any IP address you want!

It is preconfigured and ready to use:

- when pulling the image for the first time, you must login to quay.io:

    ```bash
    docker login -u="redhat+quay" -p="O81WSHRSJR14UAZBK54GQHJS0P1V4CLWAJV1X2C4SD7KO59CQ9N3RE12612XU1HR" quay.io
    ```

run the containers with
```bash
docker-compose up -d
```

You now have to assign the hostname to an ip address:

- either write this line to your `/etc/hosts` file:

```bash
127.0.0.1     quay.localhost.direct
```

- or install [DNSmasq](https://thekelleys.org.uk/dnsmasq/doc.html)

- or override the DNS service in your local network if accessable to you (e.g. in your FritzBox or OPNSense router)

Go to <https://quay.localhost.direct> !

---

## troubleshooting


```bash
 ⠋ quay-db Pulling                                                                                                    2.1s
   ⠇ 5181eccc7c90 Downloading [>                                                  ]       ...                         0.8s
Error response from daemon: failed to resolve reference "quay.io/project-quay/quay:3.8.5": pulling from host quay.io failed with status code [manifests 3.8.5]: 401 UNAUTHORIZED
```

- login to quay with
  - `docker login -u="redhat+quay" -p="O81WSHRSJR14UAZBK54GQHJS0P1V4CLWAJV1X2C4SD7KO59CQ9N3RE12612XU1HR" quay.io`

- see  <https://access.redhat.com/solutions/3533201>

---
## Links

- <https://access.redhat.com/documentation/de-de/red_hat_quay/2.9/html/deploy_red_hat_quay_-_basic/installing_red_hat_quay_basic>
