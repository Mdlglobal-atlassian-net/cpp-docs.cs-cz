---
title: Chyba kompilátoru C2666
ms.date: 11/04/2016
f1_keywords:
- C2666
helpviewer_keywords:
- C2666
ms.assetid: 78364d15-c6eb-439a-9088-e04a0176692b
ms.openlocfilehash: 4a1d46f3b000b5054564b05ca2c3c94a9e7b6398
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50479282"
---
# <a name="compiler-error-c2666"></a>Chyba kompilátoru C2666

'identifier': číslo přetížení má podobné převody

Přetížené funkce nebo operátor je nejednoznačný.   Seznam formálních parametrů může být příliš podobné pro kompilátor, aby se vyřešit nejednoznačnost.  Chcete-li vyřešit tuto chybu, je nutné explicitně přetypován jeden nebo více skutečných parametrů.

Následující ukázka generuje C2666:

```
// C2666.cpp
struct complex {
   complex(double);
};

void h(int,complex);
void h(double, double);

int main() {
   h(3,4);   // C2666
}
```

Tato chyba může být také generovány jako důsledek kompilátoru prací, které bylo provedeno pro Visual Studio .NET 2003:

- binární operátory a uživatelem definované převody na typy ukazatelů

- převod kvalifikace není stejná jako identita převodu

Pro binární operátory \<, >, \<= a > =, předaný parametr se teď implicitně převést na typ operandu Pokud typ parametru definuje operátor uživatelsky definovaný převod pro převod na typ operandu. Je nyní potenciál nejednoznačnost.

Kód, který je platný v aplikaci Visual Studio .NET 2003 a Visual Studio .NET verzí jazyka Visual C++ volání operátoru třídy explicitně pomocí syntaxe funkce.

## <a name="example"></a>Příklad

```
// C2666b.cpp
#include <string.h>
#include <stdio.h>

struct T
{
    T( const T& copy )
    {
        m_str = copy.m_str;
    }

    T( const char* str )
    {
        int iSize = (strlen( str )+ 1);
        m_str = new char[ iSize ];
        if (m_str)
            strcpy_s( m_str, iSize, str );
    }

    bool operator<( const T& RHS )
    {
        return m_str < RHS.m_str;
    }

    operator char*() const
    {
        return m_str;
    }

    char* m_str;
};

int main()
{
    T str1( "ABCD" );
    const char* str2 = "DEFG";

    // Error - Ambiguous call to operator<()
    // Trying to convert str1 to char* and then call
    // operator<( const char*, const char* )?
    //  OR
    // trying to convert str2 to T and then call
    // T::operator<( const T& )?

    if( str1 < str2 )   // C2666

    if ( str1.operator < ( str2 ) )   // Treat str2 as type T
        printf_s("str1.operator < ( str2 )\n");

    if ( str1.operator char*() < str2 )   // Treat str1 as type char*
        printf_s("str1.operator char*() < str2\n");
}
```

## <a name="example"></a>Příklad

Následující ukázka generuje C2666

```
// C2666c.cpp
// compile with: /c

enum E
{
    E_A,   E_B
};

class A
{
    int h(const E e) const {return 0; }
    int h(const int i) { return 1; }
    // Uncomment the following line to resolve.
    // int h(const E e) { return 0; }

    void Test()
    {
        h(E_A);   // C2666
        h((const int) E_A);
        h((int) E_A);
    }
};
```