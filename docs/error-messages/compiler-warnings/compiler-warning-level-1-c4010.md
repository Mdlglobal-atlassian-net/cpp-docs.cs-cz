---
title: Kompilátor upozornění (úroveň 1) C4010
ms.date: 11/04/2016
f1_keywords:
- C4010
helpviewer_keywords:
- C4010
ms.assetid: d607a9ff-8f8f-45c0-b07b-3b2f439e5485
ms.openlocfilehash: 40c6724daf17c1c0b546bb7bc64bb704f732e8d6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62386548"
---
# <a name="compiler-warning-level-1-c4010"></a>Kompilátor upozornění (úroveň 1) C4010

jednořádkový komentář obsahuje znak pro pokračování řádku

Jednořádkový komentář, který je zavedený / /, obsahuje zpětné lomítko (\\), který slouží jako znak pro pokračování řádku. Kompilátor považuje další řádek pokračování a zpracovává jako komentář.

Některé syntaxe orientovaný editory neindikuje řádek následující znak pro pokračování jako komentář. Ignorujte na řádcích, způsobující toto upozornění barevné zvýrazňování syntaxe.

Následující ukázka generuje C4010:

```
// C4010.cpp
// compile with: /WX
int main() {
   // the next line is also a comment because of the backslash \
   int a = 3; // C4010
   a++;
}
```