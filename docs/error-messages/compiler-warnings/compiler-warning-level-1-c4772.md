---
title: "Kompilátoru (úroveň 1) upozornění C4772 | Microsoft Docs"
ms.date: 11/04/2016
ms.technology: cpp-tools
ms.topic: error-reference
f1_keywords: C4772
dev_langs: C++
helpviewer_keywords: C4772
ms.assetid: dafe6fd8-9faf-41f5-9d66-a55838742c14
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 6ba1b01baf6c5d30da86821a976202bb5936c868
ms.sourcegitcommit: 69632887f7a85f4841c49b4c1353d3144927a52c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/11/2017
---
# <a name="compiler-warning-level-1-c4772"></a>C4772 kompilátoru upozornění (úroveň 1)

> \#Import odkazuje typ z chybějící knihovny typů; '*chybí typ*se používá jako zástupný znak

Knihovny typů bylo odkazováno s [#import](../../preprocessor/hash-import-directive-cpp.md) – direktiva. Ale knihovny typů obsahovala odkaz na jiné knihovny typů, který nebyl odkazuje s `#import`. Tento .tlb soubor nebyl nalezen kompilátorem.

Všimněte si, že kompilátor nebude najít knihovny typů v různých adresářích, pokud použijete [/I (Další adresáře Include)](../../build/reference/i-additional-include-directories.md) – možnost kompilátoru k určení těchto adresářů. Pokud chcete kompilátoru k nalezení knihovny typů v různých adresářích, přidejte tyto adresáře do proměnné prostředí PATH.

Ve výchozím nastavení se objeví toto upozornění za chybu. C4772 nelze potlačit s /W0.

## <a name="example"></a>Příklad

Toto je první knihovny typů, které jsou potřebné pro reprodukci C4772.

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

Toto je druhý knihovny typů, které jsou potřebné pro reprodukci C4772.

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