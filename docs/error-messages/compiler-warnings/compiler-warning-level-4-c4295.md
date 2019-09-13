---
title: Upozornění kompilátoru (úroveň 4) C4295
ms.date: 01/09/2018
f1_keywords:
- C4295
helpviewer_keywords:
- C4295
ms.assetid: 20dbff85-9f62-4ca3-8fe9-079d4512006d
ms.openlocfilehash: 5e8b546e4eb4b60197db504382b3230e779b1dec
ms.sourcegitcommit: effb516760c0f956c6308eeded48851accc96b92
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70924854"
---
# <a name="compiler-warning-level-4-c4295"></a>Upozornění kompilátoru (úroveň 4) C4295

> '*Array*': pole je příliš malé pro vložení ukončujícího znaku null

Pole bylo inicializováno, ale poslední znak v poli není null; přístup k poli jako řetězec může způsobit neočekávané výsledky.

## <a name="example"></a>Příklad

Následující ukázka generuje C4295. Chcete-li tento problém vyřešit, můžete deklarovat větší velikost pole, pro uložení ukončující hodnoty null z inicializačního řetězce, nebo můžete použít seznam inicializátorů pole, aby záměr vymazal, že se jedná o pole `char`, nikoli řetězec zakončený hodnotou null.

```C
// C4295.c
// compile with: /W4

int main() {
   char a[3] = "abc";           // C4295
   char b[3] = {'d', 'e', 'f'}; // No warning
   a[0] = b[2];
}
```
