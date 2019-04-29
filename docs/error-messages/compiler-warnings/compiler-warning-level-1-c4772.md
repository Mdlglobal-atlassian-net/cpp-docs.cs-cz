---
title: Kompilátor upozornění (úroveň 1) C4772
ms.date: 11/04/2016
f1_keywords:
- C4772
helpviewer_keywords:
- C4772
ms.assetid: dafe6fd8-9faf-41f5-9d66-a55838742c14
ms.openlocfilehash: 95243ab66d5d0296e1c316ff8dde7add75a030cd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62385456"
---
# <a name="compiler-warning-level-1-c4772"></a>Kompilátor upozornění (úroveň 1) C4772

> \#Import odkazovala na typ z chybějící knihovny typů; "*chybí typ*se používá jako zástupný symbol

Knihovnu typů se odkazovalo se [#import](../../preprocessor/hash-import-directive-cpp.md) směrnice. Nicméně knihovny typů obsahovala odkaz na jinou knihovnu typů, na který se odkazuje pomocí `#import`. Tento .tlb soubor nebyl nalezen kompilátorem.

Všimněte si, že kompilátor nebude najít knihovny typů v různých adresářích, pokud použijete [/I (další vložené adresáře)](../../build/reference/i-additional-include-directories.md) – možnost kompilátoru k určení těchto adresářů. Pokud chcete, aby kompilátor k nalezení knihovny typů v různých adresářích, přidejte do proměnné prostředí PATH v těchto adresářích.

Ve výchozím nastavení se objeví toto upozornění za chybu. C4772 nelze potlačit s /W0.

## <a name="example"></a>Příklad

Toto je první potřebnými k zopakování C4772 knihovny typů.

```IDL
// c4772a.idl
[uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12b")]
library C4772aLib
{
   [uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c100")]
   enum E_C4772a
   {
      one, two, three
   };
};
```

Toto je druhý potřebnými k zopakování C4772 knihovny typů.

```IDL
// c4772b.idl
// post-build command: del /f C4772a.tlb
// C4772a.tlb is available when c4772b.tlb is built
[uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12d")]
library C4772bLib
{
   importlib ("c4772a.tlb");
   [uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12e")]
   struct S_C4772b
   {
      enum E_C4772a e;
   };
};
```

Následující ukázka generuje C4772:

```cpp
// C4772.cpp
// assumes that C4772a.tlb is not available to the compiler
// #import "C4772a.tlb"
#import "C4772b.tlb"   // C4772 uncomment previous line to resolve
                       // and make sure c4772a.tlb is on disk
```