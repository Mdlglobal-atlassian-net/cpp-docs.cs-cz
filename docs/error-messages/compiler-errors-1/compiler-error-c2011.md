---
title: Chyba kompilátoru C2011
ms.date: 11/04/2016
f1_keywords:
- C2011
helpviewer_keywords:
- C2011
ms.assetid: 992c9d51-e850-4d53-b86b-02e73b38249c
ms.openlocfilehash: dc13829a267deea1f412eb2d8f86057f01dc0e1c
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74752415"
---
# <a name="compiler-error-c2011"></a>Chyba kompilátoru C2011

' identifier ': předefinování typu ' type '

Identifikátor již byl definován jako `type`. Vyhledejte předefinování identifikátoru.

Můžete také získat C2011 při importu souboru hlaviček nebo knihovny typů do stejného souboru více než jednou. Chcete-li zabránit vícenásobnému zahrnutí typů definovaných v hlavičkovém souboru, použijte příkaz zahrnout Guard nebo `#pragma`[jednou](../../preprocessor/once.md) direktivu v hlavičkovém souboru.

Pokud potřebujete najít počáteční deklaraci předefinovaného typu, můžete použít příznak kompilátoru [/p](../../build/reference/p-preprocess-to-a-file.md) pro vygenerování předzpracovaného výstupu předaného kompilátoru. Můžete použít nástroje pro vyhledávání textu k nalezení instancí předefinovaného identifikátoru ve výstupním souboru.

Následující ukázka generuje C2011 a ukazuje jeden ze způsobů, jak ji opravit:

```cpp
// C2011.cpp
// compile with: /c
struct S;
union S;   // C2011
union S2;   // OK
```
