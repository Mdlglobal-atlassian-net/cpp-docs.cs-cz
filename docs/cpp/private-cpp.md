---
title: private (C++)
ms.date: 11/04/2016
f1_keywords:
- private_cpp
helpviewer_keywords:
- private keyword [C++]
ms.assetid: 94e99983-46a5-4e21-800c-28f8a7c6a8ff
ms.openlocfilehash: d6dc1ca309c096a4f5e857ade3d7550749991f3f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366209"
---
# <a name="private-c"></a>private (C++)

## <a name="syntax"></a>Syntaxe

```
private:
   [member-list]
private base-class
```

## <a name="remarks"></a>Poznámky

Při předcházejícím seznamu členů třídy **private** klíčové slovo určuje, že tyto členy jsou přístupné pouze z členských funkcí a přátel třídy. To platí pro všechny členy deklarované až do dalšího specifikátoru přístupu nebo na konci třídy.

Při předcházejícím názvu základní třídy klíčové slovo **private** určuje, že veřejní a chránění členové základní třídy jsou soukromými členy odvozené třídy.

Výchozí přístup členů ve třídě je soukromý. Výchozí přístup členů ve struktuře nebo sjednocení je veřejný.

Výchozí přístup základní třídy je soukromý pro třídy a veřejné pro struktury. Sjednocení nemůže mít základní třídy.

Související informace naleznete [v tématu friend](../cpp/friend-cpp.md), [public](../cpp/public-cpp.md), [protected](../cpp/protected-cpp.md)a member-access table in Controlling Access to [Class Members](member-access-control-cpp.md).

## <a name="clr-specific"></a>Specifické pro možnost /clr

V typech CLR mohou klíčová slova specifikátoru přístupu Jazyka C++ (**veřejné**, **soukromé**a **chráněné**) ovlivnit viditelnost typů a metod s ohledem na sestavení. Další informace naleznete [v tématu Členské řízení přístupu](member-access-control-cpp.md).

> [!NOTE]
> Soubory zkompilované s [/LN](../build/reference/ln-create-msil-module.md) nejsou tímto chováním ovlivněny. V tomto případě budou všechny spravované třídy (veřejné nebo soukromé) viditelné.

## <a name="end-clr-specific"></a>Specifické pro možnost END /clr

## <a name="example"></a>Příklad

```cpp
// keyword_private.cpp
class BaseClass {
public:
   // privMem accessible from member function
   int pubFunc() { return privMem; }
private:
   void privMem;
};

class DerivedClass : public BaseClass {
public:
   void usePrivate( int i )
      { privMem = i; }   // C2248: privMem not accessible
                         // from derived class
};

class DerivedClass2 : private BaseClass {
public:
   // pubFunc() accessible from derived class
   int usePublic() { return pubFunc(); }
};

int main() {
   BaseClass aBase;
   DerivedClass aDerived;
   DerivedClass2 aDerived2;
   aBase.privMem = 1;     // C2248: privMem not accessible
   aDerived.privMem = 1;  // C2248: privMem not accessible
                          //    in derived class
   aDerived2.pubFunc();   // C2247: pubFunc() is private in
                          //    derived class
}
```

## <a name="see-also"></a>Viz také

[Řízení přístupu ke členům třídy](member-access-control-cpp.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)
