# 1inch Nginx Proxy

This repository contains a simple setup to run an Nginx proxy locally to properly proxy all requests to the 1inch API.

# Why use a proxy with the 1inch API?

Non-proxied 1inch API requests from a web browser will always throw a CORS error. This is done to keep 1inch API keys off of frontends where nefarious users can extract them while listening to network calls. By executing 1inch API requests on a separate backend, the API key is no longer living in the same environment as the users.

# Prerequisites

- [Docker Compose](https://docs.docker.com/compose/install/)

# Setup

1. Clone this repository to the machine that will be running the proxy.
2. in `./nginx.conf`, replace `replace_with_your_dev_portal_token` with your Dev Portal API key.
3. Run `docker-compose up` in the root of the repository.

Now you have an nginx proxy running locally to properly handle all 1inch API requests

The beginning of all request strings to the 1inch APIs should now be changed from `https://api.1inch.dev/` to `http://localhost:8888/`

**NOTE:** Requests to the nginx proxy should always use http and **not** https. The conversion to https will be handled by nginx automatically