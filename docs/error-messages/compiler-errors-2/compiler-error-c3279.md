---
title: Chyba kompilátoru C3279
ms.date: 11/04/2016
f1_keywords:
- C3279
helpviewer_keywords:
- C3279
ms.assetid: 639afc20-984c-4a95-be35-8bf9409f02d5
ms.openlocfilehash: 72646d7611163748fe7e27ea6c78cd38426eb6ad
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2019
ms.locfileid: "65447810"
---
# <a name="compiler-error-c3279"></a>Chyba kompilátoru C3279

dílčí a explicitní specializace, jakož i explicitní vytváření instancí šablon tříd jsou deklarovány v oboru názvů cli jsou zakázané.

`cli` Obor názvů definovaný společností Microsoft a obsahuje pseudo šablony. Microsoft C++ kompilátoru neumožňuje definovaný uživatelem, dílčí a explicitní specializace a explicitní vytváření instancí šablon tříd v tomto oboru názvů.

Následující ukázka generuje C3279:

```
// C3279.cpp
// compile with: /clr
namespace cli {
   template <> ref class array<int> {};   // C3279
   template <typename T> ref class array<T, 2> {};   // C3279
}
```