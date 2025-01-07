# cloudflare-docker-proxy

![deploy](https://github.com/liujixingnan/cloudflare-docker-proxy/actions/workflows/deploy.yaml/badge.svg)

[![Deploy to Cloudflare Workers](https://[src](src)deploy.workers.cloudflare.com/button)](https://deploy.workers.cloudflare.com/?url=https://github.com/liujixingnan/cloudflare-docker-proxy)

> If you're looking for proxy for helm, maybe you can try [cloudflare-helm-proxy](https://github.com/ciiiii/cloudflare-helm-proxy).

## Deploy

1. click the "Deploy With Workers" button
2. follow the instructions to fork and deploy
3. update routes as you requirement

[![Deploy to Cloudflare Workers](https://deploy.workers.cloudflare.com/button)](https://deploy.workers.cloudflare.com/?url=https://github.com/liujixingnan/cloudflare-docker-proxy)

## Routes configuration tutorial

1. use cloudflare worker host: only support proxy one registry
   ```javascript
   const routes = {
     "${workername}.${username}.workers.dev/": "https://registry-1.docker.io",
   };
   ```
2. use custom domain: support proxy multiple registries route by host
   - host your domain DNS on cloudflare
   - add `A` record of xxx.example.com to `192.0.2.1`
   - deploy this project to cloudflare workers
   - add `xxx.example.com/*` to HTTP routes of workers
   - add more records and modify the config as you need
   ```javascript
   const routes = {
     "docker-io.liuji.site": "https://registry-1.docker.io",
     "gcr-io.liuji.site": "https://gcr.io",
     "ghcr-io.liuji.site": "https://ghcr.io",
     "quay-io.liuji.site": "https://quay.io",
     "registry-k8s-io.liuji.site": "https://registry.k8s.io",
  	 "docker.liuji.site": "https://hub.docker.com",
  	 "github.liuji.site": "https://github.com",
  	 "raw-githubusercontent-com.liuji.site": "https://raw.githubusercontent.com",
  	 "github-io.liuji.site": "https://renlm.github.io",
  	 "grafana-github-io.liuji.site": "https://grafana.github.io",
   };
   ```

