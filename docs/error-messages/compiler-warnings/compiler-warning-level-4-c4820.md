---
title: Kompilátor upozornění (úroveň 4) C4820
ms.date: 11/04/2016
f1_keywords:
- C4820
helpviewer_keywords:
- C4820
ms.assetid: 17aa29f4-c287-49b8-bc43-8ed82ffed5ea
ms.openlocfilehash: adf8b365bc39acc1ce729e89260f8385ecb6c048
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50447824"
---
# <a name="compiler-warning-level-4-c4820"></a>Kompilátor upozornění (úroveň 4) C4820

odsazení 'bytes' bajtů přidáno po vytvoření 'member_name'

Typ a pořadí prvků způsobila kompilátoru odsazení přidat na konec struktury. Zobrazit [zarovnat](../../cpp/align-cpp.md) Další informace o odsazení struktury.

Toto upozornění je vypnuto ve výchozím nastavení. Zobrazit [kompilátoru upozornění, že je vypnuto ve výchozím nastavení](../../preprocessor/compiler-warnings-that-are-off-by-default.md) Další informace.

Následující ukázka generuje C4820:

```
// C4820.cpp
// compile with: /W4 /c
#pragma warning(default : 4820)

// Delete the following 4 lines to resolve.
__declspec(align(2)) struct MyStruct {
   char a;
   int i;   // C4820
};

// OK
#pragma pack(1)
__declspec(align(1)) struct MyStruct2 {
   char a;
   int i;
};
```