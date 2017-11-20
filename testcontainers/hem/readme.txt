docker run --rm -it --name hem -v `pwd`/build/:/usr/share/nginx/html/ -p 3333:80 nginx:1.13-alpine

docker build . -t hem:2
docker tag hem:2 localhost:5000/hem:0.0.2


