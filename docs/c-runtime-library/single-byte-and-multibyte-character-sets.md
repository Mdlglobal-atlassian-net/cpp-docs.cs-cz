---
title: Jednobajtové a vícebajtové znakové sady
ms.date: 11/04/2016
f1_keywords:
- c.character.multibyte
helpviewer_keywords:
- SBCS (single byte character set)
- MBCS [C++], about MBCS
- character sets [C++], multibyte
- character sets [C++], single byte
ms.assetid: 2cbc78ea-33c0-4cfb-b0df-7ce2458431ce
ms.openlocfilehash: 1e2d3f26891257101b4a9511f4e0b10f03113309
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/11/2019
ms.locfileid: "57745324"
---
# <a name="single-byte-and-multibyte-character-sets"></a>Jednobajtové a vícebajtové znakové sady

Znaková sada ASCII definuje znaky v rozsahu 0x00 – 0x7F. Existuje mnoho jiných množin znaků, především jazyky, které definují znaky v rozsahu 0x00 – 0x7F stejně jako na znak ASCII nastavit a také definovat rozšířené znakové sadě od 0x80 – 0xFF. Proto 8 bitů, jedním jednobajtového znaku sady (SBCS) je dostačující k reprezentaci znakové sady ASCII, jakož i znakových sad mnoha evropských jazyků. Ale některé neevropské znakových sad, jako je například japonská Kanji obsahovat mnoho více znaků, než je možné znázornit na schéma kódování jednobajtové a proto vyžadují vícebajtové znakové sady (MBCS s) kódováním.

> [!NOTE]
> Mnoho SBCS rutin v knihovně Microsoft za běhu zpracování vícebajtových bajtů, znaků a řetězce podle potřeby. Mnoho vícebajtových znakových sad definovat sadu jako podmnožinu znaků ASCII. V mnoha vícebajtové znakové sady každý znak v rozsahu 0x00 – 0x7F je stejný jako znak, který má stejnou hodnotu ve znakové sadě ASCII. V řetězce znaků ASCII a znakové sady MBCS, například jeden bajtové znak null ('\0') má hodnotu 0x00 a označuje ukončujícího znaku null.

Vícebajtové znakové sady může obsahovat jednobajtových a dvoubajtových znaků. Řetězec vícebajtového znaku zakončeného proto může obsahovat kombinaci jednobajtových a dvoubajtových znaků. Dvoubajtový vícebajtový znak je vedoucí bajt a druhý bajt. V konkrétní vícebajtové znakové sady úvodní bajty spadají do určitého rozsahu, stejně jako záznam pro bajty. Pokud tyto rozsahy překrývají, může být potřeba vyhodnotit konkrétní kontext k určení, zda je dané bajtové funguje jako vedoucí bajt nebo druhý bajt.

## <a name="see-also"></a>Viz také:

[Internacionalizace](../c-runtime-library/internationalization.md)<br/>
[Rutiny UCRT (Universal C runtime) podle kategorie](../c-runtime-library/run-time-routines-by-category.md)<br/>
