---
title: Upozornění kompilátoru (úroveň 1) C4010
ms.date: 11/04/2016
f1_keywords:
- C4010
helpviewer_keywords:
- C4010
ms.assetid: d607a9ff-8f8f-45c0-b07b-3b2f439e5485
ms.openlocfilehash: 6045d49ee34f837ad9f22bac5b2b43b75a998f7c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80164687"
---
# <a name="compiler-warning-level-1-c4010"></a>Upozornění kompilátoru (úroveň 1) C4010

Jednořádkový komentář obsahuje znak pro pokračování řádku.

Jednořádkový komentář, který je představený pomocí//, obsahuje zpětné lomítko (\\), které slouží jako znak pro pokračování řádku. Kompilátor považuje další řádek za pokračování a považuje ho za komentář.

Některé editory orientované na syntax neoznačují řádek za znakem pokračování jako komentář. Ignorovat barvy syntaxe na všech řádcích, které způsobují toto upozornění.

Následující ukázka generuje C4010:

```cpp
// C4010.cpp
// compile with: /WX
int main() {
   // the next line is also a comment because of the backslash \
   int a = 3; // C4010
   a++;
}
```
