---
title: komplexní&lt;long double&gt;
ms.date: 11/04/2016
f1_keywords:
- std::complex<long double>
- complex<long double>
- std.complex<long double>
helpviewer_keywords:
- complex<long double> function
ms.assetid: 37591991-b385-46e9-b727-d534dbc10432
ms.openlocfilehash: 19d4569523879911209bf0c05e762eba2c9852a1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62389163"
---
# <a name="complexltlong-doublegt"></a>komplexní&lt;long double&gt;

Tato třída explicitně specializovaný šablony popisuje objekt, který ukládá seřazená dvojice objektů, oba typu **long double**, nejprve představující skutečný součástí komplexní čísla a druhý představující imaginární části.

## <a name="syntax"></a>Syntaxe

```cpp
template <>
class complex<long double> {
public:
    constexpr complex(
    long double _RealVal = 0,
    long double _ImagVal = 0);

complex(
    constexpr complex<long double>& complexNum);

// rest same as template class complex
};
```

### <a name="parameters"></a>Parametry

*_RealVal*<br/>
Hodnota typu **long double** pro skutečné součástí komplexní čísla při konstrukci.

*_ImagVal*<br/>
Hodnota typu **long double** imaginární části komplexního čísla při konstrukci.

*complexNum*<br/>
Komplexní čísla typu **double** nebo typu **float** jehož reálné a imaginární části se používají k inicializaci komplexního čísla typu **long double** vytváří.

## <a name="return-value"></a>Návratová hodnota

Komplexní čísla typu **long double**.

## <a name="remarks"></a>Poznámky

Explicitní specializace šablony třídy `complex` komplexní třídy typu **long double** se liší od třídy šablony pouze v konstruktorech definuje. Převod z **long double** k **float** může být implicitní, ale převod z **double** k **long double** je povinný Chcete-li být **explicitní**. Použití **explicitní** Vylučuje zahájení s převod typu pomocí syntaxe přiřazení.

Další informace o šablony třídy `complex` a zobrazit jeho členové [complex – třída](../standard-library/complex-class.md).

**Specifické pro Microsoft**: **Long double** a **double** typy mají stejnou reprezentaci, ale jsou různé typy. Další informace najdete v tématu [základní typy](../cpp/fundamental-types-cpp.md).

## <a name="example"></a>Příklad

```cpp
// complex_comp_ld.cpp
// compile with: /EHsc
#include <complex>
#include <iostream>

int main( )
{
    using namespace std;
    double pi = 3.14159265359;

    // The first constructor specifies real & imaginary parts
    complex<long double> c1( 4.0 , 5.0 );
    cout << "Specifying initial real & imaginary parts,\n"
        << " as type float gives c1 = " << c1 << endl;

    // The second constructor initializes values of the real &
    // imaginary parts using those of complex number of type float
    complex<float> c2float( 1.0 , 3.0 );
    complex<long double> c2longdouble ( c2float );
    cout << "Implicit conversion from type float to type long double,"
        << "\n gives c2longdouble = " << c2longdouble << endl;

    // The third constructor initializes values of the real &
    // imaginary parts using those of a complex number
    // of type double
    complex<double> c3double( 3.0 , 4.0 );
    complex<long double> c3longdouble( c3double );
    cout << "Implicit conversion from type long double to type float,"
        << "\n gives c3longdouble = " << c3longdouble << endl;

    // The modulus and argument of a complex number can be recovered
    double absc3 = abs( c3longdouble );
    double argc3 = arg( c3longdouble );
    cout << "The modulus of c3 is recovered from c3 using: abs( c3 ) = "
        << absc3 << endl;
    cout << "Argument of c3 is recovered from c3 using:\n arg( c3 ) = "
        << argc3 << " radians, which is " << argc3 * 180 / pi
        << " degrees." << endl;
}
```

```Output
Specifying initial real & imaginary parts,
as type float gives c1 = (4,5)
Implicit conversion from type float to type long double,
gives c2longdouble = (1,3)
Implicit conversion from type long double to type float,
gives c3longdouble = (3,4)
The modulus of c3 is recovered from c3 using: abs( c3 ) = 5
Argument of c3 is recovered from c3 using:
arg( c3 ) = 0.927295 radians, which is 53.1301 degrees.
```

## <a name="requirements"></a>Požadavky

**Hlavička**: \<komplexní >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[complex – třída](../standard-library/complex-class.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
