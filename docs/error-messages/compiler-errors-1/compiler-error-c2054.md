---
title: Chyba kompilátoru C2054
ms.date: 11/04/2016
f1_keywords:
- C2054
helpviewer_keywords:
- C2054
ms.assetid: 37f7c612-0d7d-4728-9e67-ac4160555f48
ms.openlocfilehash: e7d90d684c1d95f540f6357bf61ee7c6f889ad3f
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/20/2019
ms.locfileid: "75302052"
---
# <a name="compiler-error-c2054"></a>Chyba kompilátoru C2054

očekávalo se klíčové slovo (pro následný identifikátor).

Identifikátor funkce se používá v kontextu, který vyžaduje koncové závorky.

Tato chyba může být způsobena vynecháním znaku rovná se (=) při komplexní inicializaci.

Následující ukázka generuje C2054:

```c
// C2054.c
int array1[] { 1, 2, 3 };   // C2054, missing =
```

Možné řešení:

```c
// C2054b.c
int main() {
   int array2[] = { 1, 2, 3 };
}
```
