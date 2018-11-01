---
title: Proměnlivé datové členy (C++)
ms.date: 11/04/2016
f1_keywords:
- mutable_cpp
helpviewer_keywords:
- mutable keyword [C++]
ms.assetid: ebe89746-3d36-43a8-8d69-f426af23f551
ms.openlocfilehash: 8d592eb97f70bfc26c075317c57ec4d5c78e3956
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50514176"
---
# <a name="mutable-data-members-c"></a>Proměnlivé datové členy (C++)

Toto klíčové slovo lze použít pouze na nestatické a nekonstantní datové členy třídy. Pokud je datový člen deklarován **proměnlivé**, je pro přiřazení k tomuto datovému členu z hodnoty **const** členskou funkci.

## <a name="syntax"></a>Syntaxe

```
mutable member-variable-declaration;
```

## <a name="remarks"></a>Poznámky

Například následující kód se zkompiluje bez chyb protože `m_accessCount` byl deklarován jako **proměnlivé**a proto je možné upravovat prostřednictvím `GetFlag` i v případě, `GetFlag` je konstantní členskou funkci.

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

## <a name="see-also"></a>Viz také:

[Klíčová slova](../cpp/keywords-cpp.md)