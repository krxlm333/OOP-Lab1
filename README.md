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
```
```
==========================================
   РЕЗУЛЬТАТИ ОБЧИСЛЕНЬ (ЗАВДАННЯ 1)      
==========================================
b = 22015486.6719
a = 0.2811
==========================================
```

## Завдання 2 (Варіант 9)

```cpp
#include <iostream>
#include <cmath>
#include <iomanip>
#include <windows.h>

using namespace std;

class TabulationClass 
{
private:
    double y, z;

public:
    TabulationClass(double init_y, double init_z) : y(init_y), z(init_z) {}

    double calc_b(double x) const 
    {
        double term1 = pow(fabs(x), 0.3) / (z + y);
        double arg_tan = (x + z * z) / (2.0 * x - 1.4);
        double term2 = pow(tan(arg_tan), 2.0);
        double inside_abs = fabs(term1 + term2);
        double cube_root = pow(inside_abs, 1.0 / 3.0);

        return y * cube_root - z * exp(x * x - y);
    }

    double calc_a(double x, double b) const 
    {
        double a_mult = pow(fabs(x), 0.2);
        double num_e = exp(y - x);
        double num_sqrt = pow(sqrt(fabs(y * y + b)), 0.3);
        double num = 3.0 + num_e + num_sqrt;

        double den_tan = pow(tan(z * z), 2.0);
        double den_abs = fabs(y - den_tan);
        double den = 1.0 + (x * x) * den_abs;

        return a_mult * (num / den);
    }

    void tabulate(double x_start, double x_end, double dx) const 
    {
        cout << fixed << setprecision(4);
        cout << "   x      |        b         |        a" << endl;
        cout << "----------+------------------+------------------" << endl;

        for (double x = x_start; x <= x_end + 1e-9; x += dx) 
        {
            if (fabs(x) < 1e-9) x = 0.0;
            double b_val = calc_b(x);
            double a_val = calc_a(x, b_val);

            cout << setw(8) << x << "  |  " 
                 << setw(14) << b_val << "  |  " 
                 << setw(14) << a_val << endl;
        }
    }
};

int main() 
{
    SetConsoleOutputCP(1251);
    SetConsoleCP(1251);

    const int N = 9;
    double y = 0.47 * N;   // 4.23
    double z = -1.32 * N;  // -11.88

    TabulationClass tabulator(y, z);
    cout << "Завдання 2 (Табулювання):" << endl;
    tabulator.tabulate(-1.0, 1.0, 0.2);

    return 0;
}
```
```
=====================================================
   ТАБЛИЦЯ ТАБУЛЮВАННЯ ФУНКЦІЙ a(x) ТА b(x)         
=====================================================
   x      |        b(x)        |        a(x)         
----------+--------------------+---------------------
 -1.0000  |            1.6984  |           37.0017
 -0.8000  |            1.1562  |           41.0420
 -0.6000  |            3.4964  |           46.8427
 -0.4000  |            7.2346  |           53.4929
 -0.2000  |            1.3135  |           54.9639
  0.0000  |            2.0126  |            0.0000
  0.2000  |            1.9970  |           37.7818
  0.4000  |            1.3878  |           25.2752
  0.6000  |           10.9466  |           15.2908
  0.8000  |            1.1174  |            9.2337
  1.0000  |            9.6886  |            5.7864
=====================================================
```

Висновки
В ході виконання лабораторної роботи було створено програму C++ з використанням об'єктно-орієнтованого підходу (класів) для обчислення складних математичних виразів за Варіантом №9, а також виконано одновимірне табулювання функцій a і b
