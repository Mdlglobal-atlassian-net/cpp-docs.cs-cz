---
title: Upozornění (úroveň 4) C4207 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4207
dev_langs:
- C++
helpviewer_keywords:
- C4207
ms.assetid: f4e09e3e-ac87-4489-8e3f-c8f76b82e721
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a5aa7f364eb8f60d680dde4c252b9c84e258cda0
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46068829"
---
# <a name="compiler-warning-level-4-c4207"></a>Kompilátor upozornění (úroveň 4) C4207

používá se nestandardní rozšíření: Rozšířená podoba inicializátoru

S rozšířeními společnosti Microsoft (/Ze), můžete inicializovat pole nesetříděné podle velikosti `char` pomocí řetězce v závorkách.

## <a name="example"></a>Příklad

```
// C4207.c
// compile with: /W4
char c[] = { 'a', 'b', "cdefg" }; // C4207

int main()
{
}
```

Tyto inicializace jsou neplatné pod kompatibility ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)).