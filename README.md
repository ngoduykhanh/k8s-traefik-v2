# k8s-traefik-v2
Traefik v2 deployment to kubernetes

# Notes

Copy from my riginal blog post https://blog.ndk.name/kubernetes-and-traefik-v2

Put everything in the same folder, then we can deploy easily with a single command

```shell
$ kubectl apply -f .
```

However, before you apply, take notes:

* I use `default` namespace, change it if you want
* I use `DaemonSet` instead of `Deployment`, change it if you want
* I use `entrypoints.web.http.redirections.entryPoint.to=websecure` to force a redirection from *http* to *https* globally without `middleware` configs. Remove it if you don't want
* I use `tls-ndk-name` as my TLS secret. Please change it.
* The dashboard is secured with a basic authentication. You can generate a base64-encoded of *htpasswd* with command `htpasswd -nb user password | openssl base64`
* I don't use **Ingress**, I use **IngressRoute**. Yes, it is a new *kind* in Traefik v2.
