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
ms.openlocfilehash: 132bd8e5ba66cbf9486a6da4747994c667e2f6e7
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2018
ms.locfileid: "34705657"
---
# <a name="reserved-words"></a>Vyhrazená slova

Slova jsou vyhrazené linkeru. Názvy těchto lze použít jako argumenty v [příkazy definice modulu](../../build/reference/module-definition-dot-def-files.md) pouze v případě, že název je uzavřena v uvozovkách ("").

||||
|-|-|-|
|**OBJEKTU APPLOADER**<sup>1</sup>|**INITINSTANCE –**<sup>2</sup>|**PŘEDBĚŽNÉHO NAČÍTÁNÍ**|
|**ZÁKLADNÍ**|**IOPL**|**PRIVÁTNÍ**|
|**KÓD**|**KNIHOVNA**<sup>1</sup>|**PROTMODE**<sup>2</sup>|
|**VYHOVUJÍCÍ**|**LOADONCALL**<sup>1</sup>|**ČISTÝ**<sup>1</sup>|
|**DATA**|**LONGNAMES**<sup>2</sup>|**JEN PRO ČTENÍ**|
|**POPIS**|**MOBILNÍ**<sup>1</sup>|**READWRITE**|
|**DEV386**|**LZE PŘESUNOUT**<sup>1</sup>|**PODSLOŽEK REALMODE**<sup>1</sup>|
|**DISCARDABLE**|**VÍCE**|**REZIDENTNÍ**|
|**DYNAMICKÉ**|**JMÉNO**|**RESIDENTNAME**<sup>1</sup>|
|**JEN PRO SPUŠTĚNÍ**|**NEWFILES**<sup>2</sup>|**ODDÍLY**|
|**EXECUTEONLY**|**NODATA**<sup>1</sup>|**SEGMENTY**|
|**EXECUTEREAD**|**NOIOPL**<sup>1</sup>|**SDÍLENÉ**|
|**EXETYPE**|**NONAME**|**JEDEN**|
|**EXPORTY**|**NEODPOVÍDAJÍCÍ**<sup>1</sup>|**VELIKOST ZÁSOBNÍKU**|
|**OPRAVENÉ**<sup>1</sup>|**NONDISCARDABLE**|**ZÁSTUPNÁ PROCEDURA**|
|**FUNKCE**<sup>2</sup>|**NONE**|**VERZE**|
|**VELIKOST HALDY**|**SDÍLENÉM**|**WINDOWAPI**|
|**IMPORTY**|**NOTWINDOWCOMPAT**<sup>1</sup>|**WINDOWCOMPAT**|
|**ZNEČIŠTĚNÁ**<sup>1</sup>|**OBJEKTY**|**WINDOWS**|
|**ZAHRNOUT**<sup>2</sup>|**PŮVODNÍ**<sup>1</sup>||

<sup>1</sup> linkeru vydá upozornění ("Ignorovat"), pokud se setká s tímto výrazem. Je však stále vyhrazené slovo.

<sup>2</sup> linkeru ignoruje slovo ale vysílá bez upozornění.

## <a name="see-also"></a>Viz také:

- [Nastavení možností linkeru](../../build/reference/setting-linker-options.md)
- [Možnosti linkeru](../../build/reference/linker-options.md)