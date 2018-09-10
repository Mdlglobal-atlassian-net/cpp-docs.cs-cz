---
title: COMPLEX – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- complex/std::complex::value_type
- complex/std::complex::imag
- complex/std::complex::real
dev_langs:
- C++
helpviewer_keywords:
- std::complex [C++], value_type
- std::complex [C++], imag
- std::complex [C++], real
ms.assetid: d6492e1c-5eba-4bc5-835b-2a88001a5868
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: af4f0307823011e4c32ae6b08e18b4cef86e05db
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44103240"
---
# <a name="complex-class"></a>complex – třída

Třída šablony popisuje objekt, který ukládá dva objekty typu `Type`, jedna reprezentuje skutečný část komplexního čísla a ten, který představuje imaginární části.

## <a name="syntax"></a>Syntaxe

```

template <class
Type>
class complex
```

## <a name="remarks"></a>Poznámky

Objekt třídy `Type`:

- Nemá veřejný výchozí konstruktor, destruktor, kopírovací konstruktor a operátor přiřazení s konvenčním chování.

- Je možné přiřadit celé číslo nebo hodnoty s plovoucí desetinnou čárkou nebo zadejte přetypování na tyto hodnoty s konvenčním chování.

- Definuje aritmetické operátory a matematické funkce, podle potřeby, které jsou definovány pro typy s plovoucí desetinnou čárkou s konvenčním chování.

Konkrétně se žádné lišila mohou existovat mezi konstrukci kopie a výchozí konstrukce, za nímž následuje přiřazení. Žádná z operací u objektů třídy `Type` může vyvolat výjimky.

