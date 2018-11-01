---
title: Chyba kompilátoru C2480
ms.date: 11/04/2016
f1_keywords:
- C2480
helpviewer_keywords:
- C2480
ms.assetid: 1a58d1c2-971b-4084-96fa-f94aa51c02f1
ms.openlocfilehash: 90016b65d4ddd58da3fb3c5ab6d81322dc0ef394
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50566722"
---
# <a name="compiler-error-c2480"></a>Chyba kompilátoru C2480

'identifier': "vlákna" je platná pouze pro položky dat statického kontextu

Nelze použít `thread` atribut s předplatným automatickou proměnnou, nestatický datový člen, parametr funkce, nebo na deklaracích nebo definicích funkce.

Použití `thread` atribut pro globální proměnné, statické datové členy a místní pouze statické proměnné.

Následující ukázka generuje C2480:

```
// C2480.cpp
// compile with: /c
__declspec( thread ) void func();   // C2480
__declspec( thread ) static int i;   // OK
```