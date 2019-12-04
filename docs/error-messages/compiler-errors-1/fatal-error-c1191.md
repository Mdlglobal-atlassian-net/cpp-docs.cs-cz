---
title: Závažná chyba C1191
ms.date: 11/04/2016
f1_keywords:
- C1191
helpviewer_keywords:
- C1191
ms.assetid: 2888c6c4-b4e6-449e-8ee0-7917f31086df
ms.openlocfilehash: 7c6756dec29138af534278742d99c2f77109b1cc
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74747290"
---
# <a name="fatal-error-c1191"></a>Závažná chyba C1191

' dll ' lze importovat pouze v globálním oboru

Instrukce pro import knihovny mscorlib. dll do programu, který používá rozhraní/CLR, se nemůže vyskytovat v oboru názvů nebo funkci, ale musí být uvedena v globálním oboru.

Následující ukázka generuje C1191:

```cpp
// C1191.cpp
// compile with: /clr
namespace sample {
   #using <mscorlib.dll>   // C1191 not at global scope
}
```

Možné řešení:

```cpp
// C1191b.cpp
// compile with: /clr /c
#using <mscorlib.dll>
namespace sample {}
```
