---
title: Upozornění (úroveň 1) C4010 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4010
dev_langs:
- C++
helpviewer_keywords:
- C4010
ms.assetid: d607a9ff-8f8f-45c0-b07b-3b2f439e5485
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 52449689d329cee45cc69b63c315ce9335befbe0
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46073095"
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