---
title: Upozornění (úroveň 4) C4559 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4559
dev_langs:
- C++
helpviewer_keywords:
- C4559
ms.assetid: ed542f60-454d-45cb-85da-987ede61b1ab
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4d5743b33f62aa954c3765b729ab5c0297b20e32
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43195573"
---
# <a name="compiler-warning-level-4-c4559"></a>Kompilátor upozornění (úroveň 4) C4559

> "*funkce*': předefinování; zisky __declspec – funkce (*modifikátor*)

## <a name="remarks"></a>Poznámky

Funkce byla předefinovat nebo došlo ke změně deklarace, a druhá definice nebo deklarace přidána **__declspec** modifikátor (*modifikátor*). Toto upozornění je informační. Pokud chcete vyřešit toto upozornění, odstraňte jednu z definic.

## <a name="example"></a>Příklad

Následující ukázka generuje C4559:

```cpp
// C4559.cpp
// compile with: /W4 /LD
void f();
__declspec(noalias) void f();   // C4559
```