---
title: Upozornění kompilátoru (úroveň 3) C4359
ms.date: 11/04/2016
f1_keywords:
- C4359
helpviewer_keywords:
- C4359
ms.assetid: d8fe993c-ef82-45a0-a43d-c29f9d1bacdb
ms.openlocfilehash: 5cb65bab1f6490d1c39b20bfba2b3ecc68da664d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198689"
---
# <a name="compiler-warning-level-3-c4359"></a>Upozornění kompilátoru (úroveň 3) C4359

' type ': skutečné zarovnání (8) je větší než hodnota zadaná v __declspec (align ())

Zarovnání zadané pro typ je menší než zarovnání typu jednoho z jeho datových členů.  Další informace najdete v tématu [Zarovnání](../../cpp/align-cpp.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C4359.

```cpp
// C4359.cpp
// compile with: /W3 /c
struct __declspec(align(8)) C8 { __int64 i; };
struct __declspec(align(4)) C4  { C8 m8; };   // C4359
struct __declspec(align(8)) C8_b  { C8 m8; };   // OK
struct __declspec(align(16)) C16  { C8 m8; };   // OK
```
