---
title: Chyba linkerů Lnk2011 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2011
dev_langs:
- C++
helpviewer_keywords:
- LNK2011
ms.assetid: 04991ef5-49d5-46c7-8eee-a9d1d3fc541e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8f60dce4cb260c670f5ee82aa88b9f106f3f14e2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33300743"
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