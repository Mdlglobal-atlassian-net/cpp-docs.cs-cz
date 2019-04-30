---
title: Chyba kompilátoru C2379
ms.date: 11/04/2016
f1_keywords:
- C2379
helpviewer_keywords:
- C2379
ms.assetid: 37dc3015-a4af-4341-bbf3-da6150df7e51
ms.openlocfilehash: 1b3256efb6c0ff8236ba80a9ac681780f34fa8dd
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/24/2019
ms.locfileid: "64345640"
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