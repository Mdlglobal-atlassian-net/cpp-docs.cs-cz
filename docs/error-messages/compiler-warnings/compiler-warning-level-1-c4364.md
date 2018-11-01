---
title: Kompilátor upozornění (úroveň 1) C4364
ms.date: 11/04/2016
f1_keywords:
- C4364
helpviewer_keywords:
- C4364
ms.assetid: 1477634c-d60f-4570-ad16-1aaeae24ac7f
ms.openlocfilehash: db2774b6a73a989b4e9250719f99122826b486fe
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50643596"
---
# <a name="compiler-warning-level-1-c4364"></a>Kompilátor upozornění (úroveň 1) C4364

\#pro sestavení 'file' dřív zjištěné v: location(line_number) bez atributu as_friend; atribut as_friend se nepoužije

A `#using` – direktiva se opakuje pro daná metadata souboru, ale `as_friend` kvalifikátor nebyl použit v první výskyt; kompilátor bude ignorovat druhou `as_friend`.

Další informace najdete v tématu [přátelská sestavení (C++)](../../dotnet/friend-assemblies-cpp.md).

## <a name="example"></a>Příklad

Následující příklad vytvoří komponentu.

```
// C4364.cpp
// compile with: /clr /LD
ref class A {};
```

## <a name="example"></a>Příklad

Následující ukázka generuje C4364.

```
// C4364_b.cpp
// compile with: /clr /W1 /c
#using " C4364.dll"
#using " C4364.dll" as_friend   // C4364
```