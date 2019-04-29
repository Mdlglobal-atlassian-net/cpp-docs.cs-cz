---
title: Chyba kompilátoru C2055
ms.date: 11/04/2016
f1_keywords:
- C2055
helpviewer_keywords:
- C2055
ms.assetid: 6cec79cc-6bec-443f-9897-fbf5452718c7
ms.openlocfilehash: 3c198168b4445e619148e5611621fa3ddba95d6b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62408784"
---
# <a name="compiler-error-c2055"></a>Chyba kompilátoru C2055

Očekával se seznam formálních parametrů, ne seznam typů

Definice funkce obsahuje seznam parametrů typu namísto seznamu formálních parametrů. ANSI C vyžaduje formálních parametrů s názvem, pokud se nejedná o typ void nebo třemi tečkami (`...`).

Následující ukázka generuje C2055:

```
// C2055.c
// compile with: /c
void func(int, char) {}  // C2055
void func (int i, char c) {}   // OK
```