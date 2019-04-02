---
title: Chyba kompilátoru C3612
ms.date: 11/04/2016
f1_keywords:
- C3612
helpviewer_keywords:
- C3612
ms.assetid: aa6e3a2b-4afa-481c-98c1-1b6d1f82f869
ms.openlocfilehash: ab18381d3f263e3207662e1667ac5c835983412f
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2019
ms.locfileid: "58781403"
---
# <a name="compiler-error-c3612"></a>Chyba kompilátoru C3612

'type': zapečetěná třída nemůže být abstraktní

Typy definované pomocí `value` jsou zapečetěné. ve výchozím nastavení, a pokud implementuje všechny metody své základní je abstraktní třídu. Zapečetěná abstraktní třída nemůže být základní třídu ani se dá vytvořit instance.

Další informace najdete v tématu [třídy a struktury](../../extensions/classes-and-structs-cpp-component-extensions.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C3612:

```
// C3612.cpp
// compile with: /clr /c
value struct V: public System::ICloneable {};   // C3612

// OK
value struct V2: public System::ICloneable {
   Object^ Clone();
};
```