---
title: Chyba kompilátoru C3279
ms.date: 11/04/2016
f1_keywords:
- C3279
helpviewer_keywords:
- C3279
ms.assetid: 639afc20-984c-4a95-be35-8bf9409f02d5
ms.openlocfilehash: 3025dbf7c6bf4701218c2d9a956cae26d7180848
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757602"
---
# <a name="compiler-error-c3279"></a>Chyba kompilátoru C3279

částečné a explicitní specializace a explicitní vytváření instancí šablon tříd deklarovaných v oboru názvů CLI jsou zakázané.

Obor názvů `cli` je definován Microsoftem a obsahuje pseudo šablony. Kompilátor společnosti C++ Microsoft nepovoluje uživatelsky definované, částečné a explicitní specializace a explicitní vytváření instancí šablon tříd v tomto oboru názvů.

Následující ukázka generuje C3279:

```cpp
// C3279.cpp
// compile with: /clr
namespace cli {
   template <> ref class array<int> {};   // C3279
   template <typename T> ref class array<T, 2> {};   // C3279
}
```
