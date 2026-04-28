
Nama : Sinurat, Federico

NRP : 5025241244

Demo : https://youtu.be/XsvpEWVRi0g
 

1.  Array adalah struktur data linear yang menyimpan kumpulan elemen dengan tipe data yang sama dalam lokasi memori yang berurutan. Setiap elemen diakses menggunakan indeks (biasanya dimulai dari 0).

Contoh Penggunaan dalam Aplikasi:

    Aplikasi Kasir/Toko: Menyimpan daftar harga barang sementara yang dibeli pelanggan dalam satu transaksi.

    Game: Menyimpan status papan permainan (misalnya matriks/array 2D untuk papan catur atau Tic-Tac-Toe), atau daftar skor leaderboard.

    Sistem Akademik: Menyimpan nilai ujian dari 50 mahasiswa di satu kelas untuk kemudian dihitung rata-ratanya.

2. a) <img width="466" height="336" alt="Screenshot 2026-04-28 180056" src="https://github.com/user-attachments/assets/a19e6ac8-e702-4804-8a9e-8c33cb89ee5b" />

 b) <img width="452" height="348" alt="Screenshot 2026-04-28 180229" src="https://github.com/user-attachments/assets/366acee8-5ace-4f14-bcd7-91e4b9394fb2" />

 c) <img width="371" height="362" alt="Screenshot 2026-04-28 180603" src="https://github.com/user-attachments/assets/2e748de5-7c49-4085-9a2c-108fc3f18009" />

 
 3. Kode : 
```
#include <iostream>
#include <stack>
#include <string>
#include <cctype>

using namespace std;

int precedence(char op) {
    if (op == '^')
        return 3;
    if (op == '*' || op == '/')
        return 2;
    if (op == '+' || op == '-')
        return 1;
    return -1;
}

string infixToPostfix(string s) {
    stack<char> st;
    string result;

    for (int i = 0; i < s.length(); i++) {
        char c = s[i];

        if (c == ' ') continue;

        if (isalnum(c)) {
            result += c;
            result += ' ';
        }
        else if (c == '(') {
            st.push('(');
        }
        else if (c == ')') {
            while (!st.empty() && st.top() != '(') {
                result += st.top();
                result += ' ';
                st.pop();
            }
            st.pop();
        }
        else {
            while (!st.empty() && precedence(s[i]) <= precedence(st.top())) {
                if (c == '^' && st.top() == '^') {
                    break;
                }
                else {
                    result += st.top();
                    result += ' ';
                    st.pop();
                }
            }
            st.push(c);
        }
    }

    while (!st.empty()) {
        result += st.top();
        result += ' ';
        st.pop();
    }

    return result;
}

int main() {
    string infix_expr = "a + (2 * b^3) / (f - g) + d * h";
    
    cout << "Ekspresi Infix   : " << infix_expr << endl;
    
    string postfix_expr = infixToPostfix(infix_expr);
    
    cout << "Ekspresi Postfix : " << postfix_expr << endl;

    return 0;
}
```
 output : <img width="513" height="82" alt="Screenshot 2026-04-28 181852" src="https://github.com/user-attachments/assets/9056e948-7c69-4602-9a09-d930703fd4a0" />

 
 4. <img width="499" height="668" alt="Screenshot 2026-04-28 184328" src="https://github.com/user-attachments/assets/6936697f-c060-452a-b3df-3b0f0a50b42e" />

 
 
 
 
5.
1)
Queue adalah struktur data linear dengan prinsip FIFO, elemen yang pertama masuk adalah yang pertama keluar. Dalam sistem layanan akademik:
Konsep Queue	Implementasi di Sistem
Enqueue	Mahasiswa ambil nomor antrian → masuk ke Rear
Dequeue	Petugas memanggil mahasiswa → keluar dari Front
Front	Mahasiswa yang sedang/akan dilayani
Rear	Mahasiswa terakhir yang baru masuk antrian
isEmpty	Tidak ada mahasiswa dalam antrian
isFull	Antrian sudah mencapai kapasitas maksimum

Alur kerja: mahasiswa datang → enqueue → menunggu → dipanggil petugas → dequeue → dilayani → selesai.

2) 

Algoritma Enqueue (Tambah Antrean):

    Cek apakah antrean sudah penuh (IsFull).

    Jika penuh, tampilkan pesan "Antrean Penuh".

    Jika tidak penuh:

        Jika antrean kosong, set front = 0.

        Geser/Tambah posisi rear sebanyak 1.

        Masukkan data mahasiswa ke posisi rear.

Algoritma Dequeue (Layani Mahasiswa):

    Cek apakah antrean kosong (IsEmpty).

    Jika kosong, tampilkan pesan "Antrean Kosong".

    Jika tidak kosong:

        Ambil data mahasiswa di posisi front (tampilkan siapa yang dilayani).

        Geser posisi front ke elemen berikutnya atau geser semua elemen ke depan.

        Jika setelah dihapus antrean jadi kosong, reset front dan rear ke kondisi awal.
          

 3) 
```
#include <iostream>
#include <string>

using namespace std;

string q[10];
int rear = -1;

void enqueue(string nama) {
    if (rear < 9) {
        q[++rear] = nama;
        cout << nama << " masuk antrean.\n";
    } else {
        cout << "Antrean penuh.\n";
    }
}

void dequeue() {
    if (rear >= 0) {
        cout << q[0] << " dilayani dan keluar antrean.\n";
        for (int i = 0; i < rear; i++) {
            q[i] = q[i + 1];
        }
        rear--;
    } else {
        cout << "Antrean kosong.\n";
    }
}

void display() {
    cout << "Kondisi Antrean: ";
    if (rear == -1) {
        cout << "Kosong";
    }
    for (int i = 0; i <= rear; i++) {
        cout << q[i] << (i == rear ? "" : " - ");
    }
    cout << "\n\n";
}
``` 
 4) 
```
int main() {
    enqueue("A");
    enqueue("B");
    enqueue("C");
    display();

    dequeue();
    display();

    enqueue("D");
    display();

    return 0;
}
 ```
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
  
