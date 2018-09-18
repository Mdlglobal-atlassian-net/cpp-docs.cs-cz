---
title: Upozornění (úroveň 4) C4201 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4201
dev_langs:
- C++
helpviewer_keywords:
- C4201
ms.assetid: 6156f508-9393-4d77-9e73-1ec3e1c32d0d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 702ce23333e29548e9bfe092c15ae60c5652168e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46096935"
---
# <a name="compiler-warning-level-4-c4201"></a>Kompilátor upozornění (úroveň 4) C4201

používá se nestandardní rozšíření: struktura/sjednocení nameless

Pod rozšíření společnosti Microsoft (/Ze) můžete určit strukturu bez deklarátorem jako členy z jiné struktury nebo sjednocení. Tyto struktury vygenerují chybu podle kompatibility ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)).

## <a name="example"></a>Příklad

```
// C4201.cpp
// compile with: /W4
struct S
{
   float y;
   struct
   {
      int a, b, c;  // C4201
   };
} *p_s;

int main()
{
}
```