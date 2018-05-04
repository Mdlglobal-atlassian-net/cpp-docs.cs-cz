---
title: Vyhrazená slova | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- code
- CONFORMING
- DISCARDABLE
- Description
- base
- APPLOADER
- Data
- DYNAMIC
- DEV386
dev_langs:
- C++
helpviewer_keywords:
- .def files [C++], reserved words
- def files [C++], reserved words
- linker [C++], reserved words
- reserved words [C++]
ms.assetid: 9b9f49e5-0739-45ab-a37e-81e3915ceb25
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: abe67e1804d436dbd44257f6d7670a71b7f74889
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="reserved-words"></a>Vyhrazená slova
Slova jsou vyhrazené linkeru. Názvy těchto lze použít jako argumenty v [příkazy definice modulu](../../build/reference/module-definition-dot-def-files.md) pouze v případě, že název je uzavřena v uvozovkách ("").  
  
||||  
|-|-|-|  
|**OBJEKTU APPLOADER**1|**INITINSTANCE –**2|**PŘEDBĚŽNÉHO NAČÍTÁNÍ**|  
|**ZÁKLADNÍ**|**IOPL**|**PRIVÁTNÍ**|  
|**KÓD**|**KNIHOVNA**1|**PROTMODE**2|  
|**VYHOVUJÍCÍ**|**LOADONCALL**1|**ČISTÝ**1|  
|**DATA**|**LONGNAMES**2|**JEN PRO ČTENÍ**|  
|**POPIS**|**MOBILNÍ**1|**READWRITE**|  
|**DEV386**|**LZE PŘESUNOUT**1|**PODSLOŽEK REALMODE**1|  
|**DISCARDABLE**|**VÍCE**|**REZIDENTNÍ**|  
|**DYNAMICKÉ**|**JMÉNO**|**RESIDENTNAME**1|  
|**JEN PRO SPUŠTĚNÍ**|**NEWFILES**2|**ODDÍLY**|  
|**EXECUTEONLY**|**NODATA**1|**SEGMENTY**|  
|**EXECUTEREAD**|**NOIOPL**1|**SDÍLENÉ**|  
|**EXETYPE**|**NONAME**|**JEDEN**|  
|**EXPORTY**|**NEODPOVÍDAJÍCÍ**1|**VELIKOST ZÁSOBNÍKU**|  
|**OPRAVENÉ**1|**NONDISCARDABLE**|**ZÁSTUPNÁ PROCEDURA**|  
|**FUNKCE**2|**NONE**|**VERZE**|  
|**VELIKOST HALDY**|**SDÍLENÉM**|**WINDOWAPI**|  
|**IMPORTY**|**NOTWINDOWCOMPAT**1|**WINDOWCOMPAT**|  
|**ZNEČIŠTĚNÁ**1|**OBJEKTY**|**WINDOWS**|  
|**ZAHRNOUT**2|**PŮVODNÍ**1||  
  
 1 linkeru vydá upozornění ("Ignorovat"), pokud se setká s tímto výrazem. Je však stále vyhrazené slovo.  
  
 2 linkeru ignoruje slovo ale vysílá bez upozornění.  
  
## <a name="see-also"></a>Viz také  
 [Nastavení možností Linkeru](../../build/reference/setting-linker-options.md)   
 [Možnosti linkeru](../../build/reference/linker-options.md)