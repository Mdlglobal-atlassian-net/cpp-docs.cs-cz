---
title: Kompilátor upozornění (úroveň 3) C4101
ms.date: 11/04/2016
f1_keywords:
- C4101
helpviewer_keywords:
- C4101
ms.assetid: d98563cd-9dce-4aae-8f12-bd552a4ea677
ms.openlocfilehash: d1109a32e754a6055e5e1d90632ad85332d832f1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62402317"
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