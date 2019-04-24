---
title: Chyba kompilátoru C2333
ms.date: 11/04/2016
f1_keywords:
- C2333
helpviewer_keywords:
- C2333
ms.assetid: 2636fc1e-d3e7-4e68-8628-3c81a99ba813
ms.openlocfilehash: e9119a8375a276a59cbf3a6db9541f6ccaef5122
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62300817"
---
# <a name="compiler-error-c2333"></a>Chyba kompilátoru C2333

'function': Chyba v deklaraci funkce; tělo funkce se přeskočí

K této chybě dochází po další chyba pro členské funkce definované uvnitř své třídy.

Následující ukázka generuje C2333:

```
// C2333.cpp
struct s1 {
   s1(s1) {}   // C2333
};
```