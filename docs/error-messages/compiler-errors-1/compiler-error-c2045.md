---
title: Chyba kompilátoru C2045
ms.date: 11/04/2016
f1_keywords:
- C2045
helpviewer_keywords:
- C2045
ms.assetid: 2fca668e-9b20-4933-987a-18c0fd0187df
ms.openlocfilehash: cf3644c49e424315fb406fa9548fcf6ce1bfcbc7
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74740374"
---
# <a name="compiler-error-c2045"></a>Chyba kompilátoru C2045

' identifier ': předefinován popisek

Popisek se zobrazí před více příkazy ve stejné funkci.

Následující ukázka generuje C2045:

```cpp
// C2045.cpp
int main() {
   label: {
   }
   goto label;
   label: {}   // C2045
}
```
