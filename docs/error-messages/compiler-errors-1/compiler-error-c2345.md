---
title: Chyba kompilátoru C2345
ms.date: 11/04/2016
f1_keywords:
- C2345
helpviewer_keywords:
- C2345
ms.assetid: e1cc88b0-0223-4d07-975b-fa99956a82bd
ms.openlocfilehash: 85d9e312bafe0cf6c9390f7484281e1aefb22aab
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760020"
---
# <a name="compiler-error-c2345"></a>Chyba kompilátoru C2345

align (hodnota): Neplatná hodnota zarovnání

Předala se hodnota k klíčovému slovu [align](../../cpp/align-cpp.md) , která je mimo povolený rozsah.

Následující kód generuje C2345

```cpp
// C2345.cpp
// compile with: /c
__declspec(align(0)) int a;   // C2345
__declspec(align(1)) int a;   // OK
```
