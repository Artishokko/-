#include <iostream>

using namespace std;

int main()
{
    int potenga;
    cout << "Input Potega" << endl;
    cin >> potenga;
    cout << "Najwieksza mnozen" << (potenga * (potenga + 1)) / 2 << "Sum: " << potenga<< endl;
    cout << "Najmniej mnozen: " << potenga  << "Sum: " << potenga << endl;

    return 0;
}
