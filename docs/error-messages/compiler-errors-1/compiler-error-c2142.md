---
title: Chyba kompilátoru C2142
ms.date: 11/04/2016
f1_keywords:
- C2142
helpviewer_keywords:
- C2142
ms.assetid: d0dbe10e-0952-49a4-8b33-e82fb7558b19
ms.openlocfilehash: eda60204e07fd025a8c62b19de70e8204f9f80f1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50502008"
---
# <a name="compiler-error-c2142"></a>Chyba kompilátoru C2142

deklarace funkce se liší, parametry proměnné jsou zadané jenom v jednom z nich

Jedna deklarace funkce obsahuje seznam parametrů proměnných. Další deklarace je nepodporuje. ANSI jazyka C ([/Za](../../build/reference/za-ze-disable-language-extensions.md)) pouze.

Následující ukázka generuje C2142:

```
// C2142.c
// compile with: /Za /c
void func();
void func( int, ... );   // C2142
void func2( int, ... );   // OK
```