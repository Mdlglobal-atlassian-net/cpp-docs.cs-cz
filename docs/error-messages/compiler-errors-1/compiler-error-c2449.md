---
title: Chyba kompilátoru C2449 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2449
dev_langs:
- C++
helpviewer_keywords:
- C2449
ms.assetid: 544bf0b6-daa0-40e8-9f21-8e583d472a2d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3e92638eaca1fe951d6b67da7563930214198926
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46018766"
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