---
title: public (C++)
ms.date: 11/04/2016
f1_keywords:
- public_cpp
helpviewer_keywords:
- public keyword [C++]
ms.assetid: f3e10a59-39f6-4bcd-827e-3e99f8f89497
ms.openlocfilehash: bf8293c6a6cf12154b02979de08035807991052c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376055"
---
# <a name="public-c"></a>public (C++)

## <a name="syntax"></a>Syntaxe

```
public:
   [member-list]
public base-class
```

## <a name="remarks"></a>Poznámky

Při předcházejícím seznamu členů třídy **veřejné** klíčové slovo určuje, že tyto členy jsou přístupné z libovolné funkce. To platí pro všechny členy deklarované až do dalšího specifikátoru přístupu nebo na konci třídy.

Při předcházejícím názvu základní třídy **veřejné** klíčové slovo určuje, že veřejné a chráněné členy základní třídy jsou veřejné a chráněné členy odvozené třídy.

Výchozí přístup členů ve třídě je soukromý. Výchozí přístup členů ve struktuře nebo sjednocení je veřejný.

Výchozí přístup základní třídy je soukromý pro třídy a veřejné pro struktury. Sjednocení nemůže mít základní třídy.

Další informace naleznete v [tématu private](../cpp/private-cpp.md), [protected](../cpp/protected-cpp.md), [friend](../cpp/friend-cpp.md)a member-access table in Controlling Access to [Class Members](member-access-control-cpp.md).

## <a name="clr-specific"></a>Specifické pro možnost /clr

V typech CLR mohou klíčová slova specifikátoru přístupu Jazyka C++ (**veřejné**, **soukromé**a **chráněné**) ovlivnit viditelnost typů a metod s ohledem na sestavení. Další informace naleznete [v tématu Členské řízení přístupu](member-access-control-cpp.md).

> [!NOTE]
> Soubory zkompilované s [/LN](../build/reference/ln-create-msil-module.md) nejsou tímto chováním ovlivněny. V tomto případě budou všechny spravované třídy (veřejné nebo soukromé) viditelné.

## <a name="end-clr-specific"></a>Specifické pro možnost END /clr

## <a name="example"></a>Příklad

```cpp
// keyword_public.cpp
class BaseClass {
public:
   int pubFunc() { return 0; }
};

class DerivedClass : public BaseClass {};

int main() {
   BaseClass aBase;
   DerivedClass aDerived;
   aBase.pubFunc();       // pubFunc() is accessible
                          //    from any function
   aDerived.pubFunc();    // pubFunc() is still public in
                          //    derived class
}
```

## <a name="see-also"></a>Viz také

[Řízení přístupu ke členům třídy](member-access-control-cpp.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)
