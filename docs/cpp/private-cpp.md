---
title: private (C++)
ms.date: 11/04/2016
f1_keywords:
- private_cpp
helpviewer_keywords:
- private keyword [C++]
ms.assetid: 94e99983-46a5-4e21-800c-28f8a7c6a8ff
ms.openlocfilehash: 002a8ad2887bd711bc3654d8e8910e2bede889d4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80177557"
---
# <a name="private-c"></a>private (C++)

## <a name="syntax"></a>Syntaxe

```
private:
   [member-list]
private base-class
```

## <a name="remarks"></a>Poznámky

Pokud před seznamem členů třídy, klíčové slovo **Private** určuje, že tyto členy jsou přístupné pouze z členských funkcí a přátel třídy. To platí pro všechny členy deklarované až k dalšímu specifikátoru přístupu nebo ke konci třídy.

Před názvem základní třídy určuje klíčové slovo **Private** , že veřejné a chráněné členy základní třídy jsou soukromé členy odvozené třídy.

Výchozí přístup členů ve třídě je privátní. Výchozí přístup členů ve struktuře nebo sjednocení je veřejný.

Výchozí přístup základní třídy je privátní pro třídy a veřejné pro struktury. Sjednocení nemohou mít základní třídy.

Související informace naleznete v tématech [Friend](../cpp/friend-cpp.md), [Public](../cpp/public-cpp.md), [Protected](../cpp/protected-cpp.md)a tabulka přístupu členů v tématu [řízení přístupu ke členům třídy](member-access-control-cpp.md).

## <a name="clr-specific"></a>Specifické pro možnost /clr

V typech CLR mohou C++ klíčová slova specifikátoru přístupu (**Public**, **Private**a **Protected**) ovlivnit viditelnost typů a metod s ohledem na sestavení. Další informace najdete v tématu [členské Access Control](member-access-control-cpp.md).

> [!NOTE]
>  Tímto chováním nejsou ovlivněny soubory zkompilované pomocí [/ln](../build/reference/ln-create-msil-module.md) . V tomto případě budou všechny spravované třídy (veřejné nebo soukromé) viditelné.

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
