---
title: "Chyba linkerů Lnk2011 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK2011
dev_langs: C++
helpviewer_keywords: LNK2011
ms.assetid: 04991ef5-49d5-46c7-8eee-a9d1d3fc541e
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9811bdb905df61bb77ea4af6bc4ced7c4ba42106
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-error-lnk2011"></a>Chyba linkerů LNK2011
Předkompilované objekt není propojený v; bitová kopie nemusí fungovat.  
  
 Pokud používáte předkompilovaných hlaviček, odkaz vyžaduje, že všechny soubory objektu vytvořeny s předkompilovaných hlaviček musí být propojena v. Pokud máte zdrojový soubor, který používáte ke generování předkompilovaných hlaviček pro použití s ostatními zdrojové soubory, teď musíte zahrnout soubor objektu společně předkompilovaných hlaviček.  
  
 Například pokud zkompilujete do souboru s názvem STUB.cpp vytvořit předkompilovaný hlavičkový pro použití s ostatními zdrojové soubory, je nutné propojit s STUB.obj nebo budete mít k této chybě. V následujících příkazových řádků řádku jeden slouží k vytvoření předkompilovaných hlaviček, COMMON.pch, který se používá s PROG1.cpp a PROG2.cpp na řádcích druhé a třetí. Soubor STUB.cpp obsahuje pouze `#include` řádky (stejná `#include` řádky jako PROG1.cpp a PROG2.cpp) a slouží pouze ke generování předkompilovaných hlaviček. Na posledním řádku musí být propojena v STUB.obj předejdete LNK2011.  
  
```  
cl /c /Yccommon.h stub.cpp  
cl /c /Yucommon.h prog1.cpp  
cl /c /Yucommon.h prog2.cpp  
link /out:prog.exe stub.obj prog1.obj prog2.obj  
```