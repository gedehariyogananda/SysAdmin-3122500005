getting started

<img src="./media/image27.png"
style="width:6.26772in;height:1.47222in" />

drag zip init dan unzip

<img src="./media/image16.png"
style="width:6.26772in;height:2.73611in" />

drag file Dockerfile

<img src="./media/image21.png"
style="width:6.26772in;height:0.27778in" />

berisi config :  
FROM node:10-alpine

WORKDIR /app

COPY . .

RUN yarn install --production

CMD \["node", "/app/src/index.js"\]

Build the container image using the docker build command.

<img src="./media/image58.png"
style="width:6.26772in;height:1.95833in" />

sudah berhasil

<img src="./media/image41.png"
style="width:6.26772in;height:0.86111in" />

start docker nya :

<img src="./media/image1.png"
style="width:6.26772in;height:0.70833in" />

berikut output nya di port 3000

<img src="./media/image50.png"
style="width:6.26772in;height:3.13889in" />

Update our app

<img src="./media/image5.png"
style="width:6.26772in;height:2.95833in" />

akan melakukan update pada code

<img src="./media/image28.png"
style="width:6.26772in;height:1.33333in" />

diupdate menjadi

<img src="./media/image60.png"
style="width:6.26772in;height:1.09722in" />

lalu save

<img src="./media/image17.png"
style="width:1.54167in;height:0.65625in" />

lalu build ulang docker :

<img src="./media/image13.png"
style="width:6.26772in;height:1.94444in" />

akan melakukan proses building

note : harus ada titik (.) di belakang nama yang ingin dibuild

mulai start new container

<img src="./media/image14.png"
style="width:6.26772in;height:0.48611in" />

<img src="./media/image14.png"
style="width:6.26772in;height:0.48611in" />

akan error, karena container tersebut menggunakan port host 3000 dan
hanya satu proses (termasuk container) yang dapat mendengarkan port
tersebut. Untuk memperbaikinya, kita perlu menghapus container lama

—

untuk menghapus container lama, kita harus docker stop

<img src="./media/image47.png"
style="width:6.26772in;height:0.51389in" />

gunakan **docker stop \<id_docker\>** untuk menghentikan container lama

<img src="./media/image53.png"
style="width:6.26772in;height:0.98611in" />

<img src="./media/image36.png"
style="width:5.30208in;height:0.53125in" />

**bisa remove sekalian dari docker container dengan docker rm**

<img src="./media/image54.png"
style="width:4.92708in;height:0.66667in" />

sudah hilang dari container kita :

<img src="./media/image31.png" style="width:6.26772in;height:0.5in" />

lalu coba jalankan kembali yang tadi di lagi karena port 3000 sudah
tidak terpakai :

<img src="./media/image6.png"
style="width:6.26772in;height:0.48611in" />

lihat hasil nya :

<img src="./media/image45.png"
style="width:6.26772in;height:1.56944in" />

**SHARING OUR APP**

create repository pada dokumentasi

<img src="./media/image46.png"
style="width:6.26772in;height:2.65278in" />

lalu buat repository , lalu create

<img src="./media/image56.png"
style="width:6.26772in;height:3.72222in" />

lalu push image nya di terimnal untuk dapat repository nya

<img src="./media/image34.png"
style="width:4.44271in;height:1.63096in" />

failed :

<img src="./media/image62.png"
style="width:6.26772in;height:0.69444in" />

karena perintah push sedang mencari gambar bernama
dockersamples/101-todo-app, tetapi tidak menemukannya. Jika Anda
menjalankan docker image ls, Anda juga tidak akan melihatnya.

Untuk memperbaikinya, kita perlu "memberi tag" pada gambar kita, yang
pada dasarnya berarti memberinya nama lain.

<img src="./media/image40.png"
style="width:6.26772in;height:1.88889in" />

<img src="./media/image59.png"
style="width:6.26772in;height:0.63889in" />

PERSISTING OUT DB

<img src="./media/image15.png"
style="width:6.26772in;height:1.31944in" />

VALIDATE

<img src="./media/image52.png"
style="width:6.26772in;height:2.91667in" />

ada random number yaitu 813

setelah docker ps -a

