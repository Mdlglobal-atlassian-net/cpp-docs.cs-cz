---
title: Chyba kompilátoru C3199
ms.date: 11/04/2016
f1_keywords:
- C3199
helpviewer_keywords:
- C3199
ms.assetid: e7a478d3-115a-40a3-991b-c7454fd2e28e
ms.openlocfilehash: 934e980149ad893e6799b0ab119a148fc5652fdc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50578955"
---
# <a name="compiler-error-c3199"></a>Chyba kompilátoru C3199

Neplatné použití direktiv pragma s plovoucí desetinnou čárkou: výjimky jsou podporované jedině v režimu bez přesné

[Float_control](../../preprocessor/float-control.md) – Direktiva pragma se používá k určení model výjimek s plovoucí desetinnou čárkou v rámci [/FP](../../build/reference/fp-specify-floating-point-behavior.md) nastavení jiné než **/FP: precise**.

Následující ukázka generuje C3199:

```
// C3199.cpp
// compile with: /fp:fast
#pragma float_control(except, on)   // C3199
```