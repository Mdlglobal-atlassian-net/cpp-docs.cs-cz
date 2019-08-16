---
title: Datum a čas
ms.date: 08/13/2019
helpviewer_keywords:
- time, MFC programming
- time
- MFC, date and time
- dates, MFC
ms.assetid: ecf56dc5-d418-4603-ad3e-af7e205a6403
ms.openlocfilehash: 2a5e6977acfca51b8074399f6f9b3166c8a358bc
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491300"
---
# <a name="date-and-time"></a>Datum a čas

Knihovna MFC podporuje několik různých způsobů práce s daty a časy:

- Podpora [datového typu data](../atl-mfc-shared/date-type.md)Automation. Datum podporuje hodnoty data, času a data a času. Třídy [COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md) a [COleDateTimeSpan](../atl-mfc-shared/reference/coledatetimespan-class.md) zapouzdřují tuto funkci. Pracují s třídou [COleVariant](../mfc/reference/colevariant-class.md) s využitím podpory automatizace.

- Třídy času pro obecné účely. Třídy [CTime –](../atl-mfc-shared/reference/ctime-class.md) a [CTimeSpan](../atl-mfc-shared/reference/ctimespan-class.md) zapouzdřují většinu funkcí přidružených k běhové knihovně standardu ANSI, která je deklarována v čase. Y.

- Podpora systémových hodin. V `CTime` případě knihovny MFC verze 3,0 byla přidána podpora pro Win32 `SYSTEMTIME` a `FILETIME` datové typy.

## <a name="date-and-time-automation-support"></a>Datum a čas: Podpora automatizace

Třída [COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md) poskytuje způsob, jak vyjádřit informace o datu a čase. Poskytuje jemnější členitost a větší rozsah než třída [CTime –](../atl-mfc-shared/reference/ctime-class.md) . Třída [COleDateTimeSpan](../atl-mfc-shared/reference/coledatetimespan-class.md) představuje uplynulý čas, jako je například rozdíl mezi dvěma `COleDateTime` objekty.

Třídy `COleDateTime` a `COleDateTimeSpan` jsou`COleVariant` určeny pro použití s třídou. `COleDateTime`a `COleDateTimeSpan` jsou také užitečné v programování databáze knihovny MFC, ale lze je použít vždy, když chcete manipulovat s hodnotami data a času. I když má `CTime` `CTime`třída větší rozsah hodnot a jemnější členitost než třída, vyžaduje větší úložiště na objekt než. `COleDateTime` Při práci s podkladovým typem dat existují také zvláštní požadavky. Další informace o implementaci data najdete v tématu [Typ data](../atl-mfc-shared/date-type.md).

