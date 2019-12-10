---
title: Upozornění kompilátoru (úroveň 4) C4714
ms.date: 11/04/2016
f1_keywords:
- C4714
helpviewer_keywords:
- C4714
ms.assetid: 22c7fd0c-899d-4e9b-95f3-725b2c49fb46
ms.openlocfilehash: 8ea4212eaddf14546827728b31299063021a959f
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74989645"
---
# <a name="compiler-warning-level-4-c4714"></a>Upozornění kompilátoru (úroveň 4) C4714

funkce Functions označená jako __forceinline není vložená.

Daná funkce byla vybrána pro vložené rozšíření, ale kompilátor neprováděl vkládání.

I když `__forceinline` je silnější označení kompilátoru než `__inline`, je vkládání stále prováděno podle uvážení kompilátoru, ale k určení výhod z vložení této funkce se nepoužívají žádné heuristiky.

V některých případech kompilátor nevloží určitou funkci z mechanických důvodů. Například kompilátor nebude vložen:

- Funkce, pokud by to vedlo k smíchání obou SEH i C++ eh.

- Některé funkce s kopírováním konstruovaných objektů předávaných hodnotou when-GX/EHs/EHa jsou zapnuty.

- Funkce vracející nepřevíjetelné objekty podle hodnoty when-GX/EHs/EHa je zapnuto.

- Funkce s vloženým sestavením při kompilaci bez-Og/Ox/O1/O2.

- Funkce se seznamem argumentů proměnných.

- Funkce s příkazem **Try** (C++ zpracování výjimek).

Následující ukázka generuje C4714:

```cpp
// C4714.cpp
// compile with: /Ob1 /GX /W4
__forceinline void func1()
{
   try
   {
   }
   catch (...)
   {
   }
}

void func2()
{
   func1();   // C4714
}

int main()
{
}
```
