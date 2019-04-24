---
title: Chyba linkerů LNK1107
ms.date: 11/04/2016
f1_keywords:
- LNK1107
helpviewer_keywords:
- LNK1107
ms.assetid: a37a893d-5efa-4eba-8f40-6c5518b4b9d0
ms.openlocfilehash: 68048d9f824283d002a4ea8b64d88f37bbeefc48
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62255389"
---
# <a name="linker-tools-error-lnk1107"></a>Chyba linkerů LNK1107

soubor je neplatný nebo poškozený: Nelze číst umístění

Nástroj nelze přečíst soubor. Tento soubor znovu vytvořte.

LNK1107 by se mohl vyskytnout, pokud se pokusíte předat modulu (příponu .dll nebo .netmodule vytvořené pomocí [/clr:noAssembly](../../build/reference/clr-common-language-runtime-compilation.md) nebo [parametr/noassembly](../../build/reference/noassembly-create-a-msil-module.md)) do propojovacího programu; předat souboru .obj, místo toho.

Pokud kompilujete následující ukázce:

```
// LNK1107.cpp
// compile with: /clr /LD
public ref class MyClass {
public:
   void Test(){}
};
```

a pak zadejte **propojit LNK1107.dll** na příkazovém řádku se zobrazí LNK1107.  Chcete-li chybu vyřešit, zadejte **propojit LNK1107.obj** místo.