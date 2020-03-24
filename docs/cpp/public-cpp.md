---
title: public (C++)
ms.date: 11/04/2016
f1_keywords:
- public_cpp
helpviewer_keywords:
- public keyword [C++]
ms.assetid: f3e10a59-39f6-4bcd-827e-3e99f8f89497
ms.openlocfilehash: dd45430543ead7258096be8f3d8cef0141f27b4e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179189"
---
# <a name="public-c"></a>public (C++)

## <a name="syntax"></a>Syntaxe

```
public:
   [member-list]
public base-class
```

## <a name="remarks"></a>Poznámky

Když předchází seznam členů třídy, klíčové slovo **Public** určuje, že tyto členy jsou přístupné z jakékoli funkce. To platí pro všechny členy deklarované až k dalšímu specifikátoru přístupu nebo ke konci třídy.

Pokud před názvem základní třídy, klíčové slovo **Public** určuje, že veřejné a chráněné členy základní třídy jsou veřejné a chráněné členy, v uvedeném pořadí, z odvozené třídy.

Výchozí přístup členů ve třídě je privátní. Výchozí přístup členů ve struktuře nebo sjednocení je veřejný.

Výchozí přístup základní třídy je privátní pro třídy a veřejné pro struktury. Sjednocení nemohou mít základní třídy.

Další informace naleznete v tématech [Private](../cpp/private-cpp.md), [Protected](../cpp/protected-cpp.md), [Friend](../cpp/friend-cpp.md)a tabulka přístupu členů v tématu [řízení přístupu ke členům třídy](member-access-control-cpp.md).

## <a name="clr-specific"></a>Specifické pro možnost /clr

V typech CLR mohou C++ klíčová slova specifikátoru přístupu (**Public**, **Private**a **Protected**) ovlivnit viditelnost typů a metod s ohledem na sestavení. Další informace najdete v tématu [členské Access Control](member-access-control-cpp.md).

> [!NOTE]
>  Tímto chováním nejsou ovlivněny soubory zkompilované pomocí [/ln](../build/reference/ln-create-msil-module.md) . V tomto případě budou všechny spravované třídy (veřejné nebo soukromé) viditelné.

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
