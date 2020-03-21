---
title: 'Výměna polí záznamu: Použití funkce RFX'
ms.date: 11/04/2016
helpviewer_keywords:
- RFX (ODBC), implementing
ms.assetid: ada8f043-37e6-4d41-9db3-92c997a61957
ms.openlocfilehash: 70197d2a9130388e86bb94f0d670360bb35febeb
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80075871"
---
# <a name="record-field-exchange-using-rfx"></a>Výměna polí záznamu: Použití funkce RFX

Toto téma vysvětluje, co uděláte k použití RFX ve vztahu k čemu rozhraní.

> [!NOTE]
>  Toto téma se vztahuje na třídy odvozené od [CRecordset](../../mfc/reference/crecordset-class.md) , ve kterých nebylo implementováno hromadné načítání řádků. Používáte-li hromadné načítání řádků, je implementováno hromadné výměny pole záznamu (Bulk RFX). Hromadná RFX je podobná RFX. Pro pochopení rozdílů si přečtěte téma [Sada záznamů: hromadné načítání záznamů (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Následující témata obsahují související informace:

- [Výměna polí záznamu: práce s kódem průvodce](../../data/odbc/record-field-exchange-working-with-the-wizard-code.md) zavádí hlavní komponenty RFX a vysvětluje kód, který průvodce aplikací knihovny MFC a **přidal třídu** (jak je popsáno v tématu [Přidání příjemce knihovny MFC rozhraní ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)) pro podporu RFX a způsob, jakým můžete chtít upravit kód průvodce.

- [Výměna polí záznamu: použití funkcí RFX](../../data/odbc/record-field-exchange-using-the-rfx-functions.md) vysvětluje zápis volání funkcí RFX ve vašem `DoFieldExchange` přepsání.

V následující tabulce je uvedena vaše role s ohledem na to, co rozhraní dělá.

### <a name="using-rfx-you-and-the-framework"></a>Použití RFX: vy a rozhraní

|Vy|Rozhraní .NET Framework|
|---------|-------------------|
|Deklarujte své třídy sady záznamů pomocí průvodce. Zadejte názvy a datové typy datových členů polí.|Průvodce odvodí třídu `CRecordset` a zapisuje pro vás přepsání [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) , včetně volání funkce RFX pro každý datový člen pole.|
|Volitelné Ručně přidejte všechny potřebné datové členy parametru do třídy. Ručně přidejte volání funkce RFX pro `DoFieldExchange` pro každý datový člen parametru, přidejte volání parametru [CFieldExchange:: SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype) pro skupinu parametrů a zadejte celkový počet parametrů v [m_nParams](../../mfc/reference/crecordset-class.md#m_nparams). Viz [Sada záznamů: Parametrizace sady záznamů (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).||
|Volitelné Ruční navázání dalších sloupců k polím datových členů. Ruční zvýšení [m_nFields](../../mfc/reference/crecordset-class.md#m_nfields). Viz [Sada záznamů: dynamické vazby datových sloupců (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).||
|Vytvořte objekt třídy sady záznamů. Před použitím objektu nastavte hodnoty svých datových členů parametru, pokud existují.|V rámci efektivity rozhraní předváže parametry pomocí rozhraní ODBC. Když předáte hodnoty parametru, rozhraní je předá do zdroje dat. Pro redotazování se odesílají jenom hodnoty parametrů, pokud se nezměnily řetězce řazení nebo filtrování.|
|Otevřete objekt sady záznamů pomocí [CRecordset:: Open](../../mfc/reference/crecordset-class.md#open).|Provede dotaz sady záznamů, váže sloupce na pole datových členů sady záznamů a volá `DoFieldExchange` k výměně dat mezi prvním vybraným záznamem a datovými členy pole sady záznamů.|
|Posuňte se v sadě záznamů pomocí příkazu [CRecordset:: Move](../../mfc/reference/crecordset-class.md#move) nebo nabídky nebo panelu nástrojů.|Volá `DoFieldExchange` pro přenos dat do datových členů pole z nového aktuálního záznamu.|
|Přidávání, aktualizace a odstraňování záznamů.|Volá `DoFieldExchange` pro přenos dat do zdroje dat.|

## <a name="see-also"></a>Viz také

[Výměna polí záznamu (Record Field Exchange – RFX)](../../data/odbc/record-field-exchange-rfx.md)<br/>
[Výměna polí záznamu: Jak funkce RFX pracuje](../../data/odbc/record-field-exchange-how-rfx-works.md)<br/>
[Sada záznamů: Získávání součtů a jiných souhrnných výsledků (ODBC)](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md)<br/>
[CRecordset – třída](../../mfc/reference/crecordset-class.md)<br/>
[CFieldExchange – třída](../../mfc/reference/cfieldexchange-class.md)<br/>
[Makra, globální funkce a globální proměnné](../../mfc/reference/mfc-macros-and-globals.md)
