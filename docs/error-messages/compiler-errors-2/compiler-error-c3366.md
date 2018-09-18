---
title: Chyba kompilátoru C3366 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3366
dev_langs:
- C++
helpviewer_keywords:
- C3366
ms.assetid: efc55bcf-c16d-43c1-a36f-87a6165fa2a8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b3638ba2415839c044d9a82d82d0abe8bc2c98e2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46026501"
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
