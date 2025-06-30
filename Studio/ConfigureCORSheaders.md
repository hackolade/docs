# Configure CORS headers

This page is only relevant for you for self-hosted repository hub: GitHub Server, GitLab Server or Bitbucket Data Center, and to let users open Hackolade data models from that repository hub using the Hackolade browser application: [https://studio.hackolade.com](<https://studio.hackolade.com> "target=\"\_blank\"").&nbsp; You may skip it if it is not the case.

&nbsp;

## Problem

By default, a web browser (e.g. Chrome, Edge) does not allow a script loaded from an origin to send HTTP requests to another origin. That security mechanism is known as the [same-origin policy](<https://developer.mozilla.org/en-US/docs/Web/Security/Same-origin\_policy> "target=\"\_blank\"").

&nbsp;

The same-origin policy of the browser will prevent the Hackolade Studio browser application (which is loaded from [https://studio.hackolade.com](<https://studio.hackolade.com> "target=\"\_blank\"")) from querying your self-hosted repository hub (which is hosted at a different origin, if self-hosted.)&nbsp; As a consequence, the application will throw an error when a user tries to connect to your repository hub:

&nbsp;

> The connection failed because \<your self-hosted repository hub\> rejected the cross-origin request from https://studio.hackolade.com.

&nbsp;

## Solution

To let the Hackolade Studio browser application contact your self-hosted repository hub, you need to enable [cross-origin resource sharing (CORS)](<https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS> "target=\"\_blank\""). This comes down to configuring the following HTTP headers for your repository hub.

[](<https://developer.mozilla.org/fr/docs/Web/HTTP/Headers/Access-Control-Allow-Origin>)

> [Access-Control-Allow-Origin](<https://developer.mozilla.org/fr/docs/Web/HTTP/Headers/Access-Control-Allow-Origin> "target=\"\_blank\""): https://studio.hackolade.com

> [Access-Control-Allow-Methods](<https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Access-Control-Allow-Methods> "target=\"\_blank\""): \*

> [Access-Control-Allow-Headers](<https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Access-Control-Allow-Headers> "target=\"\_blank\""): \*

&nbsp;

The location where you need to configure those headers depends on your infrastructure.

&nbsp;

\- If you use **GitHub Server**, then [this document](<https://docs.github.com/en/enterprise-server@3.10/rest/using-the-rest-api/using-cors-and-jsonp-to-make-cross-origin-requests?apiVersion=2022-11-28> "target=\"\_blank\"") suggests that CORS should be enabled by default. So no action is required.

\- If you use **GitLab Server**, then [this discussion](<https://gitlab.com/gitlab-org/omnibus-gitlab/-/issues/5425> "target=\"\_blank\"") suggests that CORS should also be enabled by default for /api requests. So no action is required either.

\- If you use **Bitbucket Data Center**, then CORS is not enabled by default and there is unfortunately no [configuration properties](<https://confluence.atlassian.com/bitbucketserver/configuration-properties-776640155.html> "target=\"\_blank\"") for it. The solution is to set up a reverse proxy (e.g. [nginx](<https://nginx.org/en/> "target=\"\_blank\""), [traefik](<https://doc.traefik.io/traefik/> "target=\"\_blank\"")) in front of your Bitbucket Data Center instance and to configure the HTTP headers for CORS there.

&nbsp;

