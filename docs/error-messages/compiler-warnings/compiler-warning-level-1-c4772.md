---
title: Upozornění kompilátoru (úroveň 1) C4772
ms.date: 11/04/2016
f1_keywords:
- C4772
helpviewer_keywords:
- C4772
ms.assetid: dafe6fd8-9faf-41f5-9d66-a55838742c14
ms.openlocfilehash: 89156b2f29fd21160e6abddc3ecb21efaee6dde1
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175127"
---
# <a name="compiler-warning-level-1-c4772"></a>Upozornění kompilátoru (úroveň 1) C4772

> \#import odkazoval na typ z chybějící knihovny typů; '*chybějící-Type*' použitý jako zástupný text

Na knihovnu typů se odkazuje direktiva [#import](../../preprocessor/hash-import-directive-cpp.md) . Knihovna typů však obsahovala odkaz na jinou knihovnu typů, na kterou neodkazuje `#import`. Tento jiný soubor. tlb nebyl kompilátorem nalezen.

Všimněte si, že kompilátor nenajde knihovny typů v různých adresářích, pokud použijete možnost kompilátoru [/i (další adresáře include)](../../build/reference/i-additional-include-directories.md) k určení těchto adresářů. Pokud chcete, aby kompilátor hledal knihovny typů v různých adresářích, přidejte tyto adresáře do proměnné prostředí PATH.

Ve výchozím nastavení se toto upozornění vydá jako chyba. C4772 se nedá potlačit s/W0.

## <a name="example"></a>Příklad

Toto je první knihovna typů, která se potřebuje k reprodukování C4772.

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

Toto je druhá knihovna typů, která se potřebuje k reprodukování C4772.

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
