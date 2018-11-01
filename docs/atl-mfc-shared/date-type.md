---
title: DATE – typ
ms.date: 11/04/2016
f1_keywords:
- DATE
helpviewer_keywords:
- Date data type, implementing
- Date data type
- DATE type
- Date data type, about Date data type
- MFC, date and time
- hour values representation
ms.assetid: 695853ed-b614-4575-b793-b8c287372038
ms.openlocfilehash: b8460d50a0c6cbd4b213e45c62d8d6cadae68544
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50548184"
---
# <a name="date-type"></a>DATE – typ

DATOVÝ typ je implementována pomocí čísla s plovoucí desetinnou čárkou 8 bajtů. Dny jsou reprezentovány přírůstky celé číslo počínaje 30. prosince 1899, půlnoci jako čase nula. Hodnoty hodin jsou vyjádřeny jako absolutní hodnotu desetinnou část čísla. Následující tabulka ukazuje několik dat spolu s jejich číselný ekvivalent typu datum:

|Datum a čas|Reprezentace|
|-------------------|--------------------|
|30. prosince 1899, půlnoci|0.00|
|1. ledna 1900 půlnoci|2.00|
|4. ledna 1900 půlnoci|5.00|
|4. ledna 1900, 6: 00|5.25|
|4. ledna 1900 poledne|5.50|
|4. ledna 1900, 9 do 21 hodin|5.875|

Datový typ datum, jakož i `COleDateTime` třídy, představuje data a času jako klasický číslo řádku. `COleDateTime` Třída obsahuje několik metod pro práci s hodnotami data, včetně převodu do a z jiné běžné formáty kalendářního data.

Při práci s tyto formáty data a času ve službě Automation potřeba poznamenat následující body:

- Data jsou určené v místním čase; synchronizace je nutné provést ručně při práci s daty v různých časových pásmech.

- Typy datum není účtu údržby pro letní čas.

- Časová osa datum stane jednorázová pro hodnoty data menší než 0. (před 1899 30. prosince). Důvodem je, že část celé číslo hodnoty date je považován za podepsaný, zatímco je zpracováván zlomkové části bez znaménka. Jinými slovy celé číslo části hodnoty date pravděpodobně kladné nebo záporné, zatímco zlomkovou část hodnoty date je vždy přidán k datu Celková logická. Následující tabulka ukazuje několik příkladů:

|Datum a čas|Reprezentace|
|-------------------|--------------------|
|27. prosince 1899, půlnoci|-3.00|
|28. dne 1899 poledne|-2.50|
|28. dne 1899, půlnoci|-2.00|
|29. prosince 1899, půlnoci|-1.00|
|30. prosince 1899, 18: 00|-0.75|
|30. prosince 1899 poledne|-0.50|
|30. prosince 1899, 6: 00|-0.25|
|30. prosince 1899, půlnoci|0.00|
|30. prosince 1899, 6: 00|0.25|
|30. prosince 1899 poledne|0.50|
|30. prosince 1899, 18: 00|0.75|
|31. prosince 1899, půlnoci|1.00|
|1. ledna 1900 půlnoci|2.00|
|1. ledna 1900 poledne|2.50|
|2. ledna 1900 půlnoci|3.00|

> [!CAUTION]
>  Upozorňujeme, že 6:00:00 je vždy označena desetinná hodnota 0,25 bez ohledu na to, zda je kladné celé číslo představující den (po 30. prosince 1899) nebo záporná (před 30. prosince 1899), jednoduché plovoucího bodu porovnání by chybně řazení DATA představující 6:00 RÁNO dne starší než 12/30/1899 jako *později* datu představující 7:00 hodin v daný den stejné.

Další informace o problémy související s datem a `COleDateTime` typy najdete v části [COleDateTime – třída](../atl-mfc-shared/reference/coledatetime-class.md) a [datum a čas: Podpora automatizace](../atl-mfc-shared/date-and-time-automation-support.md).

## <a name="see-also"></a>Viz také

[Datum a čas](../atl-mfc-shared/date-and-time.md)<br/>
[COleDateTime – třída](../atl-mfc-shared/reference/coledatetime-class.md)

