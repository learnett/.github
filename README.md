<a id="readme-top"></a>

<br/>
<br/>

<!-- <p align="center">
  <img src="doc/logo.png" alt="Logo" width="192" />
</p>
<br/>
<p align="center">
<a href="">Website</a> -
<a href="">Status</a> -
<a href="">Documentation</a>
</p> -->

**Cram.AI** is an all in one AI study platform with AI summaries of class notes, lectures, and PDFs, as well as AI generated flashcards

## Structure
| Path                    | Description        |
| ----------------------- | ------------------ |
| `./api`                 | API for the website|
| `./cram`                 | Ollama API |
| `./web`                 | dashboard for cram.ai |
| `./migrations`           | kysely database migrations |
---

**Fill in the environment variables before deploying. All data is stored in a Postgresql database.**

<details>
  <summary>Table of Contents</summary>
  <ol>
    <li>
      <a href="#cram-ai">About The Project</a>
      <ul>
        <li><a href="#built-with">Built With</a></li>
      </ul>
    </li>
    <li>
      <a href="#setup">Setup</a>
      <a href="#deploy">Deploy</a>
      <a href="#updating">Updating</a>
    </li>
    <li><a href="#contributing">Contributing</a></li>
    <li><a href="#license">License</a></li>
  </ol>
</details>

### Built With
* [![Python][Python]][Python-url]
* [![Typescript][Typescript]][Typescript-url]
* [![Next.js][Next.js]][Next-url]
* [![React.js][React.js]][React-url]

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## Setup
> [!IMPORTANT]  
> Open a new issue if you find any bugs

Prerequisites: 
- Node.js @ https://nodejs.org/en/download
- npm install -g pnpm

`./api`
- cd api
- create .env
```env
JWT_SECRET="" # openssl rand -base64 32
DATABASE_URL="postgresql://postgres:hamburger@localhost:5432/cramai"
REDIS_STRING="redis://localhost:6379"
PORT=3001
API_URL="http://localhost:3001"
DASHBOARD_URL="http://localhost:3000"

INNGEST_EVENT_KEY=local
INNGEST_BASE_URL=http://localhost:8288
INNGEST_DEV=1

CRAM_AI_ROUTE=http://192.168.1.229:2727

AWS_ACCESS_KEY_ID=minioadmin
AWS_SECRET_ACCESS_KEY=minioadmin
AWS_REGION=us-east-1
S3_BUCKET_NAME=cramai
AWS_ENDPOINT="http://localhost:9000"
COOKIE_DOMAIN=localhost
```
- pnpm install
- pnpm dev

`./web`
- cd web
- create .env
```env
CRAMAI_SECRET="123456"
AWS_ACCESS_KEY_ID=minioadmin
AWS_SECRET_ACCESS_KEY=minioadmin
AWS_REGION=us-east-1
S3_BUCKET_NAME=cramai
NEXT_PUBLIC_API_URL=http://localhost:3001
NEXT_PUBLIC_COOKIE_DOMAIN=localhost
BACKEND_API_KEY=123456
```
- pnpm install
- pnpm dev

See the [open issues](https://github.com/Decompile1/cram-ai/issues) for a full list of proposed features and known issues.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## Deploy
```
cd api
docker build -t cram-api .
docker compose up -d
```
```
cd cram
docker build -t cram-ai .
docker compose up -d
```
```
cd web
docker build -t cram-web .
docker compose up -d
```

```
docker pull postgres
docker volume create postgres_data
sudo docker run -d --name postgres_container -e POSTGRES_PASSWORD=hamburgers -p 5432:5432 -v postgres_data:/var/lib/postgresql/data postgres
docker ps
```

```
docker pull redis
docker run -d --name cram-ai-redis -p 6379:6379 redis
docker ps
```

## Updating
```
# if any errors
git reset --hard

git pull

docker compose -f docker-compose.gpu down
docker compose -f docker-compose.gpu up -d --build

# dev testing
sudo docker compose -f docker-compose.gpu build --no-cache
docker compose -f docker-compose.gpu up -d
```
use --no-cache if you are having caching issues with docker

## Contributing

Contributions is what makes the open source community such an amazing place to learn, inspire, and create. Any contributions you make are **greatly appreciated**!

To contribute, please fork the repo and create a pull request. You can also simply open an issue with the tag "enhancement".
Don't forget to give the project a star!

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

### Top contributors:

<a href="https://github.com/Decompile1/cram-ai/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=Decompile1/cram-ai" alt="contrib.rocks image" />
</a>

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- LICENSE -->
## License
<a href="https://www.gnu.org/licenses/gpl-3.0.en.html">
  <img align="right" height="72" alt="GNU GENERAL PUBLIC LICENSE v3.0" src="doc/GPLv3_Logo.png" />
</a>
Cram-AI is licensed under the GNU GENERAL PUBLIC LICENSE v3.0. See LICENSE for more information.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## Resources
- https://www.postgresql.org/download/macosx/
- https://postgresapp.com/
- https://redis.io/docs/latest/operate/oss_and_stack/install/install-redis/install-redis-on-mac-os/
- https://nodejs.org/en/download

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## Star History

[![Star History Chart](https://api.star-history.com/svg?repos=decompile1/cram-ai&type=date&legend=top-left)](https://www.star-history.com/#decompile1/cram-ai&type=date&legend=top-left)

[contributors-shield]: https://img.shields.io/github/contributors/Decompile1/cram-ai.svg?style=for-the-badge
[contributors-url]: https://github.com/Decompile1/cram-ai/graphs/contributors
[forks-shield]: https://img.shields.io/github/forks/Decompile1/cram-ai.svg?style=for-the-badge
[forks-url]: https://github.com/Decompile1/cram-ai/network/members
[stars-shield]: https://img.shields.io/github/stars/Decompile1/cram-ai.svg?style=for-the-badge
[stars-url]: https://github.com/Decompile1/cram-ai/stargazers
[issues-shield]: https://img.shields.io/github/issues/Decompile1/cram-ai.svg?style=for-the-badge
[issues-url]: https://github.com/Decompile1/cram-ai/issues
[license-shield]: https://img.shields.io/github/license/Decompile1/cram-ai.svg?style=for-the-badge
[license-url]: https://github.com/Decompile1/cram-ai/blob/master/LICENSE.txt
[product-screenshot]: /screenshot.png
[Next.js]: https://img.shields.io/badge/next.js-000000?style=for-the-badge&logo=nextdotjs&logoColor=white
[Next-url]: https://nextjs.org/
[React.js]: https://img.shields.io/badge/React-20232A?style=for-the-badge&logo=react&logoColor=61DAFB
[React-url]: https://reactjs.org/
[Typescript]: https://img.shields.io/badge/Typescript-20232A?style=for-the-badge&logo=typescript&logoColor=61DAFB
[Python]: https://img.shields.io/badge/Python-20232A?style=for-the-badge&logo=python&logoColor=61DAFB
[Python-url]: https://www.python.org/
[Typescript-url]: https://www.typescriptlang.org/