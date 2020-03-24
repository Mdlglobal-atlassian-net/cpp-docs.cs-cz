---
title: Upozornění kompilátoru (úroveň 1) C4229
ms.date: 11/04/2016
f1_keywords:
- C4229
helpviewer_keywords:
- C4229
ms.assetid: aadfc83b-1e5f-4229-bd0a-9c10a5d13182
ms.openlocfilehash: b1cb97c51dca7cf3fdbca024ead969c4d4e1f3eb
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80163281"
---
# <a name="compiler-warning-level-1-c4229"></a>Upozornění kompilátoru (úroveň 1) C4229

používá se anachronizmus: modifikátory pro data se ignorují.

Použití modifikátoru Microsoft, jako je například `__cdecl` v deklaraci dat, je zastaralý postup.

## <a name="example"></a>Příklad

```cpp
// C4229.cpp
// compile with: /W1 /LD
int __cdecl counter;   // C4229 cdecl ignored
```
