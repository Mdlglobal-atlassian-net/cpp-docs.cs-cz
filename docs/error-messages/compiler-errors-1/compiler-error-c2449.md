---
title: Chyba kompilátoru C2449
ms.date: 11/04/2016
f1_keywords:
- C2449
helpviewer_keywords:
- C2449
ms.assetid: 544bf0b6-daa0-40e8-9f21-8e583d472a2d
ms.openlocfilehash: f674bbec7cee8c00792848ee7e51b1e46299dd58
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50655324"
---
# <a name="compiler-error-c2449"></a>Chyba kompilátoru C2449

nalezen ' {"v rozsahu souboru (nechybí hlavička funkce?)

Vyvolá se v rozsahu souboru levou složenou závorku.

Tuto chybu může způsobovat středníkem mezi hlavička funkce a levou složenou závorku v definici funkce.

Následující ukázka generuje C2499:

```
// C2449.c
// compile with: /c
void __stdcall func(void) {}   // OK
void __stdcall func(void);  // extra semicolon on this line
{                         // C2449 detected here
```