---
title: __super
ms.date: 11/04/2016
f1_keywords:
- __super_cpp
helpviewer_keywords:
- __super keyword [C++]
ms.assetid: f0957c31-9256-405b-b402-cad182404b5f
ms.openlocfilehash: b6f6a7e108224ab4c97893104c5d6c38d325fa42
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80160824"
---
# <a name="__super"></a>__super

**Specifické pro společnost Microsoft**

Umožňuje explicitně uvést, že je pro funkci, u které je prováděno přetížení, volána implementace základní funkce.

## <a name="syntax"></a>Syntaxe

```
__super::member_function();
```

## <a name="remarks"></a>Poznámky

Všechny dostupné metody základní třídy jsou ve fázi řešení přetížení zváženy a funkce, jež poskytne nejlepší výsledek, je ta, která je volána.

**__super** se může vyskytovat jenom v těle členské funkce.

**__super** nelze použít s deklarací using. Další informace najdete v tématu [použití deklarace](../cpp/using-declaration.md) .

Při zavedení [atributů](../windows/attributes/attributes-alphabetical-reference.md) , které vkládají kód, může váš kód obsahovat jednu nebo více základních tříd, jejichž názvy neznáte, ale obsahují metody, které chcete volat.

## <a name="example"></a>Příklad

```cpp
// deriv_super.cpp
// compile with: /c
struct B1 {
   void mf(int) {}
};

struct B2 {
   void mf(short) {}

   void mf(char) {}
};

struct D : B1, B2 {
   void mf(short) {
      __super::mf(1);   // Calls B1::mf(int)
      __super::mf('s');   // Calls B2::mf(char)
   }
};
```

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[Klíčová slova](../cpp/keywords-cpp.md)
