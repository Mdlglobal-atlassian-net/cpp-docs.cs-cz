---
title: . Soubory obj jako vstup Linkeru | Microsoft Docs
ms.custom: 
ms.date: 12/29/2017
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
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9a2896822e97bdbb5ffdf8f869e67beadc1675b7
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2018
---
# <a name="obj-files-as-linker-input"></a>Soubory .Obj jako vstup linkeru

Nástroj linkeru (odkaz. Soubor EXE) přijímá soubory .obj, které jsou v běžné objekt souboru formátu (COFF).

## <a name="remarks"></a>Poznámky

Společnost Microsoft poskytuje úplný popis běžný formát souboru objektu. Další informace najdete v tématu [PE formátu](https://msdn.microsoft.com/library/windows/desktop/ms680547).

## <a name="unicode-support"></a>Podpora kódování Unicode

Od verze Visual Studio 2005, podporuje Microsoft Visual C++ compiler znaky kódování Unicode v identifikátory definované ISO/IEC C a C++ standardů. V identifikátory předchozí verze kompilátoru podporovány pouze znaky ASCII. Chcete-li podporují kódování Unicode v názvech funkcí, třídy a statické objekty, použijte kompilátoru a linkeru kódování Unicode UTF-8 symbolů COFF v soubory .obj. Kódování UTF-8 je upwardly kompatibilní s kódováním ASCII, které se používá starších verzí sady Visual Studio.

Další informace o kompilátoru a linkeru najdete v tématu [Podpora kódování Unicode v kompilátoru a Linkeru](../../build/reference/unicode-support-in-the-compiler-and-linker.md). Další informace o standardu Unicode, najdete v článku [Unicode](http://go.microsoft.com/fwlink/p/?linkid=37123) organizace.

## <a name="see-also"></a>Viz také

[Vstupní soubory LINK](../../build/reference/link-input-files.md)  
[Možnosti linkeru](../../build/reference/linker-options.md)  
[Podpora pro Unicode](../../text/support-for-unicode.md)  
[Podpora kódování Unicode v kompilátoru a linkeru](../../build/reference/unicode-support-in-the-compiler-and-linker.md)  
[Unicode standard](http://go.microsoft.com/fwlink/p/?linkid=37123)  
[Formát PE](https://msdn.microsoft.com/library/windows/desktop/ms680547)  