<img src="./media/image57.png" style="width:6.26772in;height:1.625in" />

menjadi 2, jadi ada kesalaha

jadi remove yang container yang pertama

<img src="./media/image25.png"
style="width:5.83333in;height:0.96875in" />

buat docker volume create

<img src="./media/image4.png"
style="width:6.26772in;height:0.70833in" />

run

<img src="./media/image30.png" style="width:6.26772in;height:0.625in" />

tampil dan silahkan insert data

<img src="./media/image44.png"
style="width:6.26772in;height:2.65278in" />

lalu coba remove the todo container

<img src="./media/image2.png"
style="width:6.26772in;height:0.98611in" />

run kembali todo yang baru, cek apakah data kesimpan

<img src="./media/image7.png" style="width:6.26772in;height:0.625in" />

alhasil jika dibuak di port 3000

<img src="./media/image33.png"
style="width:6.26772in;height:2.91667in" />

data tetap tersimpan

lalu cek volum

<img src="./media/image26.png"
style="width:6.26772in;height:2.05556in" />

USING BIND MOUNTH

<img src="./media/image51.png"
style="width:6.26772in;height:1.79167in" />

- -dp 3000:3000 - same as before. Run in detached (background) mode and
  create a port mapping

- -w /app - sets the "working directory" or the current directory that
  the command will run from

- node:10-alpine - the image to use. Note that this is the base image
  for our app from the Dockerfile

- sh -c "yarn install && yarn run dev" - the command. We're starting a
  shell using sh (alpine doesn't have bash) and running yarn install to
  install *all* dependencies and then running yarn run dev. If we look
  in the package.json, we'll see that the dev script is starting
  nodemon.

berikut adlah container id nya dan jalankan docker logs -f \<id nya\>

<img src="./media/image35.png"
style="width:6.26772in;height:2.31944in" />

<img src="./media/image10.png"
style="width:6.26772in;height:1.95833in" />

listening on port 3000

lalu coba rubah file di app.js

<img src="./media/image42.png"
style="width:6.26772in;height:1.33333in" />

menjadi

<img src="./media/image32.png"
style="width:6.26772in;height:1.51389in" />

sudah berhasil berubah menjadi add

<img src="./media/image19.png"
style="width:6.26772in;height:1.44444in" />

sesuai dengan yang saya edit

MUTLI CONTAINER APPS

<img src="./media/image55.png"
style="width:6.26772in;height:0.54167in" />

lakukan docker run pada network todo-app dan setup mysql password dan
mysql database nya

<img src="./media/image61.png"
style="width:6.26772in;height:1.95833in" />

run docker container mysql

<img src="./media/image3.png"
style="width:6.26772in;height:2.05556in" />

<img src="./media/image37.png"
style="width:6.26772in;height:0.38889in" />

berhasil

<img src="./media/image20.png"
style="width:6.26772in;height:1.95833in" />

<img src="./media/image24.png"
style="width:6.26772in;height:1.16667in" />

coba show databses untuk liat database yang ada :

<img src="./media/image38.png"
style="width:6.26772in;height:2.31944in" />

CONNECT TO MY SQL

<img src="./media/image22.png"
style="width:6.26772in;height:2.04167in" />

WELCOME TO NEXTSHOOT

<img src="./media/image29.png"
style="width:6.26772in;height:1.91667in" />

<img src="./media/image48.png"
style="width:6.26772in;height:2.22222in" />

<img src="./media/image9.png"
style="width:6.26772in;height:1.90278in" />

setup database todo-app

<img src="./media/image8.png"
style="width:6.26772in;height:0.48611in" />

nge run dan masukkan data

<img src="./media/image11.png"
style="width:6.26772in;height:0.36111in" />

<img src="./media/image23.png"
style="width:6.26772in;height:3.02778in" />

data pun tampil :

<img src="./media/image49.png"
style="width:6.26772in;height:1.48611in" />

<img src="./media/image43.png"
style="width:6.26772in;height:2.97222in" />

<img src="./media/image12.png"
style="width:6.26772in;height:1.33333in" />

<img src="./media/image39.png"
style="width:6.33184in;height:1.77754in" />

docker compose down

<img src="./media/image18.png"
style="width:6.26772in;height:0.79167in" />
