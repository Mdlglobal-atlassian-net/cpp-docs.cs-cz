---
title: Chyba kompilátoru C2379
ms.date: 11/04/2016
f1_keywords:
- C2379
helpviewer_keywords:
- C2379
ms.assetid: 37dc3015-a4af-4341-bbf3-da6150df7e51
ms.openlocfilehash: 1b3256efb6c0ff8236ba80a9ac681780f34fa8dd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50643843"
---
# <a name="compiler-error-c2379"></a>Chyba kompilátoru C2379

počet formálních parametrů je jiného typu, pokud se zobrazí výzva

Typ zadaného parametru není kompatibilní, prostřednictvím výchozí povýšení typu v předchozí deklaraci. Jedná se o chybu ve standardu ANSI C ([/Za](../../build/reference/za-ze-disable-language-extensions.md)) a upozornění s rozšířeními společnosti Microsoft (**/Ze**).

Následující ukázka generuje C2379:

```
// C2379.c
// compile with: /Za
void func();
void func(char);   // C2379, char promotes to int
```