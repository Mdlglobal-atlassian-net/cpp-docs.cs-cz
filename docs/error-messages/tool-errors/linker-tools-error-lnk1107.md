---
title: Chyba linkerů LNK1107
ms.date: 11/04/2016
f1_keywords:
- LNK1107
helpviewer_keywords:
- LNK1107
ms.assetid: a37a893d-5efa-4eba-8f40-6c5518b4b9d0
ms.openlocfilehash: c75966d9c6c22f1bd2123fb30282bb2bed467130
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991028"
---
# <a name="linker-tools-error-lnk1107"></a>Chyba linkerů LNK1107

soubor je neplatný nebo poškozený: nejde číst v umístění.

Nástroj nemohlo přečíst soubor. Znovu vytvořte soubor.

K LINKERŮ LNK1107 může také dojít, pokud se pokusíte předat linkeru modul (příponu. dll nebo. netmodule vytvořený pomocí [/clr:-Assembly](../../build/reference/clr-common-language-runtime-compilation.md) nebo [/NOASSEMBLY](../../build/reference/noassembly-create-a-msil-module.md)). místo toho předejte soubor. obj.

Pokud kompilujete následující ukázku:

```cpp
// LNK1107.cpp
// compile with: /clr /LD
public ref class MyClass {
public:
   void Test(){}
};
```

a pak na příkazovém řádku zadejte **Link linkerů LNK1107. dll** , získáte linkerů LNK1107.  Chcete-li vyřešit chybu, zadejte místo toho **linku linkerů LNK1107. obj** .
