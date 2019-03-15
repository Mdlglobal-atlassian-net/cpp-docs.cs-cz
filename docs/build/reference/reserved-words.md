---
title: Vyhrazená slova
ms.date: 11/04/2016
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
helpviewer_keywords:
- .def files [C++], reserved words
- def files [C++], reserved words
- linker [C++], reserved words
- reserved words [C++]
ms.assetid: 9b9f49e5-0739-45ab-a37e-81e3915ceb25
ms.openlocfilehash: 7d51f599dfb81dfa860e1bdba86c4372e80379fb
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57822441"
---
# <a name="reserved-words"></a>Vyhrazená slova

Tato slova jsou vyhrazena linkerem. Tyto názvy můžete použít jako argumenty v [příkazy definice modulu](module-definition-dot-def-files.md) pouze v případě, že je název uzavřen do dvojitých uvozovek ("").

||||
|-|-|-|
|**OBJEKTU APPLOADER**<sup>1</sup>|**INITINSTANCE –**<sup>2</sup>|**PRELOAD**|
|**ZÁKLAD**|**IOPL**|**PRIVÁTNÍ**|
|**KÓD**|**KNIHOVNA**<sup>1</sup>|**PROTMODE**<sup>2</sup>|
|**VYHOVUJÍCÍ**|**LOADONCALL**<sup>1</sup>|**ČISTĚ**<sup>1</sup>|
|**DATA**|**LONGNAMES**<sup>2</sup>|**READONLY**|
|**POPIS**|**POHYBLIVÉ**<sup>1</sup>|**READWRITE**|
|**DEV386**|**LZE PŘESUNOUT**<sup>1</sup>|**PODSLOŽEK REALMODE**<sup>1</sup>|
|**DISCARDABLE**|**MULTIPLE**|**REZIDENTNÍ**|
|**DYNAMIC**|**JMÉNO**|**RESIDENTNAME**<sup>1</sup>|
|**POUZE PRO SPUŠTĚNÍ**|**NEWFILES**<sup>2</sup>|**ODDÍLY**|
|**EXECUTEONLY**|**NODATA**<sup>1</sup>|**SEGMENTY**|
|**EXECUTEREAD**|**NOIOPL**<sup>1</sup>|**SDÍLET**|
|**EXETYPE**|**NONAME**|**JEDEN**|
|**EXPORTY**|**NEODPOVÍDAJÍCÍ**<sup>1</sup>|**VELIKOST ZÁSOBNÍKU**|
|**OPRAVA**<sup>1</sup>|**NONDISCARDABLE**|**ZÁSTUPNÁ PROCEDURA**|
|**FUNKCE**<sup>2</sup>|**NONE**|**VERZE**|
|**VELIKOST HALDY**|**NESDÍLENÉ**|**WINDOWAPI**|
|**IMPORTY**|**NOTWINDOWCOMPAT**<sup>1</sup>|**WINDOWCOMPAT**|
|**ZNEČIŠTĚNÁ**<sup>1</sup>|**OBJEKTY**|**SYSTÉM WINDOWS**|
|**ZAHRNOUT**<sup>2</sup>|**OLD**<sup>1</sup>||

<sup>1</sup> linkeru vysílá varování ("ignoruje"), pokud se setká s tímto termínem. Je však stále rezervované slovo.

<sup>2</sup> propojovací program ignoruje toto slovo ale vysílá bez upozornění.

## <a name="see-also"></a>Viz také:

- [Odkaz na MSVC linkeru](linking.md)
- [Možnosti Linkeru MSVC](linker-options.md)