---
title: komplexní&lt;float&gt; | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- complex/std::complex<float>
dev_langs:
- C++
helpviewer_keywords:
- complex<float> function
ms.assetid: 1178eb1e-39bd-4017-89cd-aea95f813939
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: af6d3ce3beca7d9bb3b14ee9c9373a8505623376
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38954002"
---
# <a name="complexltfloatgt"></a>komplexní&lt;plovoucí desetinnou čárkou&gt;

Popisuje objekt, který ukládá seřazená dvojice objektů typu **float **** nejprve představující skutečný součástí komplexní čísla a druhý představující imaginární části.

## <a name="syntax"></a>Syntaxe

```cpp
template <>
class complex<float> {
public:
    constexpr complex(
    float _RealVal = 0,
    float _ImagVal = 0);

constexpr complex(
    const complex<float>& complexNum);

constexpr complex(
    const complex<double>& complexNum);

constexpr complex(
    const complex<long double>& complexNum);
// rest same as template class complex
};
```

### <a name="parameters"></a>Parametry

*_RealVal* hodnotu typu **float** pro skutečné součástí komplexní čísla při konstrukci.

*_ImagVal* hodnotu typu **float** imaginární části komplexního čísla při konstrukci.

*complexNum* komplexního čísla typu **double** nebo typu **long double** jehož reálné a imaginární části se používají k inicializaci komplexního čísla typu **float**vytváří.

## <a name="return-value"></a>Návratová hodnota

Komplexní čísla typu **float**.

## <a name="remarks"></a>Poznámky

Explicitní specializace šablony třídy komplexní complex – třída typu **float** se liší od třídy šablony pouze v konstruktorech definuje. Převod z **float** k **double** může být implicitní, ale je méně bezpečný převod z **float** k **long double** je musí být **explicitní**. Použití **explicitní** Vylučuje zahájení s převod typu pomocí syntaxe přiřazení.

Další informace o šablony třídy `complex`, naleznete v tématu [complex – třída](../standard-library/complex-class.md). Pro seznam členů třídy šablony `complex`, naleznete v tématu.

## <a name="example"></a>Příklad

```cpp
// complex_comp_flt.cpp
// compile with: /EHsc
#include <complex>
#include <iostream>

int main( )
{
   using namespace std;
   double pi = 3.14159265359;

   // The first constructor specifies real & imaginary parts
   complex <float> c1 ( 4.0 , 5.0 );
   cout << "Specifying initial real & imaginary parts,\n"
        << " as type float gives c1 = " << c1 << endl;

   // The second constructor initializes values of the real &
   // imaginary parts using those of complex number of type double
   complex <double> c2double ( 1.0 , 3.0 );
   complex <float> c2float ( c2double );
   cout << "Implicit conversion from type double to type float,"
        << "\n gives c2float = " << c2float << endl;

   // The third constructor initializes values of the real &
   // imaginary parts using those of a complex number
   // of type long double
   complex <long double> c3longdouble ( 3.0 , 4.0 );
   complex <float> c3float ( c3longdouble );
   cout << "Explicit conversion from type long double to type float,"
        << "\n gives c3float = " << c3float << endl;

   // The modulus and argument of a complex number can be recovered
   double absc3 = abs ( c3float);
   double argc3 = arg ( c3float);
   cout << "The modulus of c3 is recovered from c3 using: abs ( c3 ) = "
        << absc3 << endl;
   cout << "Argument of c3 is recovered from c3 using:\n arg ( c3 ) = "
        << argc3 << " radians, which is " << argc3 * 180 / pi
        << " degrees." << endl;
}
\* Output:
Specifying initial real & imaginary parts,
 as type float gives c1 = (4,5)
Implicit conversion from type double to type float,
 gives c2float = (1,3)
Explicit conversion from type long double to type float,
 gives c3float = (3,4)
The modulus of c3 is recovered from c3 using: abs ( c3 ) = 5
Argument of c3 is recovered from c3 using:
 arg ( c3 ) = 0.927295 radians, which is 53.1301 degrees.
*\
```

## <a name="requirements"></a>Požadavky

**Hlavička**: \<komplexní >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[complex – třída](../standard-library/complex-class.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
