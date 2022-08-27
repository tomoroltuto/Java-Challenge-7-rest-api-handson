# 概要
このプロジェクトはREST APIの利用方法についてハンズオンした実行結果まとめたものです。

# やったこと

* ①ターミナルからGitHubに(GET・POST・PATCH・DELETE)リクエスト
* ②PostmanからGitHubに(GET・POST・PATCH・DELETE)リクエスト

## ①ターミナルからGitHubに(GET・POST・PATCH・DELETE)リクエスト

実行結果を以下にまとめます。

* GETリクエスト

コマンド

```bash
curl -i -u tomoroltuto:ghp_個人アクセストークン https://api.github.com/user'
``` 

実行結果

```bash
HTTP/2 200 
server: GitHub.com
date: Thu, 25 Aug 2022 15:09:28 GMT
content-type: application/json; charset=utf-8
...
{
   "login": "tomoroltuto",
  ...
}
``` 
* POSTリクエスト

コマンド

```bash
curl -i -X POST \-H "Authorization: token ghp_個人アクセストークン" \
    -d '{
        "name": "blog",
        "auto_init": true,
        "private": true,
        "gitignore_template": "nanoc"
      }' \
    https://api.github.com/user/repos
``` 

実行結果
```bash
HTTP/2 201 
...
location: https://api.github.com/repos/tomoroltuto/blog

{
...
"name": "blog"
...
 "private": true
...
"html_url": "https://github.com/tomoroltuto"
...
  "created_at": "2022-08-26T12:08:07Z",
  "updated_at": "2022-08-26T12:08:07Z",
  "pushed_at": "2022-08-26T12:08:07Z",
...
 "visibility": "private",
...
}
``` 

* PATCHリクエスト

コマンド
```bash
curl -i -X PATCH \
 -H "Accept: application/vnd.github.v3+json" \
 -H "Authorization: token ghp_個人アクセストークン" \
 https://api.github.com/repos/tomoroltuto/blog \      
 -d '{
  "name":"hello-world-blog",
  "description":"This is your blog repository",
  "homepage":"https://github.com",
  "private":false
 }'
``` 

実行結果
```bash
HTTP/2 200 
server: GitHub.com
...
{
...
 "name": "hello-world-blog"
...
  "private": false,
...
  "html_url": "https://github.com/tomoroltuto/hello-world-blog",
  "description": "This is your blog repository",
...
  "created_at": "2022-08-26T12:08:07Z",
  "updated_at": "2022-08-26T13:02:11Z",
  "pushed_at": "2022-08-26T12:08:07Z",
...
  "homepage": "https://github.com",
...
 "visibility": "public",
...
``` 

* DELETEリクエスト

コマンド
```bash
curl -i -X DELETE \
  -H "Accept: application/vnd.github.v3+json" \
  -H "Authorization: token ghp_個人アクセストークン" \
  https://api.github.com/repos/tomoroltuto/hello-world-blog
``` 

実行結果
```bash
HTTP/2 204 
server: GitHub.com
date: Fri, 26 Aug 2022 14:33:53 GMT
x-oauth-scopes: admin:enterprise, admin:gpg_key, admin:org, admin:org_hook, admin:public_key, admin:repo_hook, admin:ssh_signing_key, delete:packages, delete_repo, gist, notifications, project, repo, user, workflow, write:discussion, write:packages
x-accepted-oauth-scopes: delete_repo
github-authentication-token-expiration: 2022-11-24 14:32:04 UTC
x-github-media-type: github.v3; format=json
x-ratelimit-limit: 5000
x-ratelimit-remaining: 4993
x-ratelimit-reset: 1661526356
x-ratelimit-used: 7
x-ratelimit-resource: core
access-control-expose-headers: ETag, Link, Location, Retry-After, X-GitHub-OTP, X-RateLimit-Limit, X-RateLimit-Remaining, X-RateLimit-Used, X-RateLimit-Resource, X-RateLimit-Reset, X-OAuth-Scopes, X-Accepted-OAuth-Scopes, X-Poll-Interval, X-GitHub-Media-Type, X-GitHub-SSO, X-GitHub-Request-Id, Deprecation, Sunset
access-control-allow-origin: *
strict-transport-security: max-age=31536000; includeSubdomains; preload
x-frame-options: deny
x-content-type-options: nosniff
x-xss-protection: 0
referrer-policy: origin-when-cross-origin, strict-origin-when-cross-origin
content-security-policy: default-src 'none'
vary: Accept-Encoding, Accept, X-Requested-With
x-github-request-id: CE44:76B8:17BDE4:1B843B:6308D9D0
``` 

## ②PostmanからGitHubに(GET・POST・PATCH・DELETE)リクエスト
* GETリクエスト

<img width="1440" alt="GETリクエスト" src="https://user-images.githubusercontent.com/90845405/187032008-d7a90889-1f44-4445-b4ca-a112d5de8604.png">

* POSTリクエスト

<img width="1440" alt="POSTリクエスト" src="https://user-images.githubusercontent.com/90845405/187032106-44f963ec-07b7-4ea5-87aa-a1751208552a.png">

* PATCHリクエスト

<img width="1440" alt="PATCHリクエスト" src="https://user-images.githubusercontent.com/90845405/187032020-d6a10877-2a81-483c-ab2d-865676374e2d.png">

* DELETEリクエスト

<img width="1440" alt="DELETEリクエスト" src="https://user-images.githubusercontent.com/90845405/187032026-63dac6e3-f3ca-481c-90dd-5264f1e35d62.png">
