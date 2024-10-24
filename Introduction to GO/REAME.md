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

### Encapsulate Logic with Functions
```
package main

import "fmt"

func greetUsers(conferenceName string, conferenceTickets int, remainingTickets int) {
    fmt.Printf("Selamat datang di %s konferensi!\n", conferenceName)
    fmt.Printf("Kami memiliki total %d tiket, dan %d tiket yang tersisa.\n", conferenceTickets, remainingTickets)
}

func main() {
    // Memanggil fungsi
    greetUsers("GoLang Conference", 50, 50)
}
```

*Penjelasan* :
- Fungsi `greetUsers` : memisahkan logika `greetUsers` dari fungsi main

### Organize Code with Go Packages
- Membuat Package
    1. Buat folder baru dengan nama package, misalnya `helper`
    2. Buat file Go di dalam folder tersebut, misalnya `helper.go`
    3. Dalam file `helper.go`, tulislah fungsi yang akan di-export dengan menggunakan huruf kapital di awal nama fungsi.

    ```
    // helper/helper.go
    package helper

    import "fmt"

    // Fungsi yang diekspor dari package helper
    func Greet(name string) {
        fmt.Printf("Halo, %s!\n", name)
    }
    ```

    ```
    // main.go
    package main

    import (
        "helper" // Mengimpor package helper
    )

    func main() {
        helper.Greet("Dunia")
    }
    ```

*Penjelasan* :
- `Packages` : Kumpulan file Go yang dikelompokkan bersama

     Dengan menggunakan packages, bisa membagi kode menjadi bagian-bagian yang terpisah berdasarkan fungsionalitasnya

### Scope Rules in Go

1. `Local Scope`: Variabel yang `dideklarasikan dalam fungsi` hanya dapat `diakses dalam fungsi` tersebut

2. `Package Scope`: Variabel yang `dideklarasikan di luar fungsi` tetapi dalam file yang sama `dapat diakses oleh semua fungsi di package yang sama`

3. `Global Scope`: Variabel yang `diekspor dengan huruf kapital` di awal namanya bisa `diakses oleh semua package lain yang mengimpornya`

```
package main

import "fmt"

var packageLevelVariable = "Ini bisa diakses di seluruh package"

func main() {
    localVariable := "Ini hanya bisa diakses di dalam fungsi main"
    fmt.Println(localVariable)
    fmt.Println(packageLevelVariable)
}

func anotherFunction() {
    // fmt.Println(localVariable) // Tidak bisa diakses, karena localVariable hanya ada di main
    fmt.Println(packageLevelVariable) // Bisa diakses karena package scope
}
```

### Maps
```
package main

import "fmt"

func main() {
    // Membuat map
    user := map[string]string{
        "firstName": "John",
        "lastName":  "Doe",
        "email":     "john.doe@example.com",
    }

    // Mengakses nilai di map
    fmt.Println(user["firstName"])
    fmt.Println(user["lastName"])

    // Menambahkan atau memperbarui nilai di map
    user["email"] = "john.newemail@example.com"
    fmt.Println(user["email"])
}
```

*Penjelasan* :
- `Maps` : tipe data yang memungkinkan untuk menyimpan pasangan key-value

    Maps sangat berguna ketika perlu mengasosiasikan sebuah nilai dengan sebuah key tertentu

### Struct
```
package main

import "fmt"

// Mendefinisikan struct
type User struct {
    firstName string
    lastName  string
    email     string
    tickets   int
}

func main() {
    // Membuat instance dari struct
    user := User{
        firstName: "Jane",
        lastName:  "Doe",
        email:     "jane.doe@example.com",
        tickets:   2,
    }

    // Mengakses field dari struct
    fmt.Printf("Nama depan: %s, Nama belakang: %s, Email: %s, Tiket: %d\n", user.firstName, user.lastName, user.email, user.tickets)
}
```

*Penjelasan* :
- `Struct` : Untuk mendefinisikan tipe data yang lebih kompleks, yang bisa mencakup beberapa tipe data berbeda

### Goroutines - Concurrency in Go
```
package main

import (
    "fmt"
    "time"
)

// Fungsi yang berjalan dalam goroutine
func sendTicket(name string) {
    time.Sleep(2 * time.Second)
    fmt.Printf("Tiket terkirim ke %s\n", name)
}

func main() {
    fmt.Println("Memulai pengiriman tiket...")
    
    // Membuat goroutine
    go sendTicket("Alice")
    go sendTicket("Bob")

    // Memberi waktu agar goroutine selesai sebelum program berakhir
    time.Sleep(3 * time.Second)
    fmt.Println("Program selesai.")
}
```

*Penjelasan* :
- `Goroutines` : Untuk menjalankan proses secara bersamaan (concurrency)

    Dapat membuat goroutine hanya dengan menambahkan kata kunci `go` sebelum pemanggilan fungsi. Ini memungkinkan fungsi berjalan secara paralel tanpa memblokir eksekusi program utama.

- Pada contoh di atas, `sendTicket` berjalan dalam `goroutine`, yang artinya fungsinya dijalankan secara paralel.

     Dengan `time.Sleep`, kita memberi waktu untuk goroutine selesai sebelum program utama berakhir