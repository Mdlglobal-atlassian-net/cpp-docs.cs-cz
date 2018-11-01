---
title: Chyba kompilátoru C2850
ms.date: 11/04/2016
f1_keywords:
- C2850
helpviewer_keywords:
- C2850
ms.assetid: f3efe86c-4168-4e76-a133-3f8314c69f51
ms.openlocfilehash: 34c2054226ea452f76fdb15b87454677a6a6fe8e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50611767"
---
# <a name="compiler-error-c2850"></a>Chyba kompilátoru C2850

'vytvořit': povoleno pouze v rozsahu souboru; nemusí být ve vnořeném konstruktoru

Konstrukce, jako je například některé prvky pragma se může objevit jenom v globálním oboru.

Následující ukázka generuje C2850:

```
// C2850.cpp
// compile with: /c /Yc
// try the following line instead
// #pragma hdrstop
namespace X {
   #pragma hdrstop   // C2850
};
```