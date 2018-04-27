---
title: komplexní&lt;dvojité&gt; | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- complex/std::complex<double>
dev_langs:
- C++
helpviewer_keywords:
- complex<double> function
ms.assetid: 0d0b9d2a-9b9b-410b-82a0-86b6df127e47
caps.latest.revision: 23
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f17beb079b0b9e4f37cdf0ac2b3749e4ffc3790f
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="complexltdoublegt"></a>komplexní&lt;double&gt;

Popisuje objekt, který ukládá dvojici seřazené objektů typu **dvojitou **** první představující skutečné část reprezentující komplexní čísla a druhý představující pomyslná část.

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

`RealVal` Hodnota typu **dvojité** pro skutečné součástí komplexního čísla vytvářen.

`ImagVal` Hodnota typu **dvojité** pro pomyslná součástí komplexního čísla vytvářen.

`complexNum` Komplexní čísla typu **float** nebo typu `long double` jejichž skutečné a pomyslná částí se používají k inicializaci komplexní čísla typu **dvojité** vytvářen.

## <a name="return-value"></a>Návratová hodnota

Komplexní čísla typu **dvojité**.

## <a name="remarks"></a>Poznámky

Explicitní specializace šablony třídy složitou complex – třída typu **dvojité** se liší od třídy šablony pouze v konstruktorech definuje. Převod z **float** k **dvojité** může být implicitní, ale převod `long double` k **dvojité** musí být **explicitní** . Použití **explicitní** pravidla na zahájení s pomocí syntaxe přiřazení převod typů.

Další informace o třídě šablony `complex`, najdete v části [complex – třída](../standard-library/complex-class.md). Pro seznam členů třídy šablony `complex`, najdete v článku.

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
        << " as type double gives c1 = " << c1 << endl;

   // The second constructor initializes values of the real &
   // imaginary parts using those of complex number of type float
   complex <float> c2float ( 4.0 , 5.0 );
   complex <double> c2double ( c2float );
   cout << "Implicit conversion from type float to type double,"
        << "\n gives c2double = " << c2double << endl;

   // The third constructor initializes values of the real &
   // imaginary parts using those of a complex number
   // of type long double
   complex <long double> c3longdouble ( 4.0 , 5.0 );
   complex <double> c3double ( c3longdouble );
   cout << "Explicit conversion from type float to type double,"
        << "\n gives c3longdouble = " << c3longdouble << endl;

   // The modulus and argument of a complex number can be recovered
   double absc3 = abs ( c3longdouble );
   double argc3 = arg ( c3longdouble );
   cout << "The modulus of c3 is recovered from c3 using: abs ( c3 ) = "
        << absc3 << endl;
   cout << "Argument of c3 is recovered from c3 using:\n arg ( c3 ) = "
        << argc3 << " radians, which is " << argc3 * 180 / pi
        << " degrees." << endl;
}
\* Output:
Specifying initial real & imaginary parts,
 as type double gives c1 = (4,5)
Implicit conversion from type float to type double,
 gives c2double = (4,5)
Explicit conversion from type float to type double,
 gives c3longdouble = (4,5)
The modulus of c3 is recovered from c3 using: abs ( c3 ) = 6.40312
Argument of c3 is recovered from c3 using:
 arg ( c3 ) = 0.896055 radians, which is 51.3402 degrees.
*\
```

## <a name="requirements"></a>Požadavky

**Záhlaví**: \<komplexní >

**Namespace:** – std

## <a name="see-also"></a>Viz také

[complex – třída](../standard-library/complex-class.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
