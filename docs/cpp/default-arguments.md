---
title: Výchozí argumenty
ms.date: 11/04/2016
helpviewer_keywords:
- arguments [C++], function
- function declarators
- functions [C++], default arguments
- declaring functions [C++], declarators
- default arguments
- arguments [C++], default
- defaults [C++], arguments
ms.assetid: d32cf516-05cb-4d4d-b169-92f5649fdfa2
ms.openlocfilehash: 5ffc0301e7a89a379a2ea1eda9a113276df7a88e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50528918"
---
# <a name="default-arguments"></a>Výchozí argumenty

V mnoha případech obsahují funkce argumenty, které jsou tak zřídka používané, že bude stačit výchozí hodnota. Zařízení výchozího argumentu umožňuje zadání pouze těch argumentů funkce, které mají v daném volání význam. Pro ilustraci tohoto konceptu Uvažujme příklad uvedený v [přetížení funkce](../cpp/function-overloading.md).

```cpp
// Prototype three print functions.
int print( char *s );                  // Print a string.
int print( double dvalue );            // Print a double.
int print( double dvalue, int prec );  // Print a double with a
//  given precision.
```

V mnoha aplikacích mohou být pro `prec` poskytnuty přiměřené výchozí hodnoty, což eliminuje potřebu dvou funkcí:

```cpp
// Prototype two print functions.
int print( char *s );                    // Print a string.
int print( double dvalue, int prec=2 );  // Print a double with a
//  given precision.
```

Provádění `print` funkce se mírně změní tak, aby odrážely skutečnost, že existuje pouze jedna funkce pro typ **double**:

```cpp
// default_arguments.cpp
// compile with: /EHsc /c

// Print a double in specified precision.
//  Positive numbers for precision indicate how many digits
//  precision after the decimal point to show. Negative
//  numbers for precision indicate where to round the number
//  to the left of the decimal point.

#include <iostream>
#include <math.h>
using namespace std;

int print( double dvalue, int prec ) {
   // Use table-lookup for rounding/truncation.
   static const double rgPow10[] = {
      10E-7, 10E-6, 10E-5, 10E-4, 10E-3, 10E-2, 10E-1, 10E0,
         10E1,  10E2,  10E3,  10E4, 10E5,  10E6
   };
   const int iPowZero = 6;
   // If precision out of range, just print the number.
   if( prec >= -6 && prec <= 7 )
      // Scale, truncate, then rescale.
      dvalue = floor( dvalue / rgPow10[iPowZero - prec] ) *
      rgPow10[iPowZero - prec];
   cout << dvalue << endl;
   return cout.good();
}
```

K vyvolání nové funkce `print` je třeba použít následující kód:

```cpp
print( d );    // Precision of 2 supplied by default argument.
print( d, 0 ); // Override default argument to achieve other
//  results.
```

Při použití výchozích argumentů si pamatujte tyto body:

- Výchozí argumenty jsou používány pouze ve voláních funkce, kde jsou vynechány koncové argumenty – musejí to být poslední argumenty. Proto je následující kód neplatný:

    ```cpp
    int print( double dvalue = 0.0, int prec );
    ```

- Výchozí argument nelze předefinovat v pozdější deklaraci, dokonce ani v případě, kdy je opětovná definice totožná s původní. Proto následující kód generuje chybu:

    ```cpp
    // Prototype for print function.
    int print( double dvalue, int prec = 2 );

    ...

    // Definition for print function.
    int print( double dvalue, int prec = 2 )
    {
    ...
    }
    ```

   Problém s tímto kódem je, že deklarace funkce v definici předefinuje výchozí argument pro `prec`.

- Pozdějšími deklaracemi lze přidat další výchozí argumenty.

- Pro ukazatele na funkce lze zadat výchozí argumenty. Příklad:

    ```cpp
    int (*pShowIntVal)( int i = 0 );
    ```