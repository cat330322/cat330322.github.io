npm install -g yarn --registry=https://registry.npm.taobao.org
yarn install --registry=https://registry.npm.taobao.org
yarn serve
yarn build

docker run --name=dockervue -d -p 8088:80 20211130-1540
docker build -t 20211130-1540 .