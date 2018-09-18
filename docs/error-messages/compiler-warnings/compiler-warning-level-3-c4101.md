---
title: Upozornění (úroveň 3) C4101 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4101
dev_langs:
- C++
helpviewer_keywords:
- C4101
ms.assetid: d98563cd-9dce-4aae-8f12-bd552a4ea677
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1549a327329d438cb30bd6908e07419eb1b6bc1a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46060834"
---
# <a name="compiler-warning-level-3-c4101"></a>Kompilátor upozornění (úroveň 3) C4101

'identifier': neodkazovaná lokální proměnná

Lokální proměnné se nikdy nepoužívá. Toto upozornění se generují v zřejmé situace:

```
// C4101a.cpp
// compile with: /W3
int main() {
int i;   // C4101
}
```

Nicméně toto upozornění se vrátí taky při volání metody **statické** funkce člena prostřednictvím instance třídy:

```
// C4101b.cpp
// compile with:  /W3
struct S {
   static int func()
   {
      return 1;
   }
};

int main() {
   S si;   // C4101, si is never used
   int y = si.func();
   return y;
}
```

V takovém případě kompilátor používá informace o `si` přístup **statické** funkce, ale instance třídy není potřeba volat **statické** funkce; proto upozornění. Pokud chcete vyřešit toto upozornění, můžete:

- Přidejte konstruktor, ve kterém by kompilátor použít instanci `si` ve volání `func`.

- Odeberte **statické** – klíčové slovo z definice `func`.

- Volání **statické** funkce explicitně: `int y = S::func();`.