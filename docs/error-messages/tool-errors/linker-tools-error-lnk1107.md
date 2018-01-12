---
title: "Chyba linkerů Lnk1107 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK1107
dev_langs: C++
helpviewer_keywords: LNK1107
ms.assetid: a37a893d-5efa-4eba-8f40-6c5518b4b9d0
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: fae412de31163aa1b5248af43227042cd04563ba
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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