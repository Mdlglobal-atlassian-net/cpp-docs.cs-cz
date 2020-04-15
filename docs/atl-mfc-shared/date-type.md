---
title: Typ DATE
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
ms.openlocfilehash: 6fd9fde83474ff4f439c0dd3989d4dc35fe1241a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317923"
---
# <a name="date-type"></a>Typ DATE

Typ DATE je implementován pomocí osmibajtového čísla s plovoucí desetinnou desetinnou desetinnou desetinnou. Dny jsou reprezentovány přírůstky celého čísla počínaje 30. Hodinové hodnoty jsou vyjádřeny jako absolutní hodnota zlomkové části čísla. Následující tabulka ilustruje několik dat spolu s jejich číselným ekvivalentem typu DATE:

|Datum a čas|Reprezentace|
|-------------------|--------------------|
|30. prosince 1899, půlnoc|0,00|
|1. ledna 1900, půlnoc|2,00|
|4. ledna 1900, půlnoc|5.00|
|4. ledna 1900, 6:00|5.25|
|4. ledna 1900, poledne|5.50|
|4. ledna 1900, 21.00 hod.|5.875|

Typ data data data a `COleDateTime` třída představují data a časy jako klasický číselný řádek. Třída `COleDateTime` obsahuje několik metod pro manipulaci s hodnotami DATE, včetně převodu do a z jiných běžných formátů kalendářních dat.

Při práci s těmito formáty data a času v automatizaci je třeba poznamenat následující body:

- Data jsou určena v místním čase; synchronizace musí být provedena ručně při práci s daty v různých časových pásmech.

- Typy dat neúčtují letní čas.

- Časová osa data se stane nespojitou pro hodnoty kalendářních dat menší než 0 (před 30. prosince 1899). Důvodem je, že celá část data hodnoty je považována za podepsanou, zatímco zlomková část je považována za nepodepsanou. Jinými slovy, celá část hodnoty data může být kladná nebo záporná, zatímco zlomková část hodnoty data je vždy přidána k celkovému logickému datu. Následující tabulka ilustruje několik příkladů:

|Datum a čas|Reprezentace|
|-------------------|--------------------|
|27. prosince 1899, půlnoc|-3.00|
|28. prosince 1899, poledne|-2.50|
|28. prosince 1899, půlnoc|-2.00|
|29. prosince 1899, půlnoc|-1.00|
|30. prosince 1899, 18:00|-0.75|
|30. prosince 1899, poledne|-0.50|
|30. prosince 1899, 6:00|-0.25|
|30. prosince 1899, půlnoc|0,00|
|30. prosince 1899, 6:00|0,25|
|30. prosince 1899, poledne|0,50|
|30. prosince 1899, 18:00|0.75|
|31. prosince 1899, půlnoc|1,00|
|1. ledna 1900, půlnoc|2,00|
|1. ledna 1900, poledne|2.50|
|2. ledna 1900, půlnoc|3,00|

> [!CAUTION]
> Všimněte si, že vzhledem k tomu, že 6:00 AM je vždy reprezentován zlomkové hodnoty 0,25 bez ohledu na to, zda celé číslo představující den je pozitivní (po 30. prosince, 1899) nebo negativní (před 30. prosince1899), jednoduché srovnání s plovoucí desetinnou desetinnou desetinnou desetinnou desetinnou desetinnou hodnotou by chybně řadit jakékoli DATUM představující 6:00 AM o den dříve než 12/30/1899 jako *pozdější* než DATUM představující 7:00 AM téhož dne.

Další informace o problémech `COleDateTime` týkajících se data a typů naleznete v části [COleDateTime Class](../atl-mfc-shared/reference/coledatetime-class.md) a [Date and Time: Automation Support](../atl-mfc-shared/date-and-time-automation-support.md).

## <a name="see-also"></a>Viz také

[Datum a čas](../atl-mfc-shared/date-and-time.md)<br/>
[COleDateTime – třída](../atl-mfc-shared/reference/coledatetime-class.md)