`COleDateTime`objekty lze použít k reprezentaci dat mezi 1. ledna 100 a 31. prosince 9999. `COleDateTime`objekty jsou hodnoty s plovoucí desetinnou čárkou, které mají přibližnou přesnost 1 milisekundu. `COleDateTime`je založena na datovém typu DATE definované v dokumentaci knihovny MFC pod [daty COleDateTime:: operator](../atl-mfc-shared/reference/coledatetime-class.md#operator_date). Skutečná implementace data překračuje tyto hranice. `COleDateTime` Implementace ukládá tyto hranice, aby bylo snazší pracovat se třídou.

`COleDateTime`nepodporuje juliánské data. Předpokládá se, že gregoriánský kalendář bude prodloužen zpátky v čase do 1. ledna 100.

`COleDateTime`ignoruje letní čas (DST). Následující příklad kódu porovnává dvě metody výpočtu časového rozsahu, který překračuje datum přepnutí do LETNÍho času: jeden pomocí CRT a druhý pomocí `COleDateTime`.

První metoda nastaví dva `CTime` objekty, *time1* a *time2*, do 5. dubna v uvedeném pořadí, pomocí standardních struktur `tm` typu C a. `time_t` Kód zobrazuje *time1* a *time2* a časový rozsah mezi nimi.

Druhá metoda vytvoří dva `COleDateTime` objekty `oletime2`, `oletime1` a nastaví je na stejná data jako *time1* a *time2*. Zobrazuje `oletime1` a`oletime2` časová rozpětí mezi nimi.

CRT správně počítá rozdíl 23 hodin. `COleDateTimeSpan`vypočítá rozdíl 24 hodin.

[!code-cpp[NVC_ATLMFC_Utilities#176](../atl-mfc-shared/codesnippet/cpp/date-and-time-automation-support_1.cpp)]

### <a name="get-the-current-time"></a>Získat aktuální čas

Následující postup ukazuje, jak vytvořit `COleDateTime` objekt a inicializovat ho s aktuálním časem.

#### <a name="to-get-the-current-time"></a>Získání aktuálního času

1. `COleDateTime` Vytvořte objekt.

1. Volání `GetCurrentTime`.

   [!code-cpp[NVC_ATLMFC_Utilities#177](../atl-mfc-shared/codesnippet/cpp/current-time-automation-classes_1.cpp)]

### <a name="calculate-elapsed-time"></a>Vypočítat uplynulý čas

Tento postup ukazuje, jak vypočítat rozdíl mezi dvěma `COleDateTime` objekty a `COleDateTimeSpan` získat výsledek.

#### <a name="to-calculate-elapsed-time"></a>Výpočet uplynulého času

1. Vytvořte dva `COleDateTime` objekty.

1. Nastavte jeden z `COleDateTime` objektů na aktuální čas.

1. Proveďte nějakou časově náročnou úlohu.

1. Nastavte druhý `COleDateTime` objekt na aktuální čas.

1. Pořídit rozdíl mezi dvěma časy.

   [!code-cpp[NVC_ATLMFC_Utilities#178](../atl-mfc-shared/codesnippet/cpp/elapsed-time-automation-classes_1.cpp)]

### <a name="format-a-time"></a>Formátování času

#### <a name="to-format-a-time"></a>Formátování času

Použijte členskou funkci buď COleDateTime nebo [COleDateTimeSpan](../atl-mfc-shared/reference/coledatetimespan-class.md) , k vytvoření řetězce znaků představujícího čas nebo uplynulý čas. [](../atl-mfc-shared/reference/coledatetime-class.md) `Format`

   [!code-cpp[NVC_ATLMFC_Utilities#179](../atl-mfc-shared/codesnippet/cpp/formatting-time-automation-classes_1.cpp)]

Další informace najdete v tématu Třída [COleVariant](../mfc/reference/colevariant-class.md).

## <a name="date-and-time-database-support"></a>Datum a čas: Podpora databáze

Počínaje verzí 4,0, programování databáze knihovny MFC používá třídy [COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md) a [COleDateTimeSpan](../atl-mfc-shared/reference/coledatetimespan-class.md) k reprezentaci dat data a času. Tyto třídy, které se používají také v automatizaci, jsou odvozeny z třídy [COleVariant](../mfc/reference/colevariant-class.md). Poskytují lepší podporu pro správu dat data a času než do [CTime –](../atl-mfc-shared/reference/ctime-class.md) a [CTimeSpan](../atl-mfc-shared/reference/ctimespan-class.md).

## <a name="date-and-time-systemtime-support"></a>Datum a čas: Podpora SYSTEMTIME –

Třída [COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md) má konstruktory, které přijímají časy systému a souboru z Win32.

Struktura Win32 `FILETIME` představuje čas jako 64ovou hodnotu. Je to pohodlnější formát pro interní úložiště než `SYSTEMTIME` struktura a formát používaný systémem Win32 k vyjádření času vytvoření souboru. Informace o struktuře SYSTEMTIME – naleznete v tématu [SYSTEMTIME –](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime). Informace o struktuře času v nástroji najdete v tématu [čas](/windows/desktop/api/minwinbase/ns-minwinbase-filetime).

## <a name="see-also"></a>Viz také:

[Charakteristiky](../mfc/mfc-concepts.md)\
[Obecná témata MFC](../mfc/general-mfc-topics.md)
