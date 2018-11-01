---
title: 'Datum a čas: Podpora automatizace'
ms.date: 11/04/2016
helpviewer_keywords:
- adding dates
- calculating dates and times
- formatting [Visual Studio], dates
- dates, Automation support
- elapsed time, calculating in Automation
- COleDateTime class, Automation date/time support
- COleDateTimeSpan class, Automation date/time support
- Automation, date and time support
- formatting [Visual Studio], time
- calculations, date and time
- time [Visual Studio], Automation support
ms.assetid: 6eee94c4-943d-4ffc-bf7c-bdda89337ab0
ms.openlocfilehash: 5aeefe2594fcb71e8b399e017fc10f8c1c5650a6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50552682"
---
# <a name="date-and-time-automation-support"></a>Datum a čas: Podpora automatizace

Tento článek popisuje, jak využít výhod služeb knihovny třídy související se správou data a času. Popsané postupy zahrnují:

- [Získání aktuálního času](../atl-mfc-shared/current-time-automation-classes.md)

- [Výpočet uplynulého času](../atl-mfc-shared/elapsed-time-automation-classes.md)

- [Formátování řetězcovou reprezentaci data a času](../atl-mfc-shared/formatting-time-automation-classes.md)

[COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md) třída poskytuje způsob, jak reprezentaci informace o datu a času. Poskytuje rozlišovací schopnosti a větší rozsah než [CTime](../atl-mfc-shared/reference/ctime-class.md) třídy. [Coledatetimespan –](../atl-mfc-shared/reference/coledatetimespan-class.md) třída reprezentuje uplynulého času, jako je rozdíl mezi dvěma `COleDateTime` objekty.

`COleDateTime` a `COleDateTimeSpan` třídy jsou navrženy tak, která se použije `COleVariant` Třída použitá ve službě Automation. `COleDateTime` a `COleDateTimeSpan` jsou také užitečná při programování knihovny MFC databáze, ale lze je použít kdykoli budete chtít pracovat s hodnotami data a času. I když `COleDateTime` třída má větší rozsah hodnot a rozlišovací schopnosti než `CTime` třídy, vyžaduje další úložiště na objekt, než `CTime`. Nejsou zde také některé speciální aspekty při práci s podkladovým typem datum. Zobrazit [typ data](../atl-mfc-shared/date-type.md) podrobné informace o provádění datum.

`COleDateTime` objekty lze použít k reprezentaci kalendářní data mezi 1 leden 100 až 31. prosince 9999. `COleDateTime` objekty jsou hodnoty plovoucího bodu, s rozlišením přibližně 1 milisekunda. `COleDateTime` je založen na datový typ DATE definované v dokumentaci knihovny MFC v [COleDateTime::operator datum](../atl-mfc-shared/reference/coledatetime-class.md#operator_date). Skutečná implementace datum se rozpíná za tyto hranice. `COleDateTime` Implementace má tyto hranice pro usnadnění práce s třídou.

`COleDateTime` nepodporuje juliánský data. Gregoriánský kalendář je považován za rozšíření zpět v čase do 1. leden 100.

`COleDateTime` ignoruje letního času (DST). Následující příklad kódu porovná dvě metody pro výpočet časový interval, který překročí datum letního času přepnutí: jeden pomocí CRT a na další pomocí `COleDateTime`. Letního času se přepne, ve většině prostředí, druhý týden v dubnu na trh a třetí v říjnu.

První metoda nastaví `CTime` objekty, *čas1* a *time2*, duben 5 a 6. dubna, pomocí standardního typu struktury C `tm` a `time_t`. Zobrazení kódu *čas1* a *time2* a časový rozsah mezi nimi.

Druhá metoda vytvoří dva `COleDateTime` objekty, `oletime1` a `oletime2`a nastaví na stejná data jako *čas1* a *time2*. Zobrazí se `oletime1` a `oletime2` a časový rozsah mezi nimi.

CRT správně vypočítá rozdíl ve 23 hodin. `COleDateTimeSpan` vypočítá rozdíl 24 hodin.

[!code-cpp[NVC_ATLMFC_Utilities#176](../atl-mfc-shared/codesnippet/cpp/date-and-time-automation-support_1.cpp)]

## <a name="see-also"></a>Viz také

[Datum a čas](../atl-mfc-shared/date-and-time.md)
