---
title: Unicode a MBCS
ms.date: 11/04/2016
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
ms.openlocfilehash: 063c8b39ee0d29403b382b57a236f2a3e8759e3f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375744"
---
# <a name="unicode-and-mbcs"></a>Unicode a MBCS

Knihovna Tříd y Microsoft Foundation (MFC), knihovna C run-time pro visual c++ a vývojové prostředí Visual C++ jsou povoleny pro mezinárodní programování. Čím se vyznačují:

- Podpora standardu Unicode v systému Windows. Znaková sada Unicode je aktuálním standardem a měla by být použita vždy, kdy je to možné.

   Unicode je 16bitové kódování znaků, které poskytuje dostatek kódování pro všechny jazyky. Všechny znaky ASCII jsou zahrnuty v Unicode jako rozšířené znaky.

- Podpora pro formu vícebajtové znakové sady (MBCS) nazývané dvoubajtová znaková sada (DBCS) na všech platformách.

   Znaky DBCS se skládají z 1 nebo 2 bajtů. Některé rozsahy bajtů jsou vyhrazeny pro použití jako olověné bajty. Úvodní bajt určuje, že jej a následující bajt stopy tvoří jeden znak o 2 bajtů. Je nutné sledovat, které bajty jsou úvodní bajty. V určité vícebajtové znakové sadě spadají úvodní bajty do určitého rozsahu, stejně jako bajty stopy. Pokud se tyto rozsahy překrývají, může být nutné vyhodnotit kontext k určení, zda daný bajt funguje jako úvodní bajt nebo bajt stopy.

- Podpora nástrojů, které zjednodušují mbcs programování aplikací napsaných pro mezinárodní trhy.

   Při spuštění na verzi operačního systému Windows s podporou mbcs je vývojový systém Visual C++ – včetně integrovaného editoru zdrojového kódu, ladicího programu a nástrojů příkazového řádku – zcela povolen mbcs. Další informace naleznete [v tématu Podpora mbcs ve visual c++](../text/mbcs-support-in-visual-cpp.md).

> [!NOTE]
> V této dokumentaci mbcs slouží k popisu všech non-Unicode podporu pro vícebajtové znaky. V jazyce Visual C++ mbcs vždy znamená DBCS. Znakové sady širší než 2 bajty nejsou podporovány.

Podle definice je znaková sada ASCII podmnožinou všech vícebajtových znakových sad. V mnoha vícebajtových znakových sadách je každý znak v rozsahu 0x00 - 0x7F shodný se znakem, který má stejnou hodnotu v znakové sadě ASCII. Například v řetězcích znaků ASCII i MBCS má znak NULL o 1 bajty (\0) hodnotu 0x00 a označuje ukončující znak null.

## <a name="see-also"></a>Viz také

[Text a řetězce](../text/text-and-strings-in-visual-cpp.md)<br/>
[Podpora národních prostředí](../text/international-enabling.md)
