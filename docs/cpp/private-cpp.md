---
title: private (C++)
ms.date: 11/04/2016
f1_keywords:
- private_cpp
helpviewer_keywords:
- private keyword [C++]
ms.assetid: 94e99983-46a5-4e21-800c-28f8a7c6a8ff
ms.openlocfilehash: 19ea551f625cac02e639753a976eddb7a5fa164b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50622271"
---
# <a name="private-c"></a>private (C++)

## <a name="syntax"></a>Syntaxe

```
private:
   [member-list]
private base-class
```

## <a name="remarks"></a>Poznámky

Při předchozím seznam členů třídy **privátní** – klíčové slovo určuje, že tyto členy jsou přístupné pouze členskými funkcemi a přáteli třídy. To platí pro všechny členy deklarované až do dalšího specifikátoru přístupu nebo na konci třídy.

Když předchází název základní třídy **privátní** – klíčové slovo určuje, že jsou veřejné a chráněné členy základní třídy soukromé členy odvozené třídy.

Přístup k výchozím členů ve třídě je privátní. Přístup k výchozím členů struktury nebo sjednocení je přístup public.

Pro třídy privátních a veřejných pro struktury je výchozí přístup základní třídy. Sjednocení nemohou mít základní třídy.

Související informace naleznete v tématu [friend](../cpp/friend-cpp.md), [veřejné](../cpp/public-cpp.md), [chráněné](../cpp/protected-cpp.md)a v tabulce přístupu ke členům v [řízení přístupu ke členům třídy](member-access-control-cpp.md).

## <a name="clr-specific"></a>Specifické pro možnost /clr

U typů modulu CLR, klíčová slova specifikátoru přístupu jazyka C++ (**veřejné**, **privátní**, a **chráněné**) může ovlivnit viditelnost typů a metod s ohledem na sestavení. Další informace najdete v tématu [řízení přístupu ke členu](member-access-control-cpp.md).

> [!NOTE]
>  Souborů zkompilovaných pomocí [/LN](../build/reference/ln-create-msil-module.md) toto chování netýká. V tomto případě budou všechny spravované třídy (veřejné nebo soukromé) viditelné.

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

## <a name="see-also"></a>Viz také:

[Řízení přístupu ke členům třídy](member-access-control-cpp.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)