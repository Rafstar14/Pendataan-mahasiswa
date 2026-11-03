#include <iostream>
#include <string>
#include <iomanip>

using namespace std;

const int MAKS_MHS = 1000;

// Fungsi untuk memastikan string hanya berisi angka (0-9) tanpa huruf/spasi
bool validasiHanyaAngka(const string& teks) {
    if (teks.empty()) return false;
    for (size_t i = 0; i < teks.length(); i++) {
        if (teks[i] < '0' || teks[i] > '9') {
            return false;
        }
    }
    return true;
}

int main() {
    string inputJumlah;
    int jumlahMhs = 0;

    // 1. Menentukan jumlah mahasiswa di terminal (1 sampai MAKS_MHS)
    do {
        cout << "jumlah mahasiswa yang ingin didata (1-" << MAKS_MHS << "): ";
        if (!getline(cin, inputJumlah)) return 1; // input terputus (EOF)

        // Batas 4 digit mencegah stoi melempar out_of_range
        if (!validasiHanyaAngka(inputJumlah) || inputJumlah.length() > 4) {
            cout << "[!] Error: Masukkan angka bulat positif maksimal 4 digit tanpa huruf/spasi!\n\n";
            jumlahMhs = 0;
            continue;
        }

        jumlahMhs = stoi(inputJumlah);
        if (jumlahMhs < 1 || jumlahMhs > MAKS_MHS) {
            cout << "[!] Error: Jumlah mahasiswa harus antara 1 dan " << MAKS_MHS << "!\n\n";
        }
    } while (jumlahMhs < 1 || jumlahMhs > MAKS_MHS);

    // 2. Deklarasi Array 1D menyesuaikan jumlah yang diinput di terminal
    string* nim    = new string[jumlahMhs];
    string* nama   = new string[jumlahMhs];
    string* prodi  = new string[jumlahMhs];
    string* alamat = new string[jumlahMhs];

    // 3. Input data mahasiswa di terminal
    cout << "\n=== INPUT DATA MAHASISWA ===\n";
    for (int i = 0; i < jumlahMhs; i++) {
        cout << "\nData Mahasiswa ke-" << (i + 1) << " (Indeks [" << i << "]):\n";

        // Validasi NIM wajib angka saja
        do {
            cout << "NIM    : ";
            if (!getline(cin, nim[i])) return 1; // input terputus (EOF)
            if (!validasiHanyaAngka(nim[i])) {
                cout << "[!] Error: NIM hanya boleh berisi angka (0-9) tanpa huruf!\n";
            }
        } while (!validasiHanyaAngka(nim[i]));

        cout << "Nama   : ";
        getline(cin, nama[i]);

        cout << "Prodi  : ";
        getline(cin, prodi[i]);

        cout << "Alamat : ";
        getline(cin, alamat[i]);
    }

    // 4. Menampilkan hasil dalam bentuk tabel rapi
    cout << "\n=================================================================================\n";
    cout << "                            HASIL PENDATAAN MAHASISWA                            \n";
    cout << "=================================================================================\n";
    cout << left << setw(4)  << "No"
         << setw(14) << "NIM"
         << setw(24) << "Nama"
         << setw(28) << "Prodi"
         << "Alamat\n";
    cout << "---------------------------------------------------------------------------------\n";

    for (int i = 0; i < jumlahMhs; i++) {
        cout << left << setw(4)  << (i + 1)
             << setw(14) << nim[i]
             << setw(24) << nama[i]
             << setw(28) << prodi[i]
             << alamat[i] << "\n";
    }
    cout << "=================================================================================\n";

    // 5. Output sesuai format pemanggilan indeks nim[i] << nama[i] << prodi[i] << alamat[i]
    cout << "\n=== OUTPUT PEMANGGILAN LANGSUNG PER INDEKS ===\n";
    for (int i = 0; i < jumlahMhs; i++) {
        cout << "Indeks [" << i << "] -> "
             << nim[i] << " | " << nama[i] << " | " << prodi[i] << " | " << alamat[i] << "\n";
    }

    // Membersihkan memori dinamis setelah selesai digunakan
    delete[] nim;
    delete[] nama;
    delete[] prodi;
    delete[] alamat;

    return 0;
}
