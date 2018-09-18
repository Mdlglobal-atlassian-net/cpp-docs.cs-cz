---
title: Funkce volání (C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0d583609a1013620384e7e938182403fb5c694fb
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46081390"
---
# <a name="function-call-c"></a>Volání funkcí (C++)

Operátor volání funkce je při vyvolání pomocí závorek binárním operátorem.

## <a name="syntax"></a>Syntaxe

```
primary-expression ( expression-list )
```

## <a name="remarks"></a>Poznámky

V tomto kontextu `primary-expression` je první operand a `expression-list`, případně prázdný seznam argumentů, je druhý operand. Operátor volání funkce se používá pro operace, které vyžadují více parametrů. Tento postup funguje, protože `expression-list` je seznam místo jediného operandu. Operátor volání funkce musí být nestatická členská funkce.

Operátor volání funkce nemění v případě přetížení způsob, jakým jsou funkce volány. Místo toho upravuje, jak se operátor interpretuje při použití na objekty daného typu třídy. Například následující kód by obvykle neměl význam:

```cpp
Point pt;
pt( 3, 2 );
```

Zadaný operátor odpovídající přetížená volání funkce, ale tato syntaxe umožňuje posun `x` koordinovat 3 jednotky a `y` koordinovat 2 jednotky. Následující kód ukazuje takovou definici:

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

Můžete také přetížit operátor volání funkce pomocí ukazatele na funkci (spíše než samotné funkce).

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

## <a name="see-also"></a>Viz také:

[Přetížení operátoru](../cpp/operator-overloading.md)