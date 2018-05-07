---
title: Chyba linkerů Lnk1107 | Microsoft Docs
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
ms.openlocfilehash: fee2105cb0c12287cd2b47636f0e47011854a608
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-error-lnk1107"></a>Chyba linkerů LNK1107
Neplatný nebo poškozený soubor: Nelze číst v umístění  
  
 Nástroj nemohl načíst soubor. Soubor znovu vytvořte.  
  
 LNK1107 by se mohl vyskytnout, pokud se pokusíte předat modulu (.dll nebo .netmodule rozšíření, které jsou vytvořené pomocí [/clr:noAssembly](../../build/reference/clr-common-language-runtime-compilation.md) nebo [/NOASSEMBLY](../../build/reference/noassembly-create-a-msil-module.md)) linkeru; předat souboru .obj místo.  
  
 Pokud zkompilujete následující ukázka:  
  
```  
// LNK1107.cpp  
// compile with: /clr /LD  
public ref class MyClass {  
public:  
   void Test(){}  
};  
```  
  
 a pak zadejte **odkaz LNK1107.dll** na příkazovém řádku, zobrazí se LNK1107.  Chcete-li vyřešit chyby, zadejte **odkaz LNK1107.obj** místo.