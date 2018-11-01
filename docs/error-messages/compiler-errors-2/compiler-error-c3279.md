---
title: Chyba kompilátoru C3279
ms.date: 11/04/2016
f1_keywords:
- C3279
helpviewer_keywords:
- C3279
ms.assetid: 639afc20-984c-4a95-be35-8bf9409f02d5
ms.openlocfilehash: 5f39510ee9ec0e717d675aa8b396405bc33b4ea1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50445003"
---
# <a name="compiler-error-c3279"></a>Chyba kompilátoru C3279

dílčí a explicitní specializace, jakož i explicitní vytváření instancí šablon tříd jsou deklarovány v oboru názvů cli jsou zakázané.

`cli` Obor názvů definovaný společností Microsoft a obsahuje pseudo šablony. Kompilátor Visual C++ nepovoluje definovaný uživatelem, dílčí a explicitní specializace a explicitní vytváření instancí šablon tříd v tomto oboru názvů.

Následující ukázka generuje C3279:

```
// C3279.cpp
// compile with: /clr
namespace cli {
   template <> ref class array<int> {};   // C3279
   template <typename T> ref class array<T, 2> {};   // C3279
}
```