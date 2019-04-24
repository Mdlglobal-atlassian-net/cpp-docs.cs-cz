---
title: Chyba kompilátoru C2005
ms.date: 11/04/2016
f1_keywords:
- C2005
helpviewer_keywords:
- C2005
ms.assetid: 090530ed-e0ec-4358-833a-ca24260e7ffe
ms.openlocfilehash: 49d0375d5733410d728797d2a881075377b33ba6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62208996"
---
# <a name="compiler-error-c2005"></a>Chyba kompilátoru C2005

\#řádku se očekávalo číslo řádku, nalezeno "token"

`#line` – Direktiva musí být následován znakem čísla řádku.

Následující ukázka generuje C2005:

```
// C2005.cpp
int main() {
   int i = 0;
   #line i   // C2005
}
```

Možná řešení:

```
// C2005b.cpp
int main() {
   int i = 0;
   #line 0
}
```