---
title: Compiler Error C3295
ms.date: 11/04/2016
f1_keywords:
- C3295
helpviewer_keywords:
- C3295
ms.assetid: 83f0aa4d-0e0a-4905-9f66-fcf9991fc07a
ms.openlocfilehash: 63739989d737527e3f136bb3aac2269eda6231c1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62222554"
---
# <a name="compiler-error-c3295"></a>Compiler Error C3295

"#pragma – Direktiva pragma" jde použít jenom na globální nebo obor názvů

Některé prvky pragma nelze použít ve funkci.  Zobrazit [direktivy Pragma a klíčové slovo __Pragma](../../preprocessor/pragma-directives-and-the-pragma-keyword.md) Další informace.

## <a name="example"></a>Příklad

Následující ukázka generuje C3295.

```
// C3295.cpp
int main() {
   #pragma managed   // C3295
}
```