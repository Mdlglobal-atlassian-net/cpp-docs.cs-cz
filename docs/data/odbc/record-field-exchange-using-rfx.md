---
title: 'Výměna polí záznamu: Použití funkce RFX'
ms.date: 11/04/2016
helpviewer_keywords:
- RFX (ODBC), implementing
ms.assetid: ada8f043-37e6-4d41-9db3-92c997a61957
ms.openlocfilehash: 2a029f653753363e08b3c4f8b9fceab6295924af
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59034112"
---
# <a name="record-field-exchange-using-rfx"></a>Výměna polí záznamu: Použití funkce RFX

Toto téma vysvětluje, co udělat, abyste použití funkce RFX ve vztahu k čemu rozhraní framework.

> [!NOTE]
>  Toto téma platí pro třídy odvozené od [CRecordset](../../mfc/reference/crecordset-class.md) v který řádek hromadné načítání není implementovaná. Pokud používáte hromadné načítání řádků, je implementováno Hromadná výměna pole záznamu (Bulk RFX). Hromadné funkce RFX je podobný RFX. Pokud chcete znát rozdíly, přečtěte si téma [sada záznamů: Načítání záznamů (ODBC) hromadné](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Následující témata obsahují informace související:

- [Výměna polí záznamu: Práce s kódem průvodce](../../data/odbc/record-field-exchange-working-with-the-wizard-code.md) představuje hlavní komponenty RFX a vysvětluje, kód, který Průvodce aplikací knihovny MFC a **přidat třídu** (jak je popsáno v [přidání příjemce ODBC knihovny MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)) zápis Podpora RFX a jak můžete chtít změnit kód průvodce.

- [Výměna polí záznamu: Použití funkcí RFX](../../data/odbc/record-field-exchange-using-the-rfx-functions.md) vysvětluje psaní volání funkcí RFX v vaše `DoFieldExchange` přepsat.

V následující tabulce jsou uvedeny vaši roli ve vztahu k rámci udělá za vás.

### <a name="using-rfx-you-and-the-framework"></a>Použití funkce RFX: Vy a architektura

|Vy|Rozhraní framework|
|---------|-------------------|
|Deklarace třídy sady záznamů s průvodce. Zadejte názvy a datové typy pole datových členů.|Průvodce odvozuje `CRecordset` třídy a zapíše [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) přepsat za vás, včetně RFX volání pro každé pole datového člena funkce.|
|(Volitelné) Ručně přidáte všechny potřebné parametry datových členů třídy. Ručně přidejte volání funkce RFX `DoFieldExchange` pro každý parametr datový člen, přidejte volání do [CFieldExchange::SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype) pro skupinu parametrů a zadejte celkový počet parametrů v [m_nParams ](../../mfc/reference/crecordset-class.md#m_nparams). See [Recordset: Parametrizace sady záznamů (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).||
|(Volitelné) Ruční svázání další sloupce na pole datové členy. Zvyšte ručně [m_nFields](../../mfc/reference/crecordset-class.md#m_nfields). See [Recordset: Dynamické vazby datových sloupců (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).||
|Sestavte objekt třídy sady záznamů. Před použitím objektu, nastavte hodnoty parametru datové členy, pokud existuje.|Z důvodu efektivity rozhraní znovu naváže parametry, pomocí ovladače ODBC. Při předávání hodnot parametrů, předává je rozhraní ke zdroji dat. Pouze hodnoty parametrů jsou odesílány pro zopakování dotazu, pokud jste změnili řazení a/nebo filtr řetězce.|
|Vytvořit objekt sady záznamů prostřednictvím [CRecordset::Open](../../mfc/reference/crecordset-class.md#open).|Provede dotaz sadu záznamů, váže sloupce pole data členů sady záznamů a volání `DoFieldExchange` pro výměnu dat mezi první vybraný záznam a sady záznamů pole datových členů.|
|Posouvání záznamů pomocí [CRecordset::Move](../../mfc/reference/crecordset-class.md#move) nebo příkaz nabídky nebo panelu nástrojů.|Volání `DoFieldExchange` k přenosu dat do datové členy polí z nové aktuální záznam.|
|Přidat, aktualizovat a odstraňovat záznamy.|Volání `DoFieldExchange` posílat data do zdroje dat.|

## <a name="see-also"></a>Viz také:

[Výměna polí záznamu (Record Field Exchange – RFX)](../../data/odbc/record-field-exchange-rfx.md)<br/>
[Výměna polí záznamu: Jak funkce RFX pracuje](../../data/odbc/record-field-exchange-how-rfx-works.md)<br/>
[Recordset: Získávání součtů a jiných agregačních výsledků (ODBC)](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md)<br/>
[CRecordset – třída](../../mfc/reference/crecordset-class.md)<br/>
[CFieldExchange – třída](../../mfc/reference/cfieldexchange-class.md)<br/>
[Makra, globální funkce a globální proměnné](../../mfc/reference/mfc-macros-and-globals.md)

