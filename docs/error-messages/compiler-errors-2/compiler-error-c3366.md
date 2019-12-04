---
title: Chyba kompilátoru C3366
ms.date: 11/04/2016
f1_keywords:
- C3366
helpviewer_keywords:
- C3366
ms.assetid: efc55bcf-c16d-43c1-a36f-87a6165fa2a8
ms.openlocfilehash: 5173b1c0df7de6a4e8d9993e680b961a82bb10a7
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74738463"
---
# <a name="compiler-error-c3366"></a>Chyba kompilátoru C3366

' Variable ': statické datové členy spravované nebo WinRTtypes musí být definovány v rámci definice třídy

Pokusili jste se odkázat na statický člen třídy WinRT nebo .NET rozhraní, mimo definici této třídy nebo rozhraní.

Kompilátor potřebuje znát úplnou definici třídy (pro generování metadat po jednom průchodu) a vyžaduje, aby se statické datové členy inicializoval v rámci třídy.

Například následující příklad generuje C3366 a ukazuje, jak ho opravit:

```cpp
// C3366.cpp
// compile with: /clr /c
ref class X {
   public:
   static int i;   // initialize i here to avoid C3366
};

int X::i = 5;      // C3366
```
