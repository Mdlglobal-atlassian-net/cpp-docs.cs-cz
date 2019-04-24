---
title: Chyba kompilátoru C3179
ms.date: 11/04/2016
f1_keywords:
- C3179
helpviewer_keywords:
- C3179
ms.assetid: 60d7e41b-25fd-48ac-8b79-830c062f4dcd
ms.openlocfilehash: a5c92e8a776e318e732448ba31beedef946d9f41
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62174065"
---
# <a name="compiler-error-c3179"></a>Chyba kompilátoru C3179

Nepojmenované spravované nebo typ WinRT není povolený.

Všechny CLR a WinRT tříd a struktur musí mít názvy.

Následující ukázka generuje C3179 a ukazuje, jak ho opravit:

```
// C3179a.cpp
// compile with: /clr /c
typedef value struct { // C3179
// try the following line instead
// typedef value struct MyStruct {
   int i;
} V;
```
