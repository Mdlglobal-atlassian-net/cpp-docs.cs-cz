---
title: Upozornění kompilátoru (úroveň 3) C4101
ms.date: 11/04/2016
f1_keywords:
- C4101
helpviewer_keywords:
- C4101
ms.assetid: d98563cd-9dce-4aae-8f12-bd552a4ea677
ms.openlocfilehash: 0ac34fbaf4cbb54583394dff5b8645fe56b8b9cd
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80199042"
---
# <a name="compiler-warning-level-3-c4101"></a>Upozornění kompilátoru (úroveň 3) C4101

' identifier ': neodkazovaná lokální proměnná

Místní proměnná se nikdy nepoužívá. Toto upozornění se projeví ve zjevné situaci:

```cpp
// C4101a.cpp
// compile with: /W3
int main() {
int i;   // C4101
}
```

K tomuto upozornění dojde ale také při volání **statické** členské funkce prostřednictvím instance třídy:

```cpp
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

V této situaci kompilátor používá informace o `si` pro přístup ke **statické** funkci, ale instance třídy není nutná pro volání funkce **static** ; proto upozornění. Chcete-li vyřešit toto upozornění, můžete:

- Přidejte konstruktor, ve kterém by kompilátor používal instanci `si` ve volání `func`.

- Odeberte klíčové slovo **static** z definice `func`.

- Explicitně volejte **statickou** funkci: `int y = S::func();`.
