---
title: Proměnlivé datové členy (C++)
ms.date: 11/04/2016
f1_keywords:
- mutable_cpp
helpviewer_keywords:
- mutable keyword [C++]
ms.assetid: ebe89746-3d36-43a8-8d69-f426af23f551
ms.openlocfilehash: db3a9594a77a9ada971213eaea74a9842bd96a54
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179338"
---
# <a name="mutable-data-members-c"></a>Proměnlivé datové členy (C++)

Toto klíčové slovo lze použít pouze na nestatické a nekonstantní datové členy třídy. Pokud je datový člen deklarovaný jako **mutable**, je právnímu tomuto datovému členovi přiřazena hodnota z **konstantní** členské funkce.

## <a name="syntax"></a>Syntaxe

```
mutable member-variable-declaration;
```

## <a name="remarks"></a>Poznámky

Například následující kód bude zkompilován bez chyby, protože `m_accessCount` byl deklarován jako **proměnlivý**, a lze jej proto upravit pomocí `GetFlag`, i když `GetFlag` je členská funkce const.

```cpp
// mutable.cpp
class X
{
public:
   bool GetFlag() const
   {
      m_accessCount++;
      return m_flag;
   }
private:
   bool m_flag;
   mutable int m_accessCount;
};

int main()
{
}
```

## <a name="see-also"></a>Viz také

[Klíčová slova](../cpp/keywords-cpp.md)
