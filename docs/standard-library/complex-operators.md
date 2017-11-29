---
title: "&lt;komplexní&gt; operátory | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- xcomplex/std::operator!=
- xcomplex/std::operator&gt;&gt;
- xcomplex/std::operator&lt;&lt;
- xcomplex/std::operator*
- xcomplex/std::operator+
- xcomplex/std::operator-
- xcomplex/std::operator/
- xcomplex/std::operator==
dev_langs: C++
ms.assetid: aa282604-dcb9-46a2-bf1d-34c50aa6c4ba
caps.latest.revision: "11"
manager: ghogen
helpviewer_keywords:
- std::operator!= (complex)
- std::operator&gt;&gt; (complex)
- std::operator&lt;&lt; (complex), std::operator== (complex)
ms.openlocfilehash: 46d469b2e9befbc1effbb4b34e47f5cd7dc4f3f4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ltcomplexgt-operators"></a>&lt;komplexní&gt; operátory
||||  
|-|-|-|  
|[Operator! =](#op_neq)|[operátor&gt;&gt;](#op_gt_gt)|[operátor&lt;&lt;](#op_lt_lt)|  
|[operátor *](#op_star)|[operátor +](#op_add)|[Operator –](#operator-)|  
|[operátor nebo](#op_div)|[Operator ==](#op_eq_eq)|  
  
##  <a name="op_neq"></a>Operator! =  
 Testy nerovnost mezi dvěma komplexní čísla, jednu nebo obě dvě může patřit k podskupině typu pro skutečné a pomyslná části.  
  
```  
 
template <class Type>  
bool operator!=(
    const complex<Type>& left,  
    const complex<Type>& right);

template <class Type>  
bool operator!=(
    const complex<Type>& left,  
    const Type& right);

template <class Type>  
bool operator!=(
    const Type& left,  
    const complex<Type>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `left`  
 Komplexní čísla nebo jeho typu parametru má být testována nerovnost objektu.  
  
 `right`  
 Komplexní čísla nebo jeho typu parametru má být testována nerovnost objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud čísla, která není stejný; **false** Pokud čísla jsou stejné.  
  
### <a name="remarks"></a>Poznámky  
 Dva komplexní čísla jsou stejné, pokud jejich skutečné části jsou stejné, a jejich pomyslná části jsou stejné. Jinak nerovné.  
  
 Operace je přetížena tak, aby porovnání testy mohou být provedeny bez převodu dat do konkrétní formátu.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// complex_op_NE.cpp  
// compile with: /EHsc  
#include <complex>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   double pi = 3.14159265359;  
  
   // Example of the first member function  
   // type complex<double> compared with type complex<double>  
   complex <double> cl1 ( polar (3.0, pi / 6 ) );  
   complex <double> cr1a ( polar (3.0, pi /6 ) );  
   complex <double> cr1b ( polar (2.0, pi / 3 ) );  
  
   cout << "The left-side complex number is cl1 = " << cl1 << endl;  
   cout << "The 1st right-side complex number is cr1a = " << cr1a << endl;  
   cout << "The 2nd right-side complex number is cr1b = " << cr1b << endl;  
   if ( cl1 != cr1a )  
      cout << "The complex numbers cl1 & cr1a are not equal." << endl;  
   else  
      cout << "The complex numbers cl1 & cr1a are equal." << endl;  
   if ( cl1 != cr1b )  
      cout << "The complex numbers cl1 & cr1b are not equal." << endl;  
   else  
      cout << "The complex numbers cl1 & cr1b are equal." << endl;  
   cout << endl;  
  
   // Example of the second member function  
   // type complex<int> compared with type int  
   complex <int> cl2a ( 3, 4 );  
   complex <int> cl2b ( 5,0 );  
   int cr2a =3;  
   int cr2b =5;  
  
   cout << "The 1st left-side complex number is cl2a = " << cl2a << endl;  
   cout << "The 1st right-side complex number is cr2a = " << cr2a << endl;  
   if ( cl2a != cr2a )  
      cout << "The complex numbers cl2a & cr2a are not equal." << endl;  
   else  
      cout << "The complex numbers cl2a & cr2a are equal." << endl;  
  
   cout << "The 2nd left-side complex number is cl2b = " << cl2b << endl;  
   cout << "The 2nd right-side complex number is cr2b = " << cr2b << endl;  
   if ( cl2b != cr2b )  
      cout << "The complex numbers cl2b & cr2b are not equal." << endl;  
   else  
      cout << "The complex numbers cl2b & cr2b are equal." << endl;  
   cout << endl;  
  
   // Example of the third member function  
   // type double compared with type complex<double>  
   double cl3a =3;  
   double cl3b =5;  
   complex <double> cr3a ( 3, 4 );  
   complex <double> cr3b ( 5,0 );  
  
   cout << "The 1st left-side complex number is cl3a = " << cl3a << endl;  
   cout << "The 1st right-side complex number is cr3a = " << cr3a << endl;  
   if ( cl3a != cr3a )  
      cout << "The complex numbers cl3a & cr3a are not equal." << endl;  
   else  
      cout << "The complex numbers cl3a & cr3a are equal." << endl;  
  
   cout << "The 2nd left-side complex number is cl3b = " << cl3b << endl;  
   cout << "The 2nd right-side complex number is cr3b = " << cr3b << endl;  
   if ( cl3b != cr3b )  
      cout << "The complex numbers cl3b & cr3b are not equal." << endl;  
   else  
      cout << "The complex numbers cl3b & cr3b are equal." << endl;  
   cout << endl;  
}  
```  
  
```Output  
The left-side complex number is cl1 = (2.59808,1.5)  
The 1st right-side complex number is cr1a = (2.59808,1.5)  
The 2nd right-side complex number is cr1b = (1,1.73205)  
The complex numbers cl1 & cr1a are equal.  
The complex numbers cl1 & cr1b are not equal.  
  
The 1st left-side complex number is cl2a = (3,4)  
The 1st right-side complex number is cr2a = 3  
The complex numbers cl2a & cr2a are not equal.  
The 2nd left-side complex number is cl2b = (5,0)  
The 2nd right-side complex number is cr2b = 5  
The complex numbers cl2b & cr2b are equal.  
  
The 1st left-side complex number is cl3a = 3  
The 1st right-side complex number is cr3a = (3,4)  
The complex numbers cl3a & cr3a are not equal.  
The 2nd left-side complex number is cl3b = 5  
The 2nd right-side complex number is cr3b = (5,0)  
The complex numbers cl3b & cr3b are equal.  
```  
  
##  <a name="op_star"></a>operátor *  
 Vynásobí dvě komplexní čísla, jednu nebo obě dvě může patřit k podskupině typu pro skutečné a pomyslná části.  
  
```  
 
template <class Type>  
complex<Type> operator*(
    const complex<Type>& left,  
    const complex<Type>& right);

template <class Type>  
complex<Type> operator*(
    const complex<Type>& left,  
    const Type& right);

template <class Type>  
complex<Type> operator*(
    const Type& left,  
    const complex<Type>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `left`  
 První dvě komplexní čísla nebo číslo, které je typ parametru pro komplexní číslo, které má být násobí hodnotou * operaci.  
  
 `right`  
 Druhá dvě komplexní čísla nebo číslo, které je typ parametru pro komplexní číslo, které má být násobí hodnotou * operaci.  
  
### <a name="return-value"></a>Návratová hodnota  
 Komplexního čísla, která je výsledkem násobení dvou čísel, jehož hodnota a typ jsou určené parametr vstupy.  
  
### <a name="remarks"></a>Poznámky  
 Operace je přetížena tak, aby jednoduché aritmetické operace lze provést bez převodu dat do konkrétní formátu.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// complex_op_mult.cpp  
// compile with: /EHsc  
#include <complex>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   double pi = 3.14159265359;  
  
   // Example of the first member function  
   // type complex<double> times type complex<double>  
   complex <double> cl1 ( polar (3.0, pi / 6 ) );  
   complex <double> cr1 ( polar (2.0, pi / 3 ) );  
   complex <double> cs1 = cl1 * cr1;  
  
   cout << "The left-side complex number is cl1 = " << cl1 << endl;  
   cout << "The right-side complex number is cr1 = " << cr1 << endl;  
   cout << "Product of two complex numbers is: cs1 = " << cs1 << endl;  
   double abscs1 = abs ( cs1 );  
   double argcs1 = arg ( cs1 );  
   cout << "The modulus of cs1 is: " << abscs1 << endl;  
   cout << "The argument of cs1 is: "<< argcs1 << " radians, which is "  
        << argcs1 * 180 / pi << " degrees." << endl << endl;  
  
   // Example of the second member function  
   // type complex<double> times type double  
   complex <double> cl2 ( polar ( 3.0, pi / 6 ) );  
   double cr2 =5;  
   complex <double> cs2 = cl2 * cr2;  
  
   cout << "The left-side complex number is cl2 = " << cl2 << endl;  
   cout << "The right-side complex number is cr2 = " << cr2 << endl;  
   cout << "Product of two complex numbers is: cs2 = " << cs2 << endl;  
   double abscs2 = abs ( cs2 );  
   double argcs2 = arg ( cs2 );  
   cout << "The modulus of cs2 is: " << abscs2 << endl;  
   cout << "The argument of cs2 is: "<< argcs2 << " radians, which is "  
        << argcs2 * 180 / pi << " degrees." << endl << endl;  
  
   // Example of the third member function  
   // type double times type complex<double>  
   double cl3 = 5;  
   complex <double> cr3 ( polar (3.0, pi / 6 ) );  
   complex <double> cs3 = cl3 * cr3;  
  
   cout << "The left-side complex number is cl3 = " << cl3 << endl;  
   cout << "The right-side complex number is cr3 = " << cr3 << endl;  
   cout << "Product of two complex numbers is: cs3 = " << cs3 << endl;  
   double abscs3 = abs ( cs3 );  
   double argcs3 = arg ( cs3 );  
   cout << "The modulus of cs3 is: " << abscs3 << endl;  
   cout << "The argument of cs3 is: "<< argcs3 << " radians, which is "  
        << argcs3 * 180 / pi << " degrees." << endl << endl;  
}  
```  
  
##  <a name="op_add"></a>operátor +  
 Přidá dvě komplexní čísla, jednu nebo obě dvě může patřit k podmnožině typ pro skutečné a pomyslná části.  
  
```  
 
template <class Type>  
complex<Type> operator+(
    const complex<Type>& left,  
    const complex<Type>& right);

template <class Type>  
complex<Type> operator+(
    const complex<Type>& left,  
    const Type& right);

template <class Type>  
complex<Type> operator+(
    const Type& left,  
    const complex<Type>& right);

template <class Type>  
complex<Type> operator+(const complex<Type>& left);
```  
  
### <a name="parameters"></a>Parametry  
 `left`  
 První dvě komplexní čísla nebo číslo, které je typ parametru pro komplexní číslo, které má být přidán podle + operaci.  
  
 `right`  
 Druhá dvě komplexní čísla nebo číslo, které je typ parametru pro komplexní číslo, které má být přidán podle + operaci.  
  
### <a name="return-value"></a>Návratová hodnota  
 Komplexní čísla, která je výsledkem přidání dvou čísel, jehož hodnota a typ jsou určené parametr vstupy.  
  
### <a name="remarks"></a>Poznámky  
 Operace je přetížena tak, aby jednoduché aritmetické operace lze provést bez převodu dat do konkrétní formátu. Unární operátor vrátí `left`.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// complex_op_add.cpp  
// compile with: /EHsc  
#include <complex>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   double pi = 3.14159265359;  
  
   // Example of the first member function  
   // type complex<double> plus type complex<double>  
   complex <double> cl1 ( 3.0, 4.0 );  
   complex <double> cr1 ( 2.0, 5.0 );  
   complex <double> cs1 = cl1 + cr1;  
  
   cout << "The left-side complex number is cl1 = " << cl1 << endl;  
   cout << "The right-side complex number is cr1 = " << cr1 << endl;  
   cout << "The sum of the two complex numbers is: cs1 = " << cs1 << endl;  
   double abscs1 = abs ( cs1 );  
   double argcs1 = arg ( cs1 );  
   cout << "The modulus of cs1 is: " << abscs1 << endl;  
   cout << "The argument of cs1 is: "<< argcs1 << " radians, which is "   
        << argcs1 * 180 / pi << " degrees." << endl << endl;   
  
   // Example of the second member function  
   // type complex<double> plus type double  
   complex <double> cl2 ( 3.0, 4.0 );  
   double cr2 =5.0;  
   complex <double> cs2 = cl2 + cr2;  
  
   cout << "The left-side complex number is cl2 = " << cl2 << endl;  
   cout << "The right-side complex number is cr2 = " << cr2 << endl;  
   cout << "The sum of the two complex numbers is: cs2 = " << cs2 << endl;  
   double abscs2 = abs ( cs2 );  
   double argcs2 = arg ( cs2 );  
   cout << "The modulus of cs2 is: " << abscs2 << endl;  
   cout << "The argument of cs2 is: "<< argcs2 << " radians, which is "   
        << argcs2 * 180 / pi << " degrees." << endl << endl;  
  
   // Example of the third member function  
   // type double plus type complex<double>  
   double cl3 = 5.0;  
   complex <double> cr3 ( 3.0, 4.0 );  
   complex <double> cs3 = cl3 + cr3;  
  
   cout << "The left-side complex number is cl3 = " << cl3 << endl;  
   cout << "The right-side complex number is cr3 = " << cr3 << endl;  
   cout << "The sum of the two complex numbers is: cs3 = " << cs3 << endl;  
   double abscs3 = abs ( cs3 );  
   double argcs3 = arg ( cs3 );  
   cout << "The modulus of cs3 is: " << abscs3 << endl;  
   cout << "The argument of cs3 is: "<< argcs3 << " radians, which is "   
        << argcs3 * 180 / pi << " degrees." << endl << endl;   
  
   // Example of the fourth member function  
   // plus type complex<double>  
   complex <double> cr4 ( 3.0, 4.0 );  
   complex <double> cs4 = + cr4;  
  
   cout << "The right-side complex number is cr4 = " << cr4 << endl;  
   cout << "The result of the unary application of + to the right-side"  
        << "\n complex number is: cs4 = " << cs4 << endl;  
   double abscs4 = abs ( cs4 );  
   double argcs4 = arg ( cs4 );  
   cout << "The modulus of cs4 is: " << abscs4 << endl;  
   cout << "The argument of cs4 is: "<< argcs4 << " radians, which is "   
        << argcs4 * 180 / pi << " degrees." << endl << endl;    
}  
```  
  
```Output  
The left-side complex number is cl1 = (3,4)  
The right-side complex number is cr1 = (2,5)  
The sum of the two complex numbers is: cs1 = (5,9)  
The modulus of cs1 is: 10.2956  
The argument of cs1 is: 1.0637 radians, which is 60.9454 degrees.  
  
The left-side complex number is cl2 = (3,4)  
The right-side complex number is cr2 = 5  
The sum of the two complex numbers is: cs2 = (8,4)  
The modulus of cs2 is: 8.94427  
The argument of cs2 is: 0.463648 radians, which is 26.5651 degrees.  
  
The left-side complex number is cl3 = 5  
The right-side complex number is cr3 = (3,4)  
The sum of the two complex numbers is: cs3 = (8,4)  
The modulus of cs3 is: 8.94427  
The argument of cs3 is: 0.463648 radians, which is 26.5651 degrees.  
  
The right-side complex number is cr4 = (3,4)  
The result of the unary application of + to the right-side  
 complex number is: cs4 = (3,4)  
The modulus of cs4 is: 5  
The argument of cs4 is: 0.927295 radians, which is 53.1301 degrees.  
```  
  
##  <a name="operator-"></a>Operator –  
 Odečítá od dva komplexní čísla, jednu nebo obě dvě může patřit k podskupině typu pro skutečné a pomyslná části.  
  
```   
template <class Type>  
complex<Type> operator-(
    const complex<Type>& left,  
    const complex<Type>& right);

template <class Type>  
complex<Type> operator-(
    const complex<Type>& left,  
    const Type& right);

template <class Type>  
complex<Type> operator-(
    const Type& left,  
    const complex<Type>& right);

template <class Type>  
complex<Type> operator-(const complex<Type>& left);
```  
  
### <a name="parameters"></a>Parametry  
 `left`  
 První dvě komplexní čísla nebo číslo, které je typ parametru pro komplexní číslo, které se bude odečítat-operace.  
  
 `right`  
 Druhá dvě komplexní čísla nebo číslo, které je typ parametru pro komplexní číslo, které se bude odečítat-operace.  
  
### <a name="return-value"></a>Návratová hodnota  
 Komplexního čísla, která je výsledkem odčítání z `right` z `left`, jejichž hodnoty jsou určené vstupy parametr dvou čísel.  
  
### <a name="remarks"></a>Poznámky  
 Operace je přetížena tak, aby jednoduché aritmetické operace lze provést bez převodu dat do konkrétní formátu.  
  
 Unární operátor změní přihlašovací komplexního čísla a vrátí hodnotu, jejíž skutečné součást je záporná skutečné součástí počet a jejíž pomyslná součást je záporná pomyslná součástí počet.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// complex_op_sub.cpp  
// compile with: /EHsc  
#include <complex>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   double pi = 3.14159265359;  
  
   // Example of the first member function  
   // type complex<double> minus type complex<double>  
   complex <double> cl1 ( 3.0, 4.0 );  
   complex <double> cr1 ( 2.0, 5.0 );  
   complex <double> cs1 = cl1 - cr1;  
  
   cout << "The left-side complex number is cl1 = " << cl1 << endl;  
   cout << "The right-side complex number is cr1 = " << cr1 << endl;  
   cout << "Difference of two complex numbers is: cs1 = " << cs1 << endl;  
   double abscs1 = abs ( cs1 );  
   double argcs1 = arg ( cs1 );  
   cout << "The modulus of cs1 is: " << abscs1 << endl;  
   cout << "The argument of cs1 is: "<< argcs1 << " radians, which is "   
        << argcs1 * 180 / pi << " degrees." << endl << endl;   
  
   // Example of the second member function  
   // type complex<double> minus type double  
   complex <double> cl2 ( 3.0, 4.0 );  
   double cr2 =5.0;  
   complex <double> cs2 = cl2 - cr2;  
  
   cout << "The left-side complex number is cl2 = " << cl2 << endl;  
   cout << "The right-side complex number is cr2 = " << cr2 << endl;  
   cout << "Difference of two complex numbers is: cs2 = " << cs2 << endl;  
   double abscs2 = abs ( cs2 );  
   double argcs2 = arg ( cs2 );  
   cout << "The modulus of cs2 is: " << abscs2 << endl;  
   cout << "The argument of cs2 is: "<< argcs2 << " radians, which is "   
        << argcs2 * 180 / pi << " degrees." << endl << endl;  
  
   // Example of the third member function  
   // type double minus type complex<double>  
   double cl3 = 5.0;  
   complex <double> cr3 ( 3.0, 4.0 );  
   complex <double> cs3 = cl3 - cr3;  
  
   cout << "The left-side complex number is cl3 = " << cl3 << endl;  
   cout << "The right-side complex number is cr3 = " << cr3 << endl;  
   cout << "Difference of two complex numbers is: cs3 = " << cs3 << endl;  
   double abscs3 = abs ( cs3 );  
   double argcs3 = arg ( cs3 );  
   cout << "The modulus of cs3 is: " << abscs3 << endl;  
   cout << "The argument of cs3 is: "<< argcs3 << " radians, which is "   
        << argcs3 * 180 / pi << " degrees." << endl << endl;   
  
   // Example of the fourth member function  
   // minus type complex<double>  
   complex <double> cr4 ( 3.0, 4.0 );  
   complex <double> cs4 = - cr4;  
  
   cout << "The right-side complex number is cr4 = " << cr4 << endl;  
   cout << "The result of the unary application of - to the right-side"  
        << "\n complex number is: cs4 = " << cs4 << endl;  
   double abscs4 = abs ( cs4 );  
   double argcs4 = arg ( cs4 );  
   cout << "The modulus of cs4 is: " << abscs4 << endl;  
   cout << "The argument of cs4 is: "<< argcs4 << " radians, which is "   
        << argcs4 * 180 / pi << " degrees." << endl << endl;    
}  
```  
  
```Output  
The left-side complex number is cl1 = (3,4)  
The right-side complex number is cr1 = (2,5)  
Difference of two complex numbers is: cs1 = (1,-1)  
The modulus of cs1 is: 1.41421  
The argument of cs1 is: -0.785398 radians, which is -45 degrees.  
  
The left-side complex number is cl2 = (3,4)  
The right-side complex number is cr2 = 5  
Difference of two complex numbers is: cs2 = (-2,4)  
The modulus of cs2 is: 4.47214  
The argument of cs2 is: 2.03444 radians, which is 116.565 degrees.  
  
The left-side complex number is cl3 = 5  
The right-side complex number is cr3 = (3,4)  
Difference of two complex numbers is: cs3 = (2,-4)  
The modulus of cs3 is: 4.47214  
The argument of cs3 is: -1.10715 radians, which is -63.4349 degrees.  
  
The right-side complex number is cr4 = (3,4)  
The result of the unary application of - to the right-side  
 complex number is: cs4 = (-3,-4)  
The modulus of cs4 is: 5  
The argument of cs4 is: -2.2143 radians, which is -126.87 degrees.  
```  
  
##  <a name="op_div"></a>operátor nebo  
 Vydělí dvě komplexní čísla, jednu nebo obě dvě může patřit k podskupině typu pro skutečné a pomyslná části.  
  
```   
template <class Type>  
complex<Type> operator*(
    const complex<Type>& left,  
    const complex<Type>& right);

template <class Type>  
complex<Type> operator*(
    const complex<Type>& left,  
    const Type& right);

template <class Type>  
complex<Type> operator*(
    const Type& left,  
    const complex<Type>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `left`  
 Komplexní číslo nebo číslo, které je typ parametru pro komplexní číslo, které je rozdělit podle jmenovatel s čítači nebo operace.  
  
 `right`  
 Komplexní číslo nebo číslo, které je typ parametru pro komplexní číslo, které je jmenovatel, který se má použít k rozdělení čítači s nebo operace.  
  
### <a name="return-value"></a>Návratová hodnota  
 Číslo komplexní, která je výsledkem rozdělení čítači podle jmenovatel, hodnoty, které jsou určené parametr vstupy.  
  
### <a name="remarks"></a>Poznámky  
 Operace je přetížena tak, aby jednoduché aritmetické operace lze provést bez převodu dat do konkrétní formátu.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// complex_op_div.cpp  
// compile with: /EHsc  
#include <complex>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   double pi = 3.14159265359;  
  
   // Example of the first member function  
   // type complex<double> divided by type complex<double>  
   complex <double> cl1 ( polar ( 3.0, pi / 6 ) );  
   complex <double> cr1 ( polar ( 2.0, pi / 3 ) );  
   complex <double> cs1 = cl1 / cr1;  
  
   cout << "The left-side complex number is cl1 = " << cl1 << endl;  
   cout << "The right-side complex number is cr1 = " << cr1 << endl;  
   cout << "The quotient of the two complex numbers is: cs1 = cl1 /cr1 = "  
        << cs1 << endl;  
   double abscs1 = abs ( cs1 );  
   double argcs1 = arg ( cs1 );  
   cout << "The modulus of cs1 is: " << abscs1 << endl;  
   cout << "The argument of cs1 is: "<< argcs1 << " radians, which is "   
        << argcs1 * 180 / pi << " degrees." << endl << endl;   
  
   // example of the second member function  
   // type complex<double> divided by type double  
   complex <double> cl2 ( polar (3.0, pi / 6 ) );  
   double cr2 =5;  
   complex <double> cs2 = cl2 / cr2;  
  
   cout << "The left-side complex number is cl2 = " << cl2 << endl;  
   cout << "The right-side complex number is cr2 = " << cr2 << endl;  
   cout << "The quotient of the two complex numbers is: cs2 = cl2 /cr2 = "   
        << cs2 << endl;  
   double abscs2 = abs ( cs2 );  
   double argcs2 = arg ( cs2 );  
   cout << "The modulus of cs2 is: " << abscs2 << endl;  
   cout << "The argument of cs2 is: "<< argcs2 << " radians, which is "   
        << argcs2 * 180 / pi << " degrees." << endl << endl;  
  
   // Example of the third member function  
   // type double divided by type complex<double>  
   double cl3 = 5;  
   complex <double> cr3 ( polar ( 3.0, pi / 6 ) );  
   complex <double> cs3 = cl3 / cr3;  
  
   cout << "The left-side complex number is cl3 = " << cl3 << endl;  
   cout << "The right-side complex number is cr3 = " << cr3 << endl;  
   cout << "The quotient of the two complex numbers is: cs3 = cl3 /cr2 = "  
        << cs3 << endl;  
   double abscs3 = abs ( cs3 );  
   double argcs3 = arg ( cs3 );  
   cout << "The modulus of cs3 is: " << abscs3 << endl;  
   cout << "The argument of cs3 is: "<< argcs3 << " radians, which is "   
        << argcs3 * 180 / pi << " degrees." << endl << endl;  
}  
```  
  
```Output  
The left-side complex number is cl1 = (2.59808,1.5)  
The right-side complex number is cr1 = (1,1.73205)  
The quotient of the two complex numbers is: cs1 = cl1 /cr1 = (1.29904,-0.75)  
The modulus of cs1 is: 1.5  
The argument of cs1 is: -0.523599 radians, which is -30 degrees.  
  
The left-side complex number is cl2 = (2.59808,1.5)  
The right-side complex number is cr2 = 5  
The quotient of the two complex numbers is: cs2 = cl2 /cr2 = (0.519615,0.3)  
The modulus of cs2 is: 0.6  
The argument of cs2 is: 0.523599 radians, which is 30 degrees.  
  
The left-side complex number is cl3 = 5  
The right-side complex number is cr3 = (2.59808,1.5)  
The quotient of the two complex numbers is: cs3 = cl3 /cr2 = (1.44338,-0.833333)  
The modulus of cs3 is: 1.66667  
The argument of cs3 is: -0.523599 radians, which is -30 degrees.  
```  
  
##  <a name="op_lt_lt"></a>operátor&lt;&lt;  
 Vloží komplexní číslo, zadané do výstupního datového proudu.  
  
```   
template <class Type, class Elem, class Traits>  
basic_ostream<Elem, Traits>& operator<<(
    basic_ostream<Elem, Traits>& Ostr,  
    const complex<Type>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `Ostr`  
 Výstupní datový proud, do kterého je zadané číslo komplexní.  
  
 `right`  
 Komplexní číslo, je třeba zadat do výstupního datového proudu  
  
### <a name="return-value"></a>Návratová hodnota  
 Zapíše hodnota zadaný komplexní číslo, `Ostr` ve formátu kartézských: ( *skutečné část, pomyslná část* ).  
  
### <a name="remarks"></a>Poznámky  
 Výstupní datový proud je přetížena tak, že bude akceptovat jakoukoli formu komplexního čísla a jeho výchozí formát výstupu se kartézských formátu.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// complex_op_insert.cpp  
// compile with: /EHsc  
#include <complex>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   double pi = 3.14159265359;  
  
   complex <double> c1 ( 3.0, 4.0 );  
   cout << "Complex number c1 = " << c1 << endl;  
  
   complex <double> c2  ( polar ( 2.0, pi / 6 ) );  
   cout << "Complex number c2 = " << c2 << endl;  
  
   // To display in polar form  
   double absc2 = abs ( c2 );  
   double argc2 = arg ( c2 );  
   cout << "The modulus of c2 is: " << absc2 << endl;  
   cout << "The argument of c2 is: "<< argc2 << " radians, which is "   
        << argc2 * 180 / pi << " degrees." << endl << endl;  
}  
```  
  
```Output  
Complex number c1 = (3,4)  
Complex number c2 = (1.73205,1)  
The modulus of c2 is: 2  
The argument of c2 is: 0.523599 radians, which is 30 degrees.  
```  
  
##  <a name="op_eq_eq"></a>Operator ==  
 Testování rovnosti mezi dvěma komplexní čísla, jednu nebo obě dvě může patřit k podskupině typu pro skutečné a pomyslná části.  
  
```  
 
template <class Type>  
bool operator==(
    const complex<Type>& left,  
    const complex<Type>& right);

template <class Type>  
bool operator==(
    const complex<Type>& left,  
    const Type& right);

template <class Type>  
bool operator==(
    const Type& left,  
    const complex<Type>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `left`  
 Komplexní čísla nebo jeho typu parametru má být testována nerovnost objektu.  
  
 `right`  
 Komplexní čísla nebo jeho typu parametru má být testována nerovnost objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud čísla, která jsou si rovny; **false** Pokud čísla nejsou stejné.  
  
### <a name="remarks"></a>Poznámky  
 Dva komplexní čísla jsou stejné, pokud jejich skutečné části jsou stejné, a jejich pomyslná části jsou stejné. Jinak nerovné.  
  
 Operace je přetížena tak, aby porovnání testy mohou být provedeny bez převodu dat do konkrétní formátu.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// complex_op_EQ.cpp  
// compile with: /EHsc  
#include <complex>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   double pi = 3.14159265359;  
  
   // Example of the first member function  
   // type complex<double> compared with type complex<double>  
   complex <double> cl1 ( polar ( 3.0, pi / 6 ) );  
   complex <double> cr1a ( polar ( 3.0, pi /6 ) );  
   complex <double> cr1b ( polar ( 2.0, pi / 3 ) );  
  
   cout << "The left-side complex number is cl1 = " << cl1 << endl;  
   cout << "The 1st right-side complex number is cr1a = " << cr1a << endl;  
   cout << "The 2nd right-side complex number is cr1b = " << cr1b << endl;  
   if ( cl1 == cr1a )  
      cout << "The complex numbers cl1 & cr1a are equal." << endl;  
   else  
      cout << "The complex numbers cl1 & cr1a are not equal." << endl;  
   if ( cl1 == cr1b )  
      cout << "The complex numbers cl1 & cr1b are equal." << endl;  
   else  
      cout << "The complex numbers cl1 & cr1b are not equal." << endl;  
   cout << endl;  
  
   // Example of the second member function  
   // type complex<int> compared with type int  
   complex <int> cl2a ( 3, 4 );  
   complex <int> cl2b ( 5,0 );  
   int cr2a =3;  
   int cr2b =5;  
  
   cout << "The 1st left-side complex number is cl2a = " << cl2a << endl;  
   cout << "The 1st right-side complex number is cr2a = " << cr2a << endl;  
   if ( cl2a == cr2a )  
      cout << "The complex numbers cl2a & cr2a are equal." << endl;  
   else  
      cout << "The complex numbers cl2a & cr2a are not equal." << endl;  
  
   cout << "The 2nd left-side complex number is cl2b = " << cl2b << endl;  
   cout << "The 2nd right-side complex number is cr2b = " << cr2b << endl;  
   if ( cl2b == cr2b )  
      cout << "The complex numbers cl2b & cr2b are equal." << endl;  
   else  
      cout << "The complex numbers cl2b & cr2b are not equal." << endl;  
   cout << endl;  
  
   // Example of the third member function  
   // type double compared with type complex<double>  
   double cl3a =3;  
   double cl3b =5;  
   complex <double> cr3a (3, 4 );  
   complex <double> cr3b (5,0 );  
  
   cout << "The 1st left-side complex number is cl3a = " << cl3a << endl;  
   cout << "The 1st right-side complex number is cr3a = " << cr3a << endl;  
   if ( cl3a == cr3a )  
      cout << "The complex numbers cl3a & cr3a are equal." << endl;  
   else  
      cout << "The complex numbers cl3a & cr3a are not equal." << endl;  
  
   cout << "The 2nd left-side complex number is cl3b = " << cl3b << endl;  
   cout << "The 2nd right-side complex number is cr3b = " << cr3b << endl;  
   if ( cl3b == cr3b )  
      cout << "The complex numbers cl3b & cr3b are equal." << endl;  
   else  
      cout << "The complex numbers cl3b & cr3b are not equal." << endl;  
   cout << endl;  
}  
```  
  
```Output  
The left-side complex number is cl1 = (2.59808,1.5)  
The 1st right-side complex number is cr1a = (2.59808,1.5)  
The 2nd right-side complex number is cr1b = (1,1.73205)  
The complex numbers cl1 & cr1a are equal.  
The complex numbers cl1 & cr1b are not equal.  
  
The 1st left-side complex number is cl2a = (3,4)  
The 1st right-side complex number is cr2a = 3  
The complex numbers cl2a & cr2a are not equal.  
The 2nd left-side complex number is cl2b = (5,0)  
The 2nd right-side complex number is cr2b = 5  
The complex numbers cl2b & cr2b are equal.  
  
The 1st left-side complex number is cl3a = 3  
The 1st right-side complex number is cr3a = (3,4)  
The complex numbers cl3a & cr3a are not equal.  
The 2nd left-side complex number is cl3b = 5  
The 2nd right-side complex number is cr3b = (5,0)  
The complex numbers cl3b & cr3b are equal.  
```  
  
##  <a name="op_gt_gt"></a>operátor&gt;&gt;  
 Extrahuje komplexní hodnoty ze vstupního datového proudu.  
  
```  
 
template <class Type, class Elem, class Traits>  
basic_istream<Elem, Traits>& operator>>(
   basic_istream<Elem, Traits>& Istr,  
   complex<Type>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `Istr`  
 Vstupní datový proud, ze které je extrahován komplexního čísla.  
  
 `right`  
 Počet komplexní rozbalený ze vstupního datového proudu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Načte hodnotu zadaného čísla komplexní z `Istr` a vrátí ji do `right`.  
  
### <a name="remarks"></a>Poznámky  
 Jsou platné vstupní formáty  
  
- *(skutečné část, pomyslná část)*  
  
- *(skutečné část)*  
  
- *skutečné část*  
  
### <a name="example"></a>Příklad  
  
```cpp  
// complex_op_extract.cpp  
// compile with: /EHsc  
#include <complex>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   double pi = 3.14159265359;  
  
   complex <double> c2;  
  
   cout << "Input a complex number ( try: 2.0 ): ";  
   cin >> c2;  
   cout << c2 << endl;  
}  
```  
  
```Output  
  
2.0  
  
```  
  
## <a name="see-also"></a>Viz také  
 [\<komplexní >](../standard-library/complex.md)
