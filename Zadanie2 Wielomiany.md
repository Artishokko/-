

#include <iostream>
using namespace std;
int main()
{
	// zadanie 2
	int Stepien, summa, A;
	A = 1;
	summa = 0;
	cout << "Podaj N" << endl;
	cin >> Stepien;
	for (int i = 0; i <= Stepien; i++) {
		for (int j = 0; j < i; j++) {
			A = A * 2;
		}
		summa += A;
		A = 1;
	}
	cout << "Ten wielomian sie rowna = " << summa;
  
}

