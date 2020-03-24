---
title: protected (C++)
ms.date: 11/04/2016
f1_keywords:
- protected_cpp
helpviewer_keywords:
- protected keyword [C++], member access
- protected keyword [C++]
ms.assetid: 863d299f-fc0d-45d5-a1a7-bd24b7778a93
ms.openlocfilehash: 29f57eac7201ac0647275c70c539f9b2f28eb81b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179247"
---
# <a name="protected-c"></a>protected (C++)

## <a name="syntax"></a>Syntaxe

```
protected:
   [member-list]
protected base-class
```

## <a name="remarks"></a>Poznámky

Klíčové slovo **Protected** určuje přístup ke členům třídy v *seznamu Member-list* až k dalšímu specifikátoru přístupu (**veřejné** nebo **privátní**) nebo konci definice třídy. Členy třídy deklarované jako **chráněné** lze použít pouze následujícím způsobem:

- členskými funkcemi třídy, která původně deklarovala tyto členy,

- přáteli třídy, která původně deklarovala tyto členy,

- třídami odvozenými s veřejnou nebo chráněnou přístupností z této třídy, která původně deklarovala tyto členy,

- přímými soukromě odvozenými třídami, které mají také soukromý přístup k chráněným členům.

Před názvem základní třídy určuje klíčové slovo **Protected** , že veřejné a chráněné členy základní třídy jsou chráněni členy svých odvozených tříd.

Chránění členové **nejsou jako privátní členy,** které jsou přístupné pouze pro členy třídy, ve které jsou deklarovány, ale nejsou veřejné jako **veřejné** členy, které jsou přístupné v jakékoli funkci.

Chráněné členy, které jsou také deklarovány jako **static** , jsou přístupné všem přátelům nebo členským funkcím odvozené třídy. Chráněné členy, které nejsou deklarovány jako **static** , jsou přístupné pro přátele a členské funkce v odvozené třídě pouze prostřednictvím ukazatele na, odkaz na nebo objekt odvozené třídy.

Související informace naleznete v tématech [Friend](../cpp/friend-cpp.md), [Public](../cpp/public-cpp.md), [Private](../cpp/private-cpp.md)a tabulka přístupu členů v tématu [řízení přístupu ke členům třídy](member-access-control-cpp.md).

## <a name="clr-specific"></a>Specifické pro možnost /clr

V typech CLR mohou C++ klíčová slova specifikátoru přístupu (**Public**, **Private**a **Protected**) ovlivnit viditelnost typů a metod s ohledem na sestavení. Další informace najdete v tématu [členské Access Control](member-access-control-cpp.md).

> [!NOTE]
>  Tímto chováním nejsou ovlivněny soubory zkompilované pomocí [/ln](../build/reference/ln-create-msil-module.md) . V tomto případě budou všechny spravované třídy (veřejné nebo soukromé) viditelné.

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
