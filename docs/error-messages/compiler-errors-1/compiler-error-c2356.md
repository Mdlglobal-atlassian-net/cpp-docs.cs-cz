---
title: Chyba kompilátoru C2356
ms.date: 11/04/2016
f1_keywords:
- C2356
helpviewer_keywords:
- C2356
ms.assetid: 84d5a816-9a61-4d45-9978-38e485bbf767
ms.openlocfilehash: 0166cce6011017b8a18821666083f7c47f58b7a9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62302537"
---
# <a name="compiler-error-c2356"></a>Chyba kompilátoru C2356

segment inicializace nesmí změnit průběhu překladové jednotky.

Možné příčiny:

- `#pragma init_seg` předchází segmentu inicializační kód

- `#pragma init_seg` před jiným `#pragma init_seg`

Pokud chcete vyřešit, přesun segmentu inicializační kód na začátek modulu. Pokud musí být inicializován více oblastí, přesuňte je do samostatných modulů.

Následující ukázka generuje C2356:

```
// C2356.cpp
#pragma warning(disable : 4075)

int __cdecl myexit(void (__cdecl *)());
int __cdecl myexit2(void (__cdecl *)());

#pragma init_seg(".mine$m",myexit)
#pragma init_seg(".mine$m",myexit2)   // C2356
```