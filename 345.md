#include <iostream>
#include <vector>
#include <cstdlib>
#include <ctime>
#include <cmath>

using namespace std;

// Funkcja Hornera
double horner(const vector<double>& a, double x) {
    double wynik = a[0];
    for (int i = 1; i < a.size(); i++)
        wynik = wynik * x + a[i];
    return wynik;
}

// Funkcja do szukania pierwiastków wymiernych
void szukajPierwiastkow(const vector<int>& a) {
    int an = a[0];          // współczynnik wiodący
    int a0 = a.back();      // wyraz wolny

    cout << "Mozliwe pierwiastki wymierne to: ±(dzielniki a0 / dzielniki an)\n";

    for (int p = -abs(a0); p <= abs(a0); p++) {
        if (p == 0) continue;
        if (a0 % abs(p) == 0) {
            for (int q = 1; q <= abs(an); q++) {
                if (an % q == 0) {
                    double r = (double)p / q;
                    if (abs(horner(vector<double>(a.begin(), a.end()), r)) < 1e-6) {
                        cout << "Znaleziony pierwiastek: " << r << "\n";
                    }
                }
            }
        }
    }
}

// Ekstrema dla trinom polinomu stopnia 3
void ekstrema3(double a, double b, double c, double d) {
    // w(x) = ax^3 + bx^2 + cx + d
    // w'(x) = 3ax^2 + 2bx + c
    double A = 3 * a;
    double B = 2 * b;
    double C = c;

    double delta = BB - 4AC;

    if (delta < 0) {
        cout << "Brak ekstremow.\n";
        return;
    }

    double x1 = (-B - sqrt(delta)) / (2A);
    double x2 = (-B + sqrt(delta)) / (2A);

    cout << "Ekstrema:\n";
    cout << "x1 = " << x1 << ", w(x1) = " << (ax1x1x1 + bx1x1 + cx1 + d) << "\n";
    cout << "x2 = " << x2 << ", w(x2) = " << (ax2x2x2 + bx2x2 + c*x2 + d) << "\n";
}
int main() {
    srand(time(0));

    // Losujemy stopien
    int n = rand() % 5 + 3; // od 3 do 7
    cout << "Losowy stopien wielomianu: " << n << "\n";

    // Losujemy współczynniki
    vector<double> a(n + 1);
    vector<int> a_int(n + 1);

    cout << "Wspolczynniki: ";
    for (int i = 0; i <= n; i++) {
        a[i] = rand() % 11 - 5;     // od -5 do 5
        a_int[i] = (int)a[i];
        cout << a[i] << " ";
    }
    cout << "\n";

    // Wybieramy losowe a do Hornera
    double x0 = rand() % 10 - 5;
    cout << "Dzielimy przez (x - " << x0 << ")\n";

    double reszta = horner(a, x0);
    cout << "Reszta z dzielenia = " << reszta << "\n";

    // Szukamy pierwiastków wymiernych
    cout << "\n--- Szukanie pierwiastkow wymiernych ---\n";
    szukajPierwiastkow(a_int);

    // Ekstrema tylko jeśli stopień = 3
    if (n == 3) {
        cout << "\n--- Ekstrema dla stopnia 3 ---\n";
        ekstrema3(a[0], a[1], a[2], a[3]);
    }

    // Dane do wykresu
    cout << "\n--- Punkty do wykresu (x, w(x)) ---\n";
    for (double x = -5; x <= 5; x += 0.5) {
        cout << x << " " << horner(a, x) << "\n";
    }

    return 0;
}
