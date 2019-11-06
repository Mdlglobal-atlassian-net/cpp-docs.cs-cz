---
title: Upozornění kompilátoru (úroveň 1) C4042
ms.date: 11/04/2016
f1_keywords:
- C4042
helpviewer_keywords:
- C4042
ms.assetid: e4bd861b-1194-426b-bf79-68c5b021eb0a
ms.openlocfilehash: db7f0425c3752c20ca8c5d4b6c95845ff64475c5
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/05/2019
ms.locfileid: "73627036"
---
# <a name="compiler-warning-level-1-c4042"></a>Upozornění kompilátoru (úroveň 1) C4042

identifikátor: má chybnou třídu úložiště.

Zadaná třída úložiště se v tomto kontextu nedá použít s tímto identifikátorem. Kompilátor místo toho používá výchozí třídu úložiště:

- `extern`, pokud je *identifikátor* funkce.

- **auto**, pokud je *identifikátor* formální parametr nebo místní proměnná.

- Žádná třída úložiště, pokud je *identifikátor* globální proměnnou.

Toto upozornění může být způsobeno zadáním třídy úložiště jiné než **registrace** v deklaraci parametru.

Následující ukázka generuje C4042

```cpp
// C4042.cpp
// compile with: /W1 /LD
int func2( __declspec( thread ) int tls_i )    // C4042
// try the following line instead
// int func2( int tls_i )
{
   return tls_i;
}
```