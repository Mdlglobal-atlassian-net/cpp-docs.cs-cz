---
title: protected (C++)
ms.date: 11/04/2016
f1_keywords:
- protected_cpp
helpviewer_keywords:
- protected keyword [C++], member access
- protected keyword [C++]
ms.assetid: 863d299f-fc0d-45d5-a1a7-bd24b7778a93
ms.openlocfilehash: 79ca081726c1f26a251763e2533ade730f075e2f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317267"
---
# <a name="protected-c"></a>protected (C++)

## <a name="syntax"></a>Syntaxe

```
protected:
   [member-list]
protected base-class
```

## <a name="remarks"></a>Poznámky

Klíčové slovo **protected** určuje přístup ke členům třídy v *seznamu členů* až k dalšímu specifikátoru přístupu (**veřejné** mu nebo **soukromému)** nebo ke konci definice třídy. Členy třídy deklarované jako **chráněné** mohou používat pouze následující:

- členskými funkcemi třídy, která původně deklarovala tyto členy,

- přáteli třídy, která původně deklarovala tyto členy,

- třídami odvozenými s veřejnou nebo chráněnou přístupností z této třídy, která původně deklarovala tyto členy,

- přímými soukromě odvozenými třídami, které mají také soukromý přístup k chráněným členům.

Při předcházejícím názvu základní třídy **chráněné** klíčové slovo určuje, že veřejné a chráněné členy základní třídy jsou chráněni členy jeho odvozené třídy.

Chráněné členy nejsou tak soukromé jako **soukromé** členy, které jsou přístupné pouze pro členy třídy, ve kterém jsou deklarovány, ale nejsou tak veřejné jako **veřejné** členy, které jsou přístupné v libovolné funkci.

Chráněné členy, které jsou také deklarovány jako **statické** jsou přístupné pro všechny přítele nebo členské funkce odvozené třídy. Chráněné členy, které nejsou deklarovány jako **statické,** jsou přístupné přátelům a členským funkcím v odvozené třídě pouze pomocí ukazatele, odkazu nebo objektu odvozené třídy.

Související informace naleznete [v tématu friend](../cpp/friend-cpp.md), [public](../cpp/public-cpp.md), [private](../cpp/private-cpp.md)a member-access table in Controlling Access to [Class Members](member-access-control-cpp.md).

## <a name="clr-specific"></a>Specifické pro možnost /clr

V typech CLR mohou klíčová slova specifikátoru přístupu Jazyka C++ (**veřejné**, **soukromé**a **chráněné**) ovlivnit viditelnost typů a metod s ohledem na sestavení. Další informace naleznete [v tématu Členské řízení přístupu](member-access-control-cpp.md).

> [!NOTE]
> Soubory zkompilované s [/LN](../build/reference/ln-create-msil-module.md) nejsou tímto chováním ovlivněny. V tomto případě budou všechny spravované třídy (veřejné nebo soukromé) viditelné.

## <a name="end-clr-specific"></a>Specifické pro možnost END /clr

## <a name="example"></a>Příklad

```cpp
// keyword_protected.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;
class X {
public:
   void setProtMemb( int i ) { m_protMemb = i; }
   void Display() { cout << m_protMemb << endl; }
protected:
   int  m_protMemb;
   void Protfunc() { cout << "\nAccess allowed\n"; }
} x;

class Y : public X {
public:
   void useProtfunc() { Protfunc(); }
} y;

int main() {
   // x.m_protMemb;         error, m_protMemb is protected
   x.setProtMemb( 0 );   // OK, uses public access function
   x.Display();
   y.setProtMemb( 5 );   // OK, uses public access function
   y.Display();
   // x.Protfunc();         error, Protfunc() is protected
   y.useProtfunc();      // OK, uses public access function
                        // in derived class
}
```

## <a name="see-also"></a>Viz také

[Řízení přístupu ke členům třídy](member-access-control-cpp.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)
