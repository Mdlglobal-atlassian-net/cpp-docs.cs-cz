---
title: komplexní&lt;double&gt;
ms.date: 11/04/2016
f1_keywords:
- complex/std::complex<double>
helpviewer_keywords:
- complex<double> function
ms.assetid: 0d0b9d2a-9b9b-410b-82a0-86b6df127e47
ms.openlocfilehash: 7cb516363df7267c2870d2188a14208f54f7ffe9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62148403"
---
# <a name="complexltdoublegt"></a>komplexní&lt;double&gt;

Popisuje objekt, který ukládá seřazená dvojice objektů typu **double**, nejprve představující skutečný součástí komplexní čísla a druhý představující imaginární části.

## <a name="syntax"></a>Syntaxe

```cpp
template <>
class complex<double> {
public:
    constexpr complex(
    double RealVal = 0,
    double ImagVal = 0);

constexpr complex(const complex<double>& complexNum);

constexpr explicit complex(const complex<long double>& complexNum);
// rest same as template class complex
};
```

### <a name="parameters"></a>Parametry

*RealVal*<br/>
Hodnota typu **double** pro skutečné součástí komplexní čísla při konstrukci.

*ImagVal*<br/>
Hodnota typu **double** imaginární části komplexního čísla při konstrukci.

*complexNum*<br/>
Komplexní čísla typu **float** nebo typu **long double** jehož reálné a imaginární části se používají k inicializaci komplexního čísla typu **double** vytváří.

## <a name="return-value"></a>Návratová hodnota

Komplexní čísla typu **double**.

## <a name="remarks"></a>Poznámky

Explicitní specializace šablony třídy komplexní complex – třída typu **double** se liší od třídy šablony pouze v konstruktorech definuje. Převod z **float** k **double** může být implicitní, ale převod z **long double** k **double** musí být **explicitní**. Použití **explicitní** Vylučuje zahájení s převod typu pomocí syntaxe přiřazení.

Další informace o šablony třídy `complex`, naleznete v tématu [complex – třída](../standard-library/complex-class.md). Pro seznam členů třídy šablony `complex`, naleznete v tématu.

## <a name="example"></a>Příklad

```cpp
// complex_comp_dbl.cpp
// compile with: /EHsc
#include <complex>
#include <iostream>

int main( )
{
   using namespace std;
   double pi = 3.14159265359;

   // The first constructor specifies real & imaginary parts
   complex <double> c1 ( 4.0 , 5.0 );
   cout << "Specifying initial real & imaginary parts,\n"
        << "as type double gives c1 = " << c1 << endl;

   // The second constructor initializes values of the real &
   // imaginary parts using those of complex number of type float
   complex <float> c2float ( 4.0 , 5.0 );
   complex <double> c2double ( c2float );
   cout << "Implicit conversion from type float to type double,"
        << endl << "gives c2double = " << c2double << endl;

   // The third constructor initializes values of the real &
   // imaginary parts using those of a complex number
   // of type long double
   complex <long double> c3longdouble ( 4.0 , 5.0 );
   complex <double> c3double ( c3longdouble );
   cout << "Explicit conversion from type float to type double,"
        << endl << "gives c3longdouble = " << c3longdouble << endl;

   // The modulus and argument of a complex number can be recovered
   double absc3 = abs ( c3longdouble );
   double argc3 = arg ( c3longdouble );
   cout << "The modulus of c3 is recovered from c3 using: abs ( c3 ) = "
        << absc3 << endl;
   cout << "Argument of c3 is recovered from c3 using:" << endl
        << "arg ( c3 ) = " << argc3 << " radians, which is "
        << argc3 * 180 / pi << " degrees." << endl;
}
/* Output:
Specifying initial real & imaginary parts,
as type double gives c1 = (4,5)
Implicit conversion from type float to type double,
gives c2double = (4,5)
Explicit conversion from type float to type double,
gives c3longdouble = (4,5)
The modulus of c3 is recovered from c3 using: abs ( c3 ) = 6.40312
Argument of c3 is recovered from c3 using:
arg ( c3 ) = 0.896055 radians, which is 51.3402 degrees.
*/
```

## <a name="requirements"></a>Požadavky

**Hlavička**: \<komplexní >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[complex – třída](../standard-library/complex-class.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
