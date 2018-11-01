---
title: public (C++)
ms.date: 11/04/2016
f1_keywords:
- public_cpp
helpviewer_keywords:
- public keyword [C++]
ms.assetid: f3e10a59-39f6-4bcd-827e-3e99f8f89497
ms.openlocfilehash: 24cc4dd3cd7e0c893664339e7ad83383839b0b11
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50600366"
---
# <a name="public-c"></a>public (C++)

## <a name="syntax"></a>Syntaxe

```
public:
   [member-list]
public base-class
```

## <a name="remarks"></a>Poznámky

Při předchozím seznam členů třídy **veřejné** – klíčové slovo určuje, že tyto členy jsou přístupné z jakékoli funkce. To platí pro všechny členy deklarované až do dalšího specifikátoru přístupu nebo na konci třídy.

Když předchází název základní třídy **veřejné** – klíčové slovo určuje, že veřejné a chráněné členy základní třídy jsou veřejné a chráněné členy, resp. odvozené třídy.

Přístup k výchozím členů ve třídě je privátní. Přístup k výchozím členů struktury nebo sjednocení je přístup public.

Pro třídy privátních a veřejných pro struktury je výchozí přístup základní třídy. Sjednocení nemohou mít základní třídy.

Další informace najdete v tématu [privátní](../cpp/private-cpp.md), [chráněné](../cpp/protected-cpp.md), [friend](../cpp/friend-cpp.md)a v tabulce přístupu ke členům v [řízení přístupu ke členům třídy](member-access-control-cpp.md) .

## <a name="clr-specific"></a>Specifické pro možnost /clr

U typů modulu CLR, klíčová slova specifikátoru přístupu jazyka C++ (**veřejné**, **privátní**, a **chráněné**) může ovlivnit viditelnost typů a metod s ohledem na sestavení. Další informace najdete v tématu [řízení přístupu ke členu](member-access-control-cpp.md).

> [!NOTE]
>  Souborů zkompilovaných pomocí [/LN](../build/reference/ln-create-msil-module.md) toto chování netýká. V tomto případě budou všechny spravované třídy (veřejné nebo soukromé) viditelné.

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

## <a name="see-also"></a>Viz také:

[Řízení přístupu ke členům třídy](member-access-control-cpp.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)