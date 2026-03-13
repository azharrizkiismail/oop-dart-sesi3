# Resume Materi Sesi 3
## Constructor dan Enkapsulasi pada Dart (Object Oriented Programming)

**Nama :** Azhar Rizki Ismail 
**NIM :** 23141005P
**Kelas :** SI6KR
**Mata Kuliah :** Pemrograman Berorientasi Objek  

---

# Pendahuluan

Object Oriented Programming (OOP) merupakan paradigma pemrograman yang berfokus pada objek. Dalam OOP, program dibangun menggunakan konsep class dan object. Class merupakan blueprint atau cetak biru yang digunakan untuk membuat objek, sedangkan objek merupakan instance dari class yang memiliki atribut dan method tertentu.

Dalam bahasa pemrograman Dart, konsep OOP sangat penting karena digunakan dalam pengembangan berbagai aplikasi modern, terutama pada pengembangan aplikasi menggunakan framework Flutter. Pada sesi ini dipelajari dua konsep penting dalam OOP yaitu constructor dan enkapsulasi.

Constructor digunakan untuk menginisialisasi objek ketika objek dibuat, sedangkan enkapsulasi digunakan untuk melindungi data dalam sebuah class agar tidak dapat diakses secara langsung dari luar class tanpa kontrol tertentu. Dengan memahami kedua konsep ini, programmer dapat membuat program yang lebih aman, terstruktur, dan mudah dikembangkan.

---

# Constructor pada Dart

## Pengertian Constructor

Constructor adalah method khusus yang terdapat dalam sebuah class yang digunakan untuk menginisialisasi objek saat objek tersebut dibuat. Constructor memiliki nama yang sama dengan class dan akan dipanggil secara otomatis ketika objek dibuat.

Ciri-ciri constructor antara lain:

- Memiliki nama yang sama dengan class
- Tidak memiliki tipe return
- Dipanggil secara otomatis saat objek dibuat
- Digunakan untuk memberikan nilai awal pada atribut objek

Contoh constructor sederhana:

```dart
class Buku {
  String judul;

  Buku(this.judul);
}

void main() {
  var buku1 = Buku("Pemrograman Dart");
  print(buku1.judul);
}
```

---

# Jenis-Jenis Constructor di Dart

Dalam bahasa pemrograman Dart terdapat beberapa jenis constructor yang dapat digunakan sesuai kebutuhan.

## 1. Default Constructor

Default constructor merupakan constructor standar yang digunakan ketika objek dibuat. Constructor ini biasanya digunakan untuk memberikan nilai awal pada atribut objek.

### Contoh :

```dart
class Mahasiswa {
  String nama;
  int umur;

  Mahasiswa(this.nama, this.umur);
}

void main() {
  var mhs = Mahasiswa("Andi", 20);
  print(mhs.nama);
}
```

## 2. Named Constructor

Named constructor merupakan constructor yang memiliki nama tambahan sehingga satu class dapat memiliki lebih dari satu constructor dengan fungsi yang berbeda.

### Contoh :

```dart
class Mobil {
  String? merk;
  int? tahun;

  Mobil(this.merk, this.tahun);

  Mobil.baru() {
    merk = "Toyota";
    tahun = 2023;
  }

  Mobil.lama() {
    merk = "Honda";
    tahun = 2015;
  }
}

void main() {
  var mobil1 = Mobil("Suzuki", 2020);
  var mobil2 = Mobil.baru();

  print(mobil1.merk);
  print(mobil2.merk);
}
```

## 3. Parameterized Constructor

Parameterized constructor adalah constructor yang menerima parameter sehingga nilai atribut dapat ditentukan saat objek dibuat.

### Contoh :

```dart
class Produk {
  String nama;
  double harga;

  Produk(this.nama, this.harga);
}

void main() {
  var produk1 = Produk("Laptop", 8000000);
  print(produk1.nama);
}
```

## 4. Constant Constructor

Constant constructor digunakan untuk membuat objek yang bersifat immutable atau tidak dapat diubah. Untuk menggunakan constant constructor, semua atribut dalam class harus bertipe final.

Keuntungan menggunakan constant constructor adalah dapat menghemat penggunaan memori karena objek dengan nilai yang sama akan menggunakan instance yang sama.

### Contoh :

```dart
class Warna {
  final int r;
  final int g;
  final int b;

  const Warna(this.r, this.g, this.b);
}

void main() {
  const merah = Warna(255,0,0);
  const merahLagi = Warna(255,0,0);

  print(merah);
  print(merahLagi);
}
```

