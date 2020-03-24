---
title: Volání funkcí (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- function calls, C++ functions
- functions [C++], calling
- operator overloading [C++], function calls
- function overloading [C++], function-call operator
- function calls, operator
- operators [C++], overloading
- operator overloading [C++], examples
- function call operator ()
ms.assetid: 5094254a-045b-46f7-8653-69bc91e80dce
ms.openlocfilehash: 6c7326b0f9c9592cb2b3be973a5ba1747a2015a0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179806"
---
# <a name="function-call-c"></a>Volání funkcí (C++)

Operátor volání funkce je při vyvolání pomocí závorek binárním operátorem.

## <a name="syntax"></a>Syntaxe

```
primary-expression ( expression-list )
```

## <a name="remarks"></a>Poznámky

V tomto kontextu je `primary-expression` prvním operandem a `expression-list`, případně prázdný seznam argumentů, je druhý operand. Operátor volání funkce se používá pro operace, které vyžadují více parametrů. To funguje, protože `expression-list` je seznam místo jednoho operandu. Operátor volání funkce musí být nestatická členská funkce.

Operátor volání funkce nemění v případě přetížení způsob, jakým jsou funkce volány. Místo toho upravuje, jak se operátor interpretuje při použití na objekty daného typu třídy. Například následující kód by obvykle neměl význam:

```cpp
Point pt;
pt( 3, 2 );
```

Při použití vhodného přetíženého operátoru volání funkce se ale tato syntaxe dá použít k posunu `x` souřadnici 3 jednotky a `y` souřadnicích 2 jednotky. Následující kód ukazuje takovou definici:

```cpp
// function_call.cpp
class Point
{
public:
    Point() { _x = _y = 0; }
    Point &operator()( int dx, int dy )
        { _x += dx; _y += dy; return *this; }
private:
    int _x, _y;
};

int main()
{
   Point pt;
   pt( 3, 2 );
}
```

Je třeba poznamenat, že operátor volání funkce je použit na název objektu, nikoli na název funkce.

Operátor volání funkce můžete také přetížit pomocí ukazatele na funkci (místo samotné funkce).

```cpp
typedef void(*ptf)();
void func()
{
}
struct S
{
   operator ptf()
   {
      return func;
   }
};

int main()
{
   S s;
   s();//operates as s.operator ptf()()
}
```

## <a name="see-also"></a>Viz také

[Přetížení operátoru](../cpp/operator-overloading.md)
