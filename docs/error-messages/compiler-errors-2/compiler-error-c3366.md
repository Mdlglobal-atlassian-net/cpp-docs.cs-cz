---
title: Chyba kompilátoru C3366
ms.date: 11/04/2016
f1_keywords:
- C3366
helpviewer_keywords:
- C3366
ms.assetid: efc55bcf-c16d-43c1-a36f-87a6165fa2a8
ms.openlocfilehash: 4d1cd510cda9957ced1d9dd5fd8fea267f39220d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62300554"
---
# <a name="compiler-error-c3366"></a>Chyba kompilátoru C3366

'variable': statické datové členy spravované nebo WinRTtypes musí být definován v rámci definice třídy

Jste se pokusili získat odkazovat na statického členu WinRT nebo .NET třídu nebo rozhraní mimo definici třídy nebo rozhraní.

Kompilátor potřebuje vědět, úplnou definici třídy (a vygenerovat meta-data po jednom průchodu) a vyžaduje statické datové členy mají být inicializovány v rámci třídy.

Například následující příklad generuje C3366 a ukazuje, jak ho opravit:

```
// C3366.cpp
// compile with: /clr /c
ref class X {
   public:
   static int i;   // initialize i here to avoid C3366
};

int X::i = 5;      // C3366
```
