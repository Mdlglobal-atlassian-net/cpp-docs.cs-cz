---
title: Jednobajtové a vícebajtové znakové sady
ms.date: 11/04/2016
helpviewer_keywords:
- SBCS (single byte character set)
- MBCS [C++], about MBCS
- character sets [C++], multibyte
- character sets [C++], single byte
ms.assetid: 2cbc78ea-33c0-4cfb-b0df-7ce2458431ce
ms.openlocfilehash: a6a0f3aaaa463297b7c51b035acc7b2f4a40b6cf
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79444647"
---
# <a name="single-byte-and-multibyte-character-sets"></a>Jednobajtové a vícebajtové znakové sady

Znaková sada ASCII definuje znaky v rozsahu 0x00-0x7F. K dispozici je řada dalších znakových sad, hlavně z nich, které definují znaky v rozsahu 0x00-0x7F identicky se znakovou sadou ASCII a také definují rozšířenou znakovou sadu z 0x80-0xFF. Proto je 8bitové vícebajtové znakové sady (SBCS) dostačující pro reprezentaci znakové sady ASCII a také znakové sady pro mnoho evropských jazyků. Některé neevropské znakové sady, jako je například japonské písmo Kanji, obsahují mnoho dalších znaků, než lze reprezentovat v rámci schématu kódování založeného na jednobajtových, a proto vyžadují kódování vícebajtových znakových sad (MBCS).

> [!NOTE]
> Mnohé rutiny SBCS v knihovně run-time společnosti Microsoft zpracovávají vícebajtové bajty, znaky a řetězce podle potřeby. Mnoho vícebajtových znakových sad definuje znakovou sadu ASCII jako podmnožinu. V mnoha vícebajtových znakových sadách je každý znak v rozsahu 0x00-0x7F stejný jako znak, který má stejnou hodnotu jako znaková sada ASCII. Například v řetězcích znaků ASCII a MBCS má jednobajtové znak null (' \ 0 ') hodnotu 0x00 a označuje ukončující znak null.

Vícebajtová znaková sada se může skládat z jednoho bajtu a dvoubajtových znaků. Proto řetězec vícebajtových znaků může obsahovat kombinaci jednobajtových a dvoubajtových znaků. Vícebajtový znak se dvěma bajty má vedoucí bajt a koncový bajt. V určité vícebajtové znakové sadě spadají vedoucí bajty do určitého rozsahu, stejně jako v případě koncových bajtů. Pokud se tyto rozsahy překrývají, může být nutné vyhodnotit konkrétní kontext, aby bylo možné zjistit, zda daný bajt funguje jako vedoucí bajt nebo koncový bajt.

## <a name="see-also"></a>Viz také

[Internacionalizace](../c-runtime-library/internationalization.md)<br/>
[Rutiny UCRT (Universal C runtime) podle kategorie](../c-runtime-library/run-time-routines-by-category.md)<br/>
