# Лабораторна робота №1 (Варіант 9)
Студент: Кріль М. Б.  
Група: ІСТ-21/1  

---

## Завдання 1 (Варіант 9)

```cpp
#include <iostream>
#include <cmath>
#include <iomanip>
#include <windows.h>

using namespace std;

class ZavdClass 
{
private:
    double a, b;

public:
    ZavdClass() : a(0.0), b(0.0) {}

    void Fn_b(double x, double y, double z) 
    {
        double term1 = pow(fabs(x), 0.3) / (z + y);
        double arg_tan = (x + z * z) / (2.0 * x - 1.4);
        double term2 = pow(tan(arg_tan), 2.0);
        double inside_abs = fabs(term1 + term2);
        double cube_root = pow(inside_abs, 1.0 / 3.0);

        b = y * cube_root - z * exp(x * x - y);
    }

    void Fn_a(double x, double y, double z) 
    {
        double a_mult = pow(fabs(x), 0.2);
        double num_e = exp(y - x);
        double num_sqrt = pow(sqrt(fabs(y * y + b)), 0.3);
        double num = 3.0 + num_e + num_sqrt;

        double den_tan = pow(tan(z * z), 2.0);
        double den_abs = fabs(y - den_tan);
        double den = 1.0 + (x * x) * den_abs;

        a = a_mult * (num / den);
    }

    double geta() const { return a; }
    double getb() const { return b; }
};

int main() 
{
    SetConsoleOutputCP(1251);
    SetConsoleCP(1251);

    const int N = 9;
    double x = 0.48 * N;   // 4.32
    double y = 0.47 * N;   // 4.23
    double z = -1.32 * N;  // -11.88

    ZavdClass zavd;
    zavd.Fn_b(x, y, z);
    zavd.Fn_a(x, y, z);

    cout << fixed << setprecision(4);
    cout << "Завдання 1 (Варіант 9):" << endl;
    cout << "b = " << zavd.getb() << endl;
    cout << "a = " << zavd.geta() << endl;

    return 0;
}
