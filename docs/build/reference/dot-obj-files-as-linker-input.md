---
title: . Soubory obj jako vstup Linkeru | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- linker [C++], OBJ files as input
- object files, linker output
- OMF object files
- LINK tool [C++], .obj files
- COFF files
- OBJ files as linker input
- .obj files as linker input
ms.assetid: 3028e423-8b10-4972-8eb4-6e9ae58f0a26
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ca8346f9ff29d097450eda4d8bfbfee7f7a3f522
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="obj-files-as-linker-input"></a>Soubory .Obj jako vstup linkeru
Nástroj linkeru (odkaz. Soubor EXE) přijímá soubory .obj, které jsou v běžné objekt souboru formátu (COFF).  
  
## <a name="remarks"></a>Poznámky  
 Společnost Microsoft poskytuje ke stažení dokument, který definuje běžný formát souboru objektu. Další informace, stáhněte si revize 8.1 nebo novější z [Microsoft přenosné spustitelný soubor a běžné specifikaci formátu souboru objektu](http://go.microsoft.com/fwlink/?LinkId=93292).  
  
## <a name="unicode-support"></a>Podpora kódování Unicode  
 Od verze Visual Studio 2005, podporuje Microsoft Visual C++ compiler znaky kódování Unicode v identifikátory definované ISO/IEC C a C++ standardů. V identifikátory předchozí verze kompilátoru podporovány pouze znaky ASCII. Chcete-li podporují kódování Unicode v názvech funkcí, třídy a statické objekty, použijte kompilátoru a linkeru kódování Unicode UTF-8 symbolů COFF v soubory .obj. Kódování UTF-8 je upwardly kompatibilní s kódováním ASCII, které se používá starších verzí sady Visual Studio.  
  
 Další informace o kompilátoru a linkeru najdete v tématu [Podpora kódování Unicode v kompilátoru a Linkeru](../../build/reference/unicode-support-in-the-compiler-and-linker.md). Další informace o standardu Unicode, najdete v článku [Unicode](http://go.microsoft.com/fwlink/?LinkId=37123) organizace.  
  
## <a name="see-also"></a>Viz také  
 [Vstupní soubory LINK](../../build/reference/link-input-files.md)   
 [Možnosti linkeru](../../build/reference/linker-options.md)   
 [Podpora kódování Unicode](../../text/support-for-unicode.md)   
 [Podpora kódování Unicode v kompilátoru a Linkeru](../../build/reference/unicode-support-in-the-compiler-and-linker.md)   
 [Unicode standard](http://go.microsoft.com/fwlink/?LinkId=37123)   
 [Běžné specifikaci formátu souboru objektu](http://go.microsoft.com/fwlink/?LinkId=93292)