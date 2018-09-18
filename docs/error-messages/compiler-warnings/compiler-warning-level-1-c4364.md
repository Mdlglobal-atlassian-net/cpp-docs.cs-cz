---
title: Upozornění (úroveň 1) C4364 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4364
dev_langs:
- C++
helpviewer_keywords:
- C4364
ms.assetid: 1477634c-d60f-4570-ad16-1aaeae24ac7f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e37c7f37e1b51296bd5c3ae2cbdb85a93326f027
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46087250"
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