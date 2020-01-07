---
title: složitá&lt;dlouhá dvojitá&gt;
ms.date: 11/04/2016
f1_keywords:
- std::complex<long double>
- complex<long double>
- std.complex<long double>
helpviewer_keywords:
- complex<long double> function
ms.assetid: 37591991-b385-46e9-b727-d534dbc10432
ms.openlocfilehash: 5de4fc2305ef2ac6e523dcb02782455245b99429
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/20/2019
ms.locfileid: "75302338"
---
# <a name="complexltlong-doublegt"></a>složitá&lt;dlouhá dvojitá&gt;

Tato explicitně specializovaná šablona třídy popisuje objekt, který ukládá seřazený pár objektů, jak typu **Long Double**, tak první představuje skutečnou část komplexního čísla a druhý představující imaginární část.

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

// rest same as class template complex
};
```

### <a name="parameters"></a>Parametry

*_RealVal*\
Hodnota typu **Long Double** pro skutečnou část složeného čísla konstrukce

*_ImagVal*\
Hodnota typu **Long Double** pro imaginární část složeného čísla, která je konstruována.

*complexNum*\
Komplexní číslo typu **Double** nebo typu **float** , jehož reálné a imaginární části jsou použity k inicializaci komplexního typu **dlouhého dvojnásobku** typu.

## <a name="return-value"></a>Návratová hodnota

Komplexní číslo typu **Long Double**.

## <a name="remarks"></a>Poznámky

Explicitní specializace šablony třídy `complex` komplexní třídy typu **Long Double** se liší od šablony třídy pouze v konstruktorech, které definuje. Převod z typu **Long Double na typ** **float** je povolen na implicitní, ale převod z **Double** na **Long Double** musí být **explicitní**. Použití **explicitních** pravidel je vycházející z inicializace s převodem typu pomocí syntaxe přiřazení.

Další informace o šabloně třídy `complex` a jejích členech naleznete v tématu [Complex Class](../standard-library/complex-class.md).

**Specifické pro společnost Microsoft**: **dlouhé typy Double** a **Double** mají stejnou reprezentaci, ale jsou odlišné typy. Další informace najdete v tématu [předdefinované typy](../cpp/fundamental-types-cpp.md).

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

**Záhlaví**: \<složitých >

**Obor názvů:** std

## <a name="see-also"></a>Viz také:

[komplexní\ třídy](../standard-library/complex-class.md)
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
