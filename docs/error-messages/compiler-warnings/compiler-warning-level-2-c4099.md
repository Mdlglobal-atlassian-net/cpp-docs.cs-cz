---
title: Upozornění kompilátoru (úroveň 2) C4099
ms.date: 11/04/2016
f1_keywords:
- C4099
helpviewer_keywords:
- C4099
ms.assetid: 00bb803d-cae7-4ab8-8969-b46f54139ac8
ms.openlocfilehash: 97ead14dc9771dc02ad722843ec9fe1a8056e3f6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80174281"
---
# <a name="compiler-warning-level-2-c4099"></a>Upozornění kompilátoru (úroveň 2) C4099

' identifier ': název typu First zaznamenal použití ' objecttype1 ' nyní používá ' objecttype2 '

Objekt deklarovaný jako struktura je definován jako třída nebo objekt deklarovaný jako třída je definován jako struktura. Kompilátor používá typ uvedený v definici.

## <a name="example"></a>Příklad

Následující ukázka generuje C4099.

```cpp
// C4099.cpp
// compile with: /W2 /c
struct A;
class A {};   // C4099, use different identifer or use same object type
```
