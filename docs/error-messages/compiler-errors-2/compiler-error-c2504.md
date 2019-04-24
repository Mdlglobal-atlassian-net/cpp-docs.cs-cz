---
title: Chyba kompilátoru C2504
ms.date: 11/04/2016
f1_keywords:
- C2504
helpviewer_keywords:
- C2504
ms.assetid: c9e002a6-a4ee-4ba7-970e-edf4adb83692
ms.openlocfilehash: 8f428699aa14cbd1f021a57ed8dcabefa8b24c16
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62165083"
---
# <a name="compiler-error-c2504"></a>Chyba kompilátoru C2504

'class': základní třída undefined

Základní třída je deklarovaná, ale dosud definováno.  Možné příčiny:

1. Chybí soubor k zahrnutí.

1. Externí základní třída není deklarována s [extern](../../cpp/using-extern-to-specify-linkage.md).

Následující ukázka generuje C2504:

```
// C2504.cpp
// compile with: /c
class A;
class B : public A {};   // C2504
```

// OK

```
class C{};
class D : public C {};
```