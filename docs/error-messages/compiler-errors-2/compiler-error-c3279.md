---
title: Chyba kompilátoru C3279 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3279
dev_langs:
- C++
helpviewer_keywords:
- C3279
ms.assetid: 639afc20-984c-4a95-be35-8bf9409f02d5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 89c537da9bcf91e7774353cc1516a4c44e28649c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46056765"
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