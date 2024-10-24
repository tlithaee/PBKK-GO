# TABLE OF CONTENTS
- [Introduction to GO](#introduction-to-go)
- [GO Syntax and Concepts](#go-syntax-and-concepts)



## INTRODUCTION TO GO
### What?
Go adalah bahasa pemrograman open-source yang dirancang oleh Google untuk membuat perangkat lunak yang efisien, cepat, dan mudah dipahami.

### Why?
Go memiliki performa yang sangat baik karena dikompilasi langsung ke kode mesin. Ini juga mendukung concurrency dengan baik melalui goroutines yang ringan

### How?
Go lebih sederhana daripada banyak bahasa modern karena memiliki sedikit fitur yang kompleks (seperti warisan kelas atau generik) dan fokus pada efisiensi.

## GO SYNTAX and CONCEPTS
### Local Setup - Install Go & Editor
1. Instalasi Go:
    - Unduh Go:
    https://golang.org/dl/.

2. Proses Instalasi:
    - Pada Windows, ini berarti menjalankan file `.msi` dan mengikuti wizard instalasi.

    - Untuk memastikan instalasi berhasil, buka terminal atau command prompt dan ketik perintah berikut:
    ```
    go version
    ```

    Jika Go berhasil diinstal, Anda akan melihat output yang menunjukkan versi Go yang terinstal, misalnya:
    ```
    go version go1.19.3 darwin/amd64
    ```

3. Go Modules

    Untuk mengelola dependensi eksternal atau library pihak ketiga dalam proyek.

    - Buka direktori proyek Anda di terminal, lalu jalankan perintah berikut untuk membuat file `go.mod` yang mendefinisikan modul Go untuk proyek tersebut:
    ```
    go mod init <nama-modul>
    ```
    - Perintah ini akan membuat file `go.mod` di direktori proyek, yang akan melacak semua dependensi dan versi yang digunakan dalam proyek tersebut.

### Write our First Program & Structure of a Go File
- Struktur dasar dari file Go selalu dimulai dengan deklarasi package:
    ```
    package main

    import "fmt"

    func main() {
        fmt.Println("Hello, World!")
    }
    ```
    *Penjelasan* :
    - Fungsi `main`: Fungsi ini adalah entry point dari program Go. Semua kode akan dimulai dari sini.

### Variables & Constants in Go
- Deklarasi Variabel :
    ```
    var name string = "John"
    age := 30
    ```

- Deklarasi Konstanta :
    ```
    const PI = 3.14
    ```
*Penjelasan* :
- Go memiliki tipe data `statis`, jadi variabel harus dideklarasikan dengan tipe tertentu dan tidak bisa diubah-ubah.

### Formatted Output - printf
```
fmt.Printf("Hello %s, you are %d years old.\n", name, age)
```

*Penjelasan* :
- Go menggunakan `fmt.Printf` untuk mencetak keluaran yang diformat
- Format `%s` untuk string, `%d` untuk integer, `%f` untuk float, etc.

### Data Types in Go
```
var height float64 = 5.9
```

*Penjelasan* :
- Tipe Data Dasar: 

    `Int`, `float64`, `string`, `bool`, `array`, dan `slice`.

### Getting User Input
```
var name string
fmt.Print("Enter your name: ")
fmt.Scan(&name)
fmt.Printf("Hello, %s!\n", name)
```

*Penjelasan* :
- Untuk mendapatkan input pengguna, kita bisa menggunakan `fmt.Scan`

### What is a Pointer?
```
var x int = 10
var p *int = &x
fmt.Println(*p) // Output: 10
```
*Penjelasan* :
- Pointer menyimpan alamat memori dari variabel. 
- Operator `&` = mendapatkan alamat memori
- Operator `*` = mengakses nilai di alamat tersebut.

### Book Ticket Logic
```
var tickets int = 50
var booked int

fmt.Print("How many tickets? ")
fmt.Scan(&booked)

tickets -= booked
fmt.Printf("Tickets remaining: %d\n", tickets)
```

### Arrays & Slices
- `Array` : Tipe data dengan ukuran tetap
    ```
    var names [3]string = [3]string{"John", "Jane", "Doe"}
    ```

- `Slice` : Tipe data dinamis yang bisa berubah ukuran
    ```
    names := []string{"John", "Jane", "Doe"}
    names = append(names, "Alice")
    ```

### Loops in Go
- `For Loop` :  Satu-satunya jenis loop di Go adalah `for`
    ```
    for i := 0; i < 10; i++ {
    fmt.Println(i)
    }
    ```

- `Range` : Dapat digunakan untuk iterasi pada slice atau array
    ```
    for index, value := range names {
    fmt.Printf("%d: %s\n", index, value)
    }
    ```

### Conditionals (if / else) and Boolean Data Type
```
age := 20
if age >= 18 {
    fmt.Println("Adult")
} else {
    fmt.Println("Minor")
}
```

*Penjelasan* :
- Boolean : `true`, `false`
- Operator perbandingan dan logika : `&&`, `||`, `!`

### Validate User Input
```
if len(name) < 2 {
    fmt.Println("Name is too short")
}
if !strings.Contains(email, "@") {
    fmt.Println("Invalid email address")
}
```

*Penjelasan* :
- Validasi Input Pengguna: 
    - Nama harus `>2 karakter`
    - Email harus memiliki karakter `@`

### Switch Statement
```
switch city {
case "New York":
    fmt.Println("Booking for New York")
case "London":
    fmt.Println("Booking for London")
default:
    fmt.Println("No valid city selected")
}
```

*Penjelasan* :
- Switch Statement: Alternatif lebih sederhana untuk if else dengan beberapa kondisi.