---

# Constructor dengan Initializer List

Initializer list digunakan untuk menginisialisasi variabel sebelum body constructor dijalankan. Biasanya digunakan untuk field bertipe final atau untuk melakukan validasi data.

### Contoh :

```dart
class Titik {
  final double x;
  final double y;

  Titik(double x, double y)
      : x = x.abs(),
        y = y.abs() {
    print("Titik dibuat di ($x,$y)");
  }
}
```

---

# Enkapsulasi

Enkapsulasi merupakan konsep dalam OOP yang digunakan untuk menyembunyikan detail implementasi suatu class dan melindungi data agar tidak dapat diakses secara langsung dari luar class.

Tujuan utama dari enkapsulasi antara lain :
- Melindungi data dari perubahan yang tidak diinginkan
- Mengontrol akses terhadap atribut
- Membuat kode lebih terstruktur
- Mempermudah perawatan program

Dalam Dart, enkapsulasi dilakukan dengan menggunakan underscore _ untuk membuat variabel menjadi private.

### Contoh :

```dart
class Person {
  String _name;
  int age;

  Person(this._name, this.age);
}
```

---

# Public dan Private pada Dart

Dalam Dart terdapat dua jenis akses variabel yaitu public dan private.

## Public

Variabel public dapat diakses dari mana saja dalam program.

### Contoh :

```dart
String nama;
```

## Private

Variabel private hanya dapat diakses dalam file yang sama dan biasanya menggunakan underscore

### Contoh :

```dart
String _nama;
```

---

# Getter

Getter digunakan untuk mengambil atau membaca nilai dari variabel private.

### Contoh :

```dart
class Person {
  String _name;

  Person(this._name);

  String get name {
    return _name;
  }
}

void main() {
  var p = Person("Budi");
  print(p.name);
}
```

---

# Setter

Setter digunakan untuk mengubah nilai variabel private dengan aturan atau validasi tertentu.

### Contoh :

```dart
class Produk {
  String _nama;
  double _harga;

  Produk(this._nama, this._harga);

  set harga(double value) {
    if(value > 0){
      _harga = value;
    } else {
      print("Harga tidak valid");
    }
  }
}
```

---

# Contoh Getter dan Setter Lengkap

```dart
class Produk {
  String _nama;
  double _harga;

  Produk(this._nama, this._harga);

  String get nama => _nama;
  double get harga => _harga;

  set nama(String value) {
    if(value.length >= 3){
      _nama = value;
    }
  }

  set harga(double value) {
    if(value > 0){
      _harga = value;
    }
  }
}
```

---

# Studi Kasus Sistem Login Sederhana

Contoh penerapan enkapsulasi dapat dilihat pada sistem login sederhana berikut :

```dart
class User {
  String _username;
  String _password;

  User(this._username, this._password);

  String get username => _username;

  bool login(String username, String password) {
    return _username == username && _password == password;
  }

  void gantiPassword(String lama, String baru) {
    if(_password == lama){
      if(baru.length >= 8){
        _password = baru;
        print("Password berhasil diubah");
      } else {
        print("Password baru minimal 8 karakter");
      }
    } else {
      print("Password lama salah");
    }
  }
}
```

---

# Kesimpulan

Constructor dan enkapsulasi merupakan konsep penting dalam Object Oriented Programming yang digunakan dalam bahasa pemrograman Dart. Constructor berfungsi untuk menginisialisasi objek saat pertama kali dibuat sehingga objek memiliki nilai awal yang sesuai.

Dart menyediakan beberapa jenis constructor seperti default constructor, named constructor, parameterized constructor, dan constant constructor yang dapat digunakan sesuai kebutuhan program.

Sementara itu, enkapsulasi digunakan untuk melindungi data dalam class dengan cara membatasi akses langsung terhadap variabel menggunakan konsep private. Dengan adanya getter dan setter, programmer tetap dapat mengakses serta memodifikasi data dengan kontrol dan validasi tertentu.

Dengan menerapkan constructor dan enkapsulasi dengan baik, program yang dibuat akan menjadi lebih aman, terstruktur, mudah dipelihara, serta lebih fleksibel untuk pengembangan di masa depan.

---

# Latihan : Simulasi Rekening Bank

