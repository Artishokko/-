#include <iostream>

using namespace std;

int main()
{
    int potenga;
    cout << "Input Potega" << endl;
    cin >> potenga;
    cout << "Najwieksza " << (potenga * (potenga - 1)) / 2<< endl;
    cout << "Najmniejsza" << potenga * 2 << endl;

    return 0;
}
