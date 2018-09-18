---
title: Chyba Linkerů LNK1107 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1107
dev_langs:
- C++
helpviewer_keywords:
- LNK1107
ms.assetid: a37a893d-5efa-4eba-8f40-6c5518b4b9d0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 73a1643d10ea9adc6ac6979eb2de023593ba8d01
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46060704"
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