```dart
class RekeningBank {

  String _nomorRekening;
  double _saldo;

  RekeningBank(this._nomorRekening, this._saldo);

  void deposit(double jumlah){

    if(jumlah > 0){
      _saldo += jumlah;
      print("Deposit berhasil. Saldo sekarang: $_saldo");
    }
    else{
      print("Jumlah deposit tidak valid");
    }

  }

  void tarik(double jumlah){

    if(jumlah <= _saldo){
      _saldo -= jumlah;
      print("Penarikan berhasil. Saldo sekarang: $_saldo");
    }
    else{
      print("Saldo tidak mencukupi");
    }

  }

  void cekSaldo(){
    print("Saldo saat ini: $_saldo");
  }

}

void main(){

  var rekening = RekeningBank("123456789", 1000000);

  rekening.cekSaldo();
  rekening.deposit(500000);
  rekening.tarik(300000);
  rekening.cekSaldo();

}
```

---

# Latihan : Multiple Constructor pada Class Mahasiswa

Pada latihan ini dibuat sebuah class Mahasiswa yang memiliki beberapa constructor berbeda, yaitu default constructor, named constructor dariMap(), dan named constructor tanpaNama(). Tujuannya adalah untuk memahami bagaimana sebuah class dapat memiliki lebih dari satu cara dalam membuat objek.

```dart
class Mahasiswa {

  String? nama;
  int? umur;
  String? jurusan;

  // Default Constructor
  Mahasiswa(this.nama, this.umur, this.jurusan);

  // Named Constructor dari Map
  Mahasiswa.dariMap(Map<String, dynamic> data) {
    nama = data['nama'];
    umur = data['umur'];
    jurusan = data['jurusan'];
  }

  // Named Constructor tanpa nama
  Mahasiswa.tanpaNama() {
    nama = "Tidak diketahui";
    umur = 0;
    jurusan = "Belum ditentukan";
  }

  void tampilkanData() {
    print("Nama: $nama");
    print("Umur: $umur");
    print("Jurusan: $jurusan");
    print("------------------");
  }
}

void main() {

  // Objek menggunakan default constructor
  var mhs1 = Mahasiswa("Andi", 20, "Informatika");

  // Objek menggunakan named constructor dariMap
  var dataMahasiswa = {
    "nama": "Budi",
    "umur": 21,
    "jurusan": "Sistem Informasi"
  };

  var mhs2 = Mahasiswa.dariMap(dataMahasiswa);

  // Objek menggunakan named constructor tanpaNama
  var mhs3 = Mahasiswa.tanpaNama();

  // Menampilkan data
  mhs1.tampilkanData();
  mhs2.tampilkanData();
  mhs3.tampilkanData();
}
```

---

# Latihan : Enkapsulasi Lengkap pada Class User

Pada latihan ini dibuat sebuah class User yang menerapkan konsep enkapsulasi. Data dalam class dibuat private dengan menggunakan tanda underscore. Untuk mengakses dan memodifikasi data tersebut digunakan getter dan setter dengan validasi tertentu.

```dart
class User {

  String _username;
  String _password;
  String _email;

  // Constructor
  User(this._username, this._password, this._email);

  // Getter
  String get username => _username;
  String get password => _password;
  String get email => _email;

  // Setter username
  set username(String value) {
    if (value.length >= 5) {
      _username = value;
      print("Username berhasil diubah menjadi: $value");
    } else {
      print("Username gagal diubah. Minimal 5 karakter.");
    }
  }

  // Setter password
  set password(String value) {
    if (value.length >= 8) {
      _password = value;
      print("Password berhasil diubah.");
    } else {
      print("Password gagal diubah. Minimal 8 karakter.");
    }
  }

  // Setter email
  set email(String value) {
    if (value.contains("@")) {
      _email = value;
      print("Email berhasil diubah menjadi: $value");
    } else {
      print("Email tidak valid. Harus mengandung '@'.");
    }
  }
}

void main() {

  // Membuat objek User
  var user1 = User("admin01", "password123", "admin@email.com");

  print("Data Awal User:");
  print("Username: ${user1.username}");
  print("Password: ${user1.password}");
  print("Email: ${user1.email}");

  print("\nMengubah Data User:");

  // Mengubah username
  user1.username = "andi123";

  // Mengubah password
  user1.password = "passbaru123";

  // Mengubah email
  user1.email = "andi@email.com";

  print("\nData Setelah Diubah:");
  print("Username: ${user1.username}");
  print("Password: ${user1.password}");
  print("Email: ${user1.email}");
}
```
