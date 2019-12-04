---
title: Chyba kompilátoru C3453
ms.date: 11/04/2016
f1_keywords:
- C3453
helpviewer_keywords:
- C3453
ms.assetid: dbefdbcf-f697-4239-b7a5-1d99b85e9e7f
ms.openlocfilehash: 993300d4bf3b4fd6f0bd05392fc5263b3c8671d9
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756692"
---
# <a name="compiler-error-c3453"></a>Chyba kompilátoru C3453

' Attribute ': atribut se nepoužil, protože kvalifikátor ' Assembly ' se neshoduje.

Atributy na úrovni sestavení nebo modulu lze zadat pouze jako samostatné instrukce.

## <a name="example"></a>Příklad

Následující ukázka generuje C3453.

```cpp
// C3453.cpp
// compile with: /clr /c
[assembly:System::CLSCompliant(true)]   // C3453
// try the following line instead
// [assembly:System::CLSCompliant(true)];
ref class X {};
```
