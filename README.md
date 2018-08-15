# travisonfire

## prerequisites

- [Node.js](https://nodejs.org)
- [Docker](https://www.docker.com/) or [Ruby](https://www.ruby-lang.org/)

## how to

- Create a new project on [Firebase](https://console.firebase.google.com)
- Create a new repo on GitHub
- Clone it locally

  ```shell
  git clone https://github.com/bartw/mygreatproject
  ``` 

- Create an index.html for your site

  ```shell
  cd travisonfire
  mkdir public
  touch public/index.html
  ```

- Install the Firebase tools

  ```shell
  npm install -g firebase-tools
  ```

- Login

  ```shell
  firebase login
  ```

- Initiate your project

  ```shell
  firebase init
  ```

  - Select at least "hosting"
  - Select your project
  - It doesn't really matter if you create a single page app or not
  - Don't overwrite your clean index.html

- Go to [Travis](https://travis-ci.org) and activate your repository

- Install Travis CLI directly or use Docker
  
  ```shell
  # only run the docker command if you don't have and don't want to install Ruby
  docker run -it --rm ruby:latest bash
  gem install travis
  ```

- Generate a Firebase token

  ```shell
  # run this outside of your Docker container
  firebase login:ci
  ```

- Encrypt the Firebase token using the Travis CLI

  ```shell
  travis encrypt "1/yourToken" -r githubusername/reponame
  ```

- Create your travis.yml file

  ```shell
  touch .travis.yml
  ```

  ```yml
  language: node_js
  node_js:
    - "node"
  deploy:
    provider: firebase
    token:
      secure: "encrypted"
  ```

## license

This repo is licensed under the [MIT License](LICENSE).
