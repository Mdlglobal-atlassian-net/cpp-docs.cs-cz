---
title: Upozornění (úroveň 4) C4565 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4565
dev_langs:
- C++
helpviewer_keywords:
- C4565
ms.assetid: a71f1341-a4a1-4060-ad1e-9322531883ed
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c25f2f1fc16c6d45a7d1eddec8d3efe62db142f2
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43211259"
---
# <a name="compiler-warning-level-4-c4565"></a>Kompilátor upozornění (úroveň 4) C4565

> "*funkce*': předefinování; symbol se předtím deklaroval s: __declspec (*modifikátor*)

## <a name="remarks"></a>Poznámky

Symbol se předefinovalo nebo došlo ke změně deklarace, a druhá definice nebo deklarace, na rozdíl od první definice nebo deklarace, neměl `__declspec` modifikátor (*modifikátor*). Toto upozornění je informační. Pokud chcete vyřešit toto upozornění, odstraňte jednu z definic.

## <a name="example"></a>Příklad

Následující ukázka generuje C4565:

```cpp
// C4565.cpp
// compile with: /W4 /LD
__declspec(noalias) void f();
void f();   // C4565
```