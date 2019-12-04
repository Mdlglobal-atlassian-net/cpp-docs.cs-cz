---
title: Chyba kompilátoru C2480
ms.date: 11/04/2016
f1_keywords:
- C2480
helpviewer_keywords:
- C2480
ms.assetid: 1a58d1c2-971b-4084-96fa-f94aa51c02f1
ms.openlocfilehash: 3e495a8019405a558511637467133877dae1183e
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74743520"
---
# <a name="compiler-error-c2480"></a>Chyba kompilátoru C2480

' identifier ': ' Thread ' je platný pouze pro položky dat statického rozsahu

Atribut `thread` nelze použít s automatickým proměnnou, nestatickým datovým členem, parametrem funkce nebo v deklaracích nebo definicích funkcí.

Použijte atribut `thread` u globálních proměnných, statických datových členů a místních statických proměnných.

Následující ukázka generuje C2480:

```cpp
// C2480.cpp
// compile with: /c
__declspec( thread ) void func();   // C2480
__declspec( thread ) static int i;   // OK
```
