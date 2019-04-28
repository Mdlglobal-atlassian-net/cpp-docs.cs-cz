---
title: Chyba kompilátoru C2011
ms.date: 11/04/2016
f1_keywords:
- C2011
helpviewer_keywords:
- C2011
ms.assetid: 992c9d51-e850-4d53-b86b-02e73b38249c
ms.openlocfilehash: 14969c9cdf4b00844d2001bf4817ea7ffc9bfba6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62361552"
---
# <a name="compiler-error-c2011"></a>Chyba kompilátoru C2011

'identifier': "typ" předefinování typu

Identifikátor již byl definován jako `type`. Zkontrolujte redefinice identifikátor.

Může také získáte C2011 Pokud importujete soubor hlaviček nebo do stejného souboru knihovny typů více než jednou. Zabránit vícenásobnému zahrnutí typy definované v souboru hlaviček, zahrnují použití chrání nebo `#pragma` [po](../../preprocessor/once.md) direktivy v souboru hlaviček.

Pokud je potřeba najít počáteční deklaraci typu Předefinovaná, můžete použít [/P](../../build/reference/p-preprocess-to-a-file.md) předán kompilátoru příznak pro generování předzpracovaného výstupu kompilátoru. Textové vyhledávací nástroje můžete použít k vyhledání instance identifikátoru Předefinovaná do výstupního souboru.

Následující ukázka generuje C2011 a ukazuje jeden způsob, jak ho opravit:

```
// C2011.cpp
// compile with: /c
struct S;
union S;   // C2011
union S2;   // OK
```