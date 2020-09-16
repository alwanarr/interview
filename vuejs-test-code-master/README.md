# vue-test-code

## Project setup

```
yarn install
```

### Compiles and hot-reloads for development

```
yarn serve
```

### Compiles and minifies for production

```
yarn build
```

### Lints and fixes files

```
yarn lint
```

### Customize configuration

See [Configuration Reference](https://cli.vuejs.org/config/).

Expected Output :
![expected](./src/assets/Expected.png)

##error
1.method setData yang memanggil store mutataions yang tidak ditemukan
2.lalu saya ganti setDatas menjadi setData
3.mutations tidak ditemukan
4.lalu saya ganti mutations yang di actions/commit menjadi SET_DATA
5.state list yang bernilai null saya ganti menjadi array kosong []
6.getters getCountData yang me return 0
7.saya ubah menjadi return state list lalu di computed count (user component)
saya kasih keyword (length) karena state lists sudah saya ubah menjadi array ([]). jadi ketika axios tidak mendapatkan data atau error maka count akan bernilai 0 ([].length array kosong).

dan jika prosoes di axios berhasil maka state lists akan terisi data object di dalam array. karena tipe datanya array maka bisa di kasih keyword length.

Terimakasihh..
