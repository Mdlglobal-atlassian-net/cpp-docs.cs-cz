---
title: 'Výměna polí záznamu: Použití funkce RFX'
ms.date: 11/04/2016
helpviewer_keywords:
- RFX (ODBC), implementing
ms.assetid: ada8f043-37e6-4d41-9db3-92c997a61957
ms.openlocfilehash: dc0cdcee758f4842b0738068a8a11c4e2e404155
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367147"
---
# <a name="record-field-exchange-using-rfx"></a>Výměna polí záznamu: Použití funkce RFX

Toto téma vysvětluje, co můžete provést použití RFX ve vztahu k tomu, co provádí rámec.

> [!NOTE]
> Toto téma se vztahuje na třídy odvozené z [CRecordset,](../../mfc/reference/crecordset-class.md) ve kterém hromadné načítání řádků nebyla implementována. Pokud používáte hromadné načítání řádků, je implementována výměna pole hromadného záznamu (Bulk RFX). Hromadné RFX je podobný RFX. Rozdíly najdete v tématu [Sada záznamů: Hromadné načítání záznamů (ODBC).](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)

Následující témata obsahují související informace:

- [Výměna pole záznamu: Práce s kódem průvodce](../../data/odbc/record-field-exchange-working-with-the-wizard-code.md) zavádí hlavní součásti RFX a vysvětluje kód, který Průvodce aplikací knihovny MFC a **Add Class** (jak je popsáno v přidání [příjemce Knihovny MFC ODBC)](../../mfc/reference/adding-an-mfc-odbc-consumer.md)napište na podporu RFX a jak můžete chtít upravit kód průvodce.

- [Výměna pole záznamu: Pomocí funkcí RFX](../../data/odbc/record-field-exchange-using-the-rfx-functions.md) vysvětluje zápis volání `DoFieldExchange` rfx funkce v přepsání.

V následující tabulce jsou uvedeny vaše role ve vztahu k tomu, co rámec dělá pro vás.

### <a name="using-rfx-you-and-the-framework"></a>Použití RFX: Vy a rámec

|Vy|Rámec|
|---------|-------------------|
|Deklarujte třídy sady záznamů pomocí průvodce. Zadejte názvy a datové typy datových členů polí.|Průvodce odvodí třídu `CRecordset` a zapíše přepsání [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) za vás, včetně volání funkce RFX pro každého člena dat pole.|
|(Nepovinné) Ručně přidejte všechny potřebné členy dat parametru do třídy. Ručně přidejte volání funkce `DoFieldExchange` RFX pro každý datový člen parametru, přidejte volání [CFieldExchange::SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype) pro skupinu parametrů a zadejte celkový počet parametrů v [m_nParams](../../mfc/reference/crecordset-class.md#m_nparams). Viz [Sada záznamů: Parametrizace sady záznamů (ODBC).](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)||
|(Nepovinné) Ručně spojte další sloupce s datovými členy pole. Ručně [se](../../mfc/reference/crecordset-class.md#m_nfields)m_nFields . Viz [Sada záznamů: Sloupce dat dynamicky vazby (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).||
|Vytvořte objekt třídy sady záznamů. Před použitím objektu nastavte hodnoty jeho datových členů parametru, pokud existuje.|Pro efektivitu rozhraní předpojit parametry pomocí ROZHRANÍ ODBC. Když předáte hodnoty parametrů, rozhraní je předá zdroji dat. Pouze hodnoty parametrů jsou odesílány pro opakované dotazy, pokud řazení nebo řetězce filtru byly změněny.|
|Otevřete objekt sady záznamů pomocí [sady CRecordset::Open](../../mfc/reference/crecordset-class.md#open).|Provede dotaz sady záznamů, sváže sloupce s datovými členy sady `DoFieldExchange` záznamů a volá k výměně dat mezi prvním vybraným záznamem a datovými členy sady záznamů.|
|Posuňte se v sadě záznamů pomocí [sady CRecordset::Move](../../mfc/reference/crecordset-class.md#move) nebo příkazu nabídky nebo panelu nástrojů.|Volání `DoFieldExchange` přenosu dat do datových členů pole z nového aktuálního záznamu.|
|Přidání, aktualizace a odstranění záznamů|Volání `DoFieldExchange` přenosu dat do zdroje dat.|

## <a name="see-also"></a>Viz také

[Výměna pole záznamu (RFX)](../../data/odbc/record-field-exchange-rfx.md)<br/>
[Výměna polí záznamu: Jak funkce RFX pracuje](../../data/odbc/record-field-exchange-how-rfx-works.md)<br/>
[Sada záznamů: Získávání součtů a jiných agregačních výsledků (ODBC)](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md)<br/>
[CRecordset – třída](../../mfc/reference/crecordset-class.md)<br/>
[CFieldExchange – třída](../../mfc/reference/cfieldexchange-class.md)<br/>
[Makra, globální funkce a globální proměnné](../../mfc/reference/mfc-macros-and-globals.md)
