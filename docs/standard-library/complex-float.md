---
title: komplexní&lt;float&gt; | Microsoft Docs
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
ms.openlocfilehash: 278a9e33fb305b73c2919c455f55b816de644e4b
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33843389"
---
# <a name="complexltfloatgt"></a>komplexní&lt;float&gt;

Popisuje objekt, který ukládá dvojici seřazené objektů typu **float **** první představující skutečné část reprezentující komplexní čísla a druhý představující pomyslná část.

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

`_RealVal` Hodnota typu **float** pro skutečné součástí komplexního čísla vytvářen.

`_ImagVal` Hodnota typu **float** pro pomyslná součástí komplexního čísla vytvářen.

`complexNum` Komplexní čísla typu **dvojité** nebo typu `long double` jejichž skutečné a pomyslná částí se používají k inicializaci komplexní čísla typu **float** vytvářen.

## <a name="return-value"></a>Návratová hodnota

Komplexní čísla typu **float**.

## <a name="remarks"></a>Poznámky

Explicitní specializace šablony třídy složitou complex – třída typu **float** se liší od třídy šablony pouze v konstruktorech definuje. Převod z **float** k **dvojité** může být implicitní, ale méně bezpečné převod **float** k `long double` musí být  **explicitní**. Použití **explicitní** pravidla na zahájení s pomocí syntaxe přiřazení převod typů.

Další informace o třídě šablony `complex`, najdete v části [complex – třída](../standard-library/complex-class.md). Pro seznam členů třídy šablony `complex`, najdete v článku.

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

**Záhlaví**: \<komplexní >

**Namespace:** – std

## <a name="see-also"></a>Viz také

[complex – třída](../standard-library/complex-class.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