Explicitní specializace šablony třídy komplexní existují tři typy s plovoucí desetinnou čárkou. V této implementaci hodnoty libovolného typu `Type` přetypovat na **double** pro skutečné výpočty s **double** výsledek zpětně přiřazena poté uložený objekt typu `Type``.`

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[complex](#complex)|Sestaví komplexního čísla se zadaným reálné a imaginární části nebo jako kopii některé komplexního čísla.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[value_type](#value_type)|Typ, který představuje datový typ používá k reprezentování reálné a imaginární části komplexního čísla.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[imag](#imag)|Extrahuje imaginární komplexního čísla.|
|[Real](#real)|Extrahuje reálnou součástí komplexního čísla.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[Operator * =](#op_star_eq)|Vynásobí číslo cílového komplexní faktoru, který může být komplexní nebo stejného typu jako reálné a imaginární části komplexních číslo.|
|[operator+=](#op_add_eq)|Přidá číslo cílového komplexního čísla, kde počet přidaných může být složitý nebo stejného typu, jako jsou reálné a imaginární části komplexní čísla, ke kterému je přidání.|
|[operátor-=](#operator-_eq)|Odečte číslo z cílové komplexního čísla, kde číslo odečtena může být složitý nebo stejného typu jako jsou reálné a imaginární části komplexní čísla, ke kterému je přidání.|
|[/ = – operátor](#op_div_eq)|Vydělí cílové komplexního čísla dělitelem, která může být komplexní nebo být stejného typu, jako jsou reálné a imaginární části komplexních číslo.|
|[operátor =](#op_eq)|Přiřadí číslo cílového komplexního čísla, kde může být složitý číslo přiřazené nebo stejného typu, jako jsou reálné a imaginární části komplexní čísla, ke kterému je přiřazen.|

## <a name="requirements"></a>Požadavky

**Hlavička**: \<komplexní >

**Namespace:** std

## <a name="complex"></a>  COMPLEX::Complex

Sestaví komplexního čísla se zadaným reálné a imaginární části nebo jako kopii některé komplexního čísla.

```cpp
constexpr complex(
    const T&
    _RealVal = 0  ,
    const T&
    _ImagVal = 0);

    template <class Other>
constexpr complex(
    const complex<Other>&
    complexNum);
```

### <a name="parameters"></a>Parametry

*_RealVal*<br/>
Hodnota části skutečné použitý k inicializaci komplexního čísla při konstrukci.

*_ImagVal*<br/>
Hodnota imaginární části použitý k inicializaci komplexního čísla při konstrukci.

*complexNum*<br/>
Komplexní čísla, jejichž reálné a imaginární části se používají k inicializaci komplexního čísla při konstrukci.

### <a name="remarks"></a>Poznámky

První konstruktor inicializuje uložený reálné část k _ *RealVal* a imaginární části uložené na \_ *Imagval*. Druhý konstruktor inicializuje uložený na skutečném část `complexNum` **.real**() a imaginární části uložené na `complexNum` **.imag**().

V této implementaci, pokud převaděč nepodporuje šablony členské funkce, šablony:

```cpp
template <class Other>
complex(const complex<Other>& right);
```

nahradí:

```

complex(const complex& right);
```

což je kopírovací konstruktor.

### <a name="example"></a>Příklad

```cpp
// complex_complex.cpp
// compile with: /EHsc
#include <complex>
#include <iostream>

int main( )
{
   using namespace std;
   double pi = 3.14159265359;

   // The first constructor specifies real & imaginary parts
   complex <double> c1 ( 4.0 , 5.0 );
   cout << "Specifying initial real & imaginary parts,"
        << "c1 = " << c1 << endl;

   // The second constructor initializes values of the real &
   // imaginary parts using those of another complex number
   complex <double> c2 ( c1 );
   cout << "Initializing with the real and imaginary parts of c1,"
        << " c2 = " << c2 << endl;

   // Complex numbers can be initialized in polar form
   // but will be stored in Cartesian form
   complex <double> c3 ( polar ( sqrt( (double)8 ) , pi / 4 ) );
   cout << "c3 = polar ( sqrt ( 8 ) , pi / 4 ) = " << c3 << endl;

   // The modulus and argument of a complex number can be recovered
   double absc3 = abs ( c3 );
   double argc3 = arg ( c3 );
   cout << "The modulus of c3 is recovered from c3 using: abs ( c3 ) = "
        << absc3 << endl;
   cout << "Argument of c3 is recovered from c3 using:\n arg ( c3 ) = "
        << argc3 << " radians, which is " << argc3 * 180 / pi
        << " degrees." << endl;
}
```

## <a name="imag"></a>  COMPLEX::Imag

Extrahuje imaginární komplexního čísla.

```cpp
T imag() const;


T imag(const T& right);
```

### <a name="parameters"></a>Parametry

*doprava*<br/>
Komplexní čísla, jehož imaginární hodnota má být extrahován.

### <a name="return-value"></a>Návratová hodnota

Imaginární části komplexního čísla.

### <a name="remarks"></a>Poznámky

Pro komplexní čísla *+ bi*, imaginární části nebo komponenty je *Im(a + bi) = b.*

### <a name="example"></a>Příklad

```cpp
// complex_imag.cpp
// compile with: /EHsc
#include <complex>
#include <iostream>

int main( )
{
   using namespace std;

   complex <double> c1 ( 4.0 , 3.0 );
   cout << "The complex number c1 = " << c1 << endl;

   double dr1 = c1.real ( );
   cout << "The real part of c1 is c1.real ( ) = "
        << dr1 << "." << endl;

   double di1 = c1.imag ( );
   cout << "The imaginary part of c1 is c1.imag ( ) = "
        << di1 << "." << endl;
}
```

```Output
The complex number c1 = (4,3)
The real part of c1 is c1.real ( ) = 4.
The imaginary part of c1 is c1.imag ( ) = 3.
```

## <a name="op_star_eq"></a>  COMPLEX::Operator * =

Vynásobí číslo cílového komplexní faktoru, který může být komplexní nebo stejného typu jako reálné a imaginární části komplexních číslo.

```cpp
template <class Other>
complex& operator*=(const complex<Other>& right);

complex<Type>& operator*=(const Type& right);

complex<Type>& operator*=(const complex<Type>& right);
```

### <a name="parameters"></a>Parametry

*doprava*<br/>
Komplexní čísla nebo číslo, které je stejného typu jako parametr komplexního čísla cíl.

### <a name="return-value"></a>Návratová hodnota

Komplexní čísla, která byla vynásobí číslo zadané jako parametr.

### <a name="remarks"></a>Poznámky

Operace je přetížena tak, aby jednoduché aritmetické operace se můžou provádět bez převodu dat na konkrétní formát.

### <a name="example"></a>Příklad

```cpp
// complex_op_me.cpp
// compile with: /EHsc
#include <complex>
#include <iostream>

int main() {
   using namespace std;
   double pi = 3.14159265359;

   // Example of the first member function
   // type complex<double> multiplied by type complex<double>
   complex <double> cl1 ( polar ( 3.0 , pi / 6 ) );
   complex <double> cr1 ( polar ( 2.0 , pi / 3 ) );
   cout << "The left-side complex number is cl1 = " << cl1 << endl;
   cout << "The right-side complex number is cr1 = " << cr1 << endl;

   complex <double> cs1 = cl1 * cr1;
   cout << "Quotient of two complex numbers is: cs1 = cl1 * cr1 = "
        << cs1 << endl;

   // This is equivalent to the following operation
   cl1 *= cr1;
   cout << "Quotient of two complex numbers is also: cl1 *= cr1 = "
        << cl1 << endl;

   double abscl1 = abs ( cl1 );
   double argcl1 = arg ( cl1 );
   cout << "The modulus of cl1 is: " << abscl1 << endl;
   cout << "The argument of cl1 is: "<< argcl1 << " radians, which is "
        << argcl1 * 180 / pi << " degrees." << endl << endl;

   // Example of the second member function
   // type complex<double> multiplied by type double
   complex <double> cl2 ( polar ( 3.0 , pi / 6 ) );
   double cr2 = 5.0;
   cout << "The left-side complex number is cl2 = " << cl2 << endl;
   cout << "The right-side complex number is cr2 = " << cr2 << endl;

   complex <double> cs2 = cl2 * cr2;
   cout << "Quotient of two complex numbers is: cs2 = cl2 * cr2 = "
        << cs2 << endl;

   // This is equivalent to the following operation
   cl2 *= cr2;
   cout << "Quotient of two complex numbers is also: cl2 *= cr2 = "
        << cl2 << endl;

   double abscl2 = abs ( cl2 );
   double argcl2 = arg ( cl2 );
   cout << "The modulus of cl2 is: " << abscl2 << endl;
   cout << "The argument of cl2 is: "<< argcl2 << " radians, which is "
        << argcl2 * 180 / pi << " degrees." << endl;
}
```

## <a name="op_add_eq"></a>  COMPLEX::Operator +=

Přidá číslo cílového komplexního čísla, kde počet přidaných může být složitý nebo stejného typu, jako jsou reálné a imaginární části komplexní čísla, ke kterému je přidání.

```cpp
template <class Other>
complex<Type>& operator+=(const complex<Other>& right);

complex<Type>& operator+=(const Type& right);

complex<Type>& operator+=(const complex<Type>& right);
```

### <a name="parameters"></a>Parametry

*doprava*<br/>
Komplexní čísla nebo číslo, které je stejného typu jako parametr komplexního čísla cíl.

### <a name="return-value"></a>Návratová hodnota

Komplexní čísla, který byl zadán jako parametr přidá číslo.

### <a name="remarks"></a>Poznámky

Operace je přetížena tak, aby jednoduché aritmetické operace se můžou provádět bez převodu dat na konkrétní formát.

### <a name="example"></a>Příklad

```cpp
// complex_op_pe.cpp
// compile with: /EHsc
#include <complex>
#include <iostream>

int main( )
{
   using namespace std;
   double pi = 3.14159265359;

   // Example of the first member function
   // type complex<double> added to type complex<double>
   complex <double> cl1 ( 3.0 , 4.0 );
   complex <double> cr1 ( 2.0 , -1.0 );
   cout << "The left-side complex number is cl1 = " << cl1 << endl;
   cout << "The right-side complex number is cr1 = " << cr1 << endl;

   complex <double> cs1 = cl1 + cr1;
   cout << "The sum of the two complex numbers is: cs1 = cl1 + cr1 = "
        << cs1 << endl;

   // This is equivalent to the following operation
   cl1 += cr1;
   cout << "The complex number cr1 added to the complex number cl1 is:"
        << "\n cl1 += cr1 = " << cl1 << endl;

   double abscl1 = abs ( cl1 );
   double argcl1 = arg ( cl1 );
   cout << "The modulus of cl1 is: " << abscl1 << endl;
   cout << "The argument of cl1 is: "<< argcl1 << " radians, which is "
        << argcl1 * 180 / pi << " degrees." << endl << endl;

   // Example of the second member function
   // type double added to type complex<double>
   complex <double> cl2 ( -2 , 4 );
   double cr2 =5.0;
   cout << "The left-side complex number is cl2 = " << cl2 << endl;
   cout << "The right-side complex number is cr2 = " << cr2 << endl;

   complex <double> cs2 = cl2 + cr2;
   cout << "The sum of the two complex numbers is: cs2 = cl2 + cr2 = "
        << cs2 << endl;

   // This is equivalent to the following operation
   cl2 += cr2;
   cout << "The complex number cr2 added to the complex number cl2 is:"
        << "\n cl2 += cr2 = " << cl2 << endl;

   double abscl2 = abs ( cl2 );
   double argcl2 = arg ( cl2 );
   cout << "The modulus of cl2 is: " << abscl2 << endl;
   cout << "The argument of cl2 is: "<< argcl2 << " radians, which is "
        << argcl2 * 180 / pi << " degrees." << endl << endl;
}
```

```Output
The left-side complex number is cl1 = (3,4)
The right-side complex number is cr1 = (2,-1)
The sum of the two complex numbers is: cs1 = cl1 + cr1 = (5,3)
The complex number cr1 added to the complex number cl1 is:
cl1 += cr1 = (5,3)
The modulus of cl1 is: 5.83095
The argument of cl1 is: 0.54042 radians, which is 30.9638 degrees.

The left-side complex number is cl2 = (-2,4)
The right-side complex number is cr2 = 5
The sum of the two complex numbers is: cs2 = cl2 + cr2 = (3,4)
The complex number cr2 added to the complex number cl2 is:
cl2 += cr2 = (3,4)
The modulus of cl2 is: 5
The argument of cl2 is: 0.927295 radians, which is 53.1301 degrees.
```

## <a name="complex__operator-_eq"></a>  COMPLEX::Operator-=

Odečte číslo z cílové komplexního čísla, kde číslo odečtena může být složitý nebo stejného typu jako jsou reálné a imaginární části komplexní čísla, ke kterému je přidání.

```cpp
template <class Other>
complex<Type>& operator-=(const complex<Other>& complexNum);

complex<Type>& operator-=(const Type& _RealPart);

complex<Type>& operator-=(const complex<Type>& complexNum);
```

### <a name="parameters"></a>Parametry

*complexNum*<br/>
Komplexní čísla se odečítají z cílové komplexního čísla.

*_RealPart*<br/>
Reálné číslo bude odečítat od cílové komplexního čísla.

### <a name="return-value"></a>Návratová hodnota

Komplexní čísla, pro který byla jako číslo zadané jako parametr odečtena od něj.

### <a name="remarks"></a>Poznámky

Operace je přetížena tak, aby jednoduché aritmetické operace se můžou provádět bez převodu dat na konkrétní formát.

### <a name="example"></a>Příklad

```cpp
// complex_op_se.cpp
// compile with: /EHsc
#include <complex>
#include <iostream>

int main( )
{
   using namespace std;
   double pi = 3.14159265359;

   // Example of the first member function
   // type complex<double> subtracted from type complex<double>
   complex <double> cl1 ( 3.0 , 4.0 );
   complex <double> cr1 ( 2.0 , -1.0 );
   cout << "The left-side complex number is cl1 = " << cl1 << endl;
   cout << "The right-side complex number is cr1 = " << cr1 << endl;

   complex <double> cs1 = cl1 - cr1;
   cout << "The difference between the two complex numbers is:"
        << "\n cs1 = cl1 - cr1 = " << cs1 << endl;

   // This is equivalent to the following operation
   cl1 -= cr1;
   cout << "Complex number cr1 subtracted from complex number cl1 is:"
        << "\n cl1 -= cr1 = " << cl1 << endl;

   double abscl1 = abs ( cl1 );
   double argcl1 = arg ( cl1 );
   cout << "The modulus of cl1 is: " << abscl1 << endl;
   cout << "The argument of cl1 is: "<< argcl1 << " radians, which is "
        << argcl1 * 180 / pi << " degrees." << endl << endl;

   // Example of the second member function
   // type double subtracted from type complex<double>
   complex <double> cl2 ( 2.0 , 4.0 );
   double cr2 = 5.0;
   cout << "The left-side complex number is cl2 = " << cl2 << endl;
   cout << "The right-side complex number is cr2 = " << cr2 << endl;

   complex <double> cs2 = cl2 - cr2;
   cout << "The difference between the two complex numbers is:"
        << "\n cs2 = cl2 - cr2 = " << cs2 << endl;

   // This is equivalent to the following operation
   cl2  -= cr2;
   cout << "Complex number cr2 subtracted from complex number cl2 is:"
        << "\n cl2 -= cr2 = " << cl2 << endl;

   double abscl2 = abs ( cl2 );
   double argcl2 = arg ( cl2 );
   cout << "The modulus of cl2 is: " << abscl2 << endl;
   cout << "The argument of cl2 is: "<< argcl2 << " radians, which is "
        << argcl2 * 180 / pi << " degrees." << endl << endl;
}
```

```Output
The left-side complex number is cl1 = (3,4)
The right-side complex number is cr1 = (2,-1)
The difference between the two complex numbers is:
cs1 = cl1 - cr1 = (1,5)
Complex number cr1 subtracted from complex number cl1 is:
cl1 -= cr1 = (1,5)
The modulus of cl1 is: 5.09902
The argument of cl1 is: 1.3734 radians, which is 78.6901 degrees.

The left-side complex number is cl2 = (2,4)
The right-side complex number is cr2 = 5
The difference between the two complex numbers is:
cs2 = cl2 - cr2 = (-3,4)
Complex number cr2 subtracted from complex number cl2 is:
cl2 -= cr2 = (-3,4)
The modulus of cl2 is: 5
The argument of cl2 is: 2.2143 radians, which is 126.87 degrees.
```

## <a name="op_div_eq"></a>  COMPLEX::Operator / =

Vydělí cílové komplexního čísla dělitelem, která může být komplexní nebo být stejného typu, jako jsou reálné a imaginární části komplexních číslo.

```cpp
template <class Other>
complex<Type>& operator/=(const complex<Other>& complexNum);

complex<Type>& operator/=(const Type& _RealPart);

complex<Type>& operator/=(const complex<Type>& complexNum);
```

### <a name="parameters"></a>Parametry

*complexNum*<br/>
Komplexní čísla se odečítají z cílové komplexního čísla.

*_RealPart*<br/>
Reálné číslo bude odečítat od cílové komplexního čísla.

### <a name="return-value"></a>Návratová hodnota

Komplexní čísla, které byly rozdělené podle čísla, zadaný jako parametr.

### <a name="remarks"></a>Poznámky

Operace je přetížena tak, aby jednoduché aritmetické operace se můžou provádět bez převodu dat na konkrétní formát.

### <a name="example"></a>Příklad

```cpp
// complex_op_de.cpp
// compile with: /EHsc
#include <complex>
#include <iostream>

int main( )
{
   using namespace std;
   double pi = 3.14159265359;

   // Example of the first member function
   // type complex<double> divided by type complex<double>
   complex <double> cl1 ( polar (3.0 , pi / 6 ) );
   complex <double> cr1 ( polar (2.0 , pi / 3 ) );
   cout << "The left-side complex number is cl1 = " << cl1 << endl;
   cout << "The right-side complex number is cr1 = " << cr1 << endl;

   complex <double> cs1 = cl1 / cr1;
   cout << "The quotient of the two complex numbers is: cs1 = cl1 /cr1 = "
        << cs1 << endl;

   // This is equivalent to the following operation
   cl1 /= cr1;
   cout << "Quotient of two complex numbers is also: cl1 /= cr1 = "
        << cl1 << endl;

   double abscl1 = abs ( cl1 );
   double argcl1 = arg ( cl1 );
   cout << "The modulus of cl1 is: " << abscl1 << endl;
   cout << "The argument of cl1 is: "<< argcl1 << " radians, which is "
        << argcl1 * 180 / pi << " degrees." << endl << endl;

   // Example of the second member function
   // type complex<double> divided by type double
   complex <double> cl2 ( polar (3.0 , pi / 6 ) );
   double cr2 =5;
   cout << "The left-side complex number is cl2 = " << cl2 << endl;
   cout << "The right-side complex number is cr2 = " << cr2 << endl;

   complex <double> cs2 = cl2 / cr2;
   cout << "The quotient of the two complex numbers is: cs2 /= cl2 cr2 = "
        << cs2 << endl;

   // This is equivalent to the following operation
   cl2 /= cr2;
   cout << "Quotient of two complex numbers is also: cl2 = /cr2 = "
        << cl2 << endl;

   double abscl2 = abs ( cl2 );
   double argcl2 = arg ( cl2 );
   cout << "The modulus of cl2 is: " << abscl2 << endl;
   cout << "The argument of cl2 is: "<< argcl2 << " radians, which is "
        << argcl2 * 180 / pi << " degrees." << endl << endl;
}
```

```Output
The left-side complex number is cl1 = (2.59808,1.5)
The right-side complex number is cr1 = (1,1.73205)
The quotient of the two complex numbers is: cs1 = cl1 /cr1 = (1.29904,-0.75)
Quotient of two complex numbers is also: cl1 /= cr1 = (1.29904,-0.75)
The modulus of cl1 is: 1.5
The argument of cl1 is: -0.523599 radians, which is -30 degrees.

The left-side complex number is cl2 = (2.59808,1.5)
The right-side complex number is cr2 = 5
The quotient of the two complex numbers is: cs2 /= cl2 cr2 = (0.519615,0.3)
Quotient of two complex numbers is also: cl2 = /cr2 = (0.519615,0.3)
The modulus of cl2 is: 0.6
The argument of cl2 is: 0.523599 radians, which is 30 degrees.
```

## <a name="op_eq"></a>  COMPLEX::Operator =

Přiřadí číslo cílového komplexního čísla, kde může být složitý číslo přiřazené nebo stejného typu, jako jsou reálné a imaginární části komplexní čísla, ke kterému je přiřazen.

```cpp
template <class Other>
complex<Type>& operator=(const complex<Other>& right);

complex<Type>& operator=(const Type& right);
```

### <a name="parameters"></a>Parametry

*doprava*<br/>
Komplexní čísla nebo číslo, které je stejného typu jako parametr komplexního čísla cíl.

### <a name="return-value"></a>Návratová hodnota

Komplexní čísla, který byl přiřazen jako číslo zadané jako parametr.

### <a name="remarks"></a>Poznámky

Operace je přetížena tak, aby jednoduché aritmetické operace se můžou provádět bez převodu dat na konkrétní formát.

### <a name="example"></a>Příklad

```cpp
// complex_op_as.cpp
// compile with: /EHsc
#include <complex>
#include <iostream>

int main( )
{
   using namespace std;
   double pi = 3.14159265359;

   // Example of the first member function
   // type complex<double> assigned to type complex<double>
   complex <double> cl1 ( 3.0 , 4.0 );
   complex <double> cr1 ( 2.0 , -1.0 );
   cout << "The left-side complex number is cl1 = " << cl1 << endl;
   cout << "The right-side complex number is cr1 = " << cr1 << endl;

   cl1  = cr1;
   cout << "The complex number cr1 assigned to the complex number cl1 is:"
        << "\ncl1 = cr1 = " << cl1 << endl;

   // Example of the second member function
   // type double assigned to type complex<double>
   complex <double> cl2 ( -2 , 4 );
   double cr2 =5.0;
   cout << "The left-side complex number is cl2 = " << cl2 << endl;
   cout << "The right-side complex number is cr2 = " << cr2 << endl;

   cl2 = cr2;
   cout << "The complex number cr2 assigned to the complex number cl2 is:"
        << "\ncl2 = cr2 = " << cl2 << endl;

   cl2 = complex<double>(3.0, 4.0);
   cout << "The complex number (3, 4) assigned to the complex number cl2 is:"
        << "\ncl2 = " << cl2 << endl;
}
```

```Output
The left-side complex number is cl1 = (3,4)
The right-side complex number is cr1 = (2,-1)
The complex number cr1 assigned to the complex number cl1 is:
cl1 = cr1 = (2,-1)
The left-side complex number is cl2 = (-2,4)
The right-side complex number is cr2 = 5
The complex number cr2 assigned to the complex number cl2 is:
cl2 = cr2 = (5,0)
The complex number (3, 4) assigned to the complex number cl2 is:
cl2 = (3,4)
```

## <a name="real"></a>  COMPLEX::Real

Získá nebo nastaví reálnou součástí komplexního čísla.

```cpp
constexpr T real() const;


T real(const T& right);
```

### <a name="parameters"></a>Parametry

*doprava*<br/>
Komplexní čísla, jejichž skutečné hodnoty je třeba extrahovat.

### <a name="return-value"></a>Návratová hodnota

Skutečné součástí komplexní čísla.

### <a name="remarks"></a>Poznámky

Pro komplexní čísla *+ bi*, skutečné část nebo součást je *Re(a + bi) =.*

### <a name="example"></a>Příklad

```cpp
// complex_class_real.cpp
// compile with: /EHsc
#include <complex>
#include <iostream>

int main( )
{
   using namespace std;

   complex <double> c1 ( 4.0 , 3.0 );
   cout << "The complex number c1 = " << c1 << endl;

   double dr1 = c1.real ( );
   cout << "The real part of c1 is c1.real ( ) = "
        << dr1 << "." << endl;

   double di1 = c1.imag ( );
   cout << "The imaginary part of c1 is c1.imag ( ) = "
        << di1 << "." << endl;
}
```

```Output
The complex number c1 = (4,3)
The real part of c1 is c1.real ( ) = 4.
The imaginary part of c1 is c1.imag ( ) = 3.
```

## <a name="value_type"></a>  COMPLEX::value_type

Typ, který představuje datový typ používá k reprezentování reálné a imaginární části komplexního čísla.

```

typedef Type value_type;
```

### <a name="remarks"></a>Poznámky

`value_type` je synonymum pro třídu komplexní `Type` parametr šablony.

### <a name="example"></a>Příklad

```cpp
// complex_valuetype.cpp
// compile with: /EHsc
#include <complex>
#include <iostream>

int main( )
{
   using namespace std;
   complex <double>::value_type a = 3, b = 4;

   complex <double> c1 ( a , b );
   cout << "Specifying initial real & imaginary parts"
      << "\nof type value_type: "
      << "c1 = " << c1 << "." << endl;
}
```

```Output
Specifying initial real & imaginary parts
of type value_type: c1 = (3,4).
```

## <a name="see-also"></a>Viz také:

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
