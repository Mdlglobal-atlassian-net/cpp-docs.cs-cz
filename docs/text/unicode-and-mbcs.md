---
title: Unicode a MBCS
ms.date: 11/04/2016
f1_keywords:
- _mbcs
helpviewer_keywords:
- MBCS [C++], Unicode
- MFC [C++], character sets
- character sets [C++], multibyte
- run-time libraries [C++], language portability
- character sets [C++], Unicode
- Unicode [C++], MFC and C run-time functions
- multibyte characters [C++]
- runtime [C++], language portability
ms.assetid: 677baec6-71b4-4579-94df-64f18bc117c4
ms.openlocfilehash: 5883dcce5c290b197dcaa61296eb2f44f3bb882c
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/11/2019
ms.locfileid: "57741824"
---
# <a name="unicode-and-mbcs"></a>Unicode a MBCS

Knihovny Microsoft Foundation Classes (MFC), knihovny run-time jazyka C pro Visual C++ a vývojové prostředí Visual C++ jsou povolené pomáhat mezinárodní programování. Poskytují:

- Podpora standardu Unicode na Windows. Znaková sada Unicode je aktuálním standardem a měla by být použita vždy, kdy je to možné.

   Kódování Unicode je 16bitový znak kódování, poskytuje dostatek kódování pro všechny jazyky. Všechny znaky ASCII jsou zahrnuty v kódování Unicode, jako rozšířené znaky.

- Podpora pro formuláře vícebajtové znakové sady (MBCS s) názvem dvoubajtové znakové sady (DBCS) na všech platformách.

   Znaky DBCS se skládají z 1 nebo 2 bajty. Některé rozsahů bajtů jsou vyhrazeny pro použití jako úvodní bajty. Vedoucí bajt určuje, že ho a následující bajt tvoří jeden znak 2 bajty dlouhý. Musí udržovat přehled o které bajty jsou vedoucí bajty. V konkrétní vícebajtové znakové sady úvodní bajty spadají do určitého rozsahu, stejně jako záznam pro bajty. Pokud tyto rozsahy překrývají, může být nutné vyhodnotit kontextu k určení, zda je dané bajtové funguje jako vedoucí bajt nebo druhý bajt.

- Podpora pro nástroje, které zjednodušují programování znakové sady MBCS aplikací určených pro mezinárodní trhy.

   Při spuštění na znakové sady MBCS povolené verzi operačního systému Windows, vývoj pro systém Visual C++ – včetně integrovaného editoru zdrojového kódu, ladicí program a nástroje příkazového řádku, je zcela znakové sady MBCS povolen. Další informace najdete v tématu [podporu znakové sady MBCS v jazyku Visual C++](../text/mbcs-support-in-visual-cpp.md).

> [!NOTE]
>  V této dokumentaci znakové sady MBCS slouží k popisu veškerou podporu kódování Unicode pro vícebajtové znaky. Znakové sady MBCS v jazyce Visual C++ vždy znamená DBCS. Znakových sad větší než 2 bajty nejsou podporovány.

Podle definice je znaková sada ASCII podmnožinou všech vícebajtových znakových sad. V mnoha vícebajtové znakové sady každý znak v rozsahu 0x00 – 0x7F je stejný jako znak, který má stejnou hodnotu ve znakové sadě ASCII. V řetězce znaků ASCII a znakové sady MBCS, například 1bajtových znak NULL ('\0') má hodnotu 0x00 a označuje ukončujícího znaku null.

## <a name="see-also"></a>Viz také:

[Text a řetězce](../text/text-and-strings-in-visual-cpp.md)<br/>
[Podpora národních prostředí](../text/international-enabling.md)
