---
title: Výměna pole záznamu (Record Field Exchange – RFX)
ms.date: 11/04/2016
helpviewer_keywords:
- RFX (ODBC) [C++]
- data [MFC], moving between sources and recordsets
- database classes [C++], RFX
- data [MFC]
- ODBC [C++], RFX
ms.assetid: f5ddfbf0-2901-48d7-9848-4fb84de3c7ee
ms.openlocfilehash: 6f965b90e1e0bbcfd3ad04bb5b40644d61050b2e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367151"
---
# <a name="record-field-exchange-rfx"></a>Výměna pole záznamu (Record Field Exchange – RFX)

Třídy databáze Rozhraní MFC ODBC automatizují přesun dat mezi zdrojem dat a objektem [sady záznamů.](../../data/odbc/recordset-odbc.md) Když odvodíte třídu z [CRecordset](../../mfc/reference/crecordset-class.md) a nepoužíváte hromadné načítání řádků, data jsou přenášena mechanismem výměny pole záznamu (RFX).

> [!NOTE]
> Pokud jste implementovali hromadné načítání řádků `CRecordset` v odvozené třídě, rozhraní framework používá mechanismus hromadného záznamu pole exchange (Bulk RFX) k přenosu dat. Další informace naleznete [v tématu Recordset: Fetching Records in Bulk (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

RFX je podobný dialogu výměny dat (DDX). Přesunutí dat mezi zdrojem dat a datovými členy pole sady záznamů vyžaduje více volání funkce [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) sady záznamů a značnou interakci mezi rozhraním [ODBC](../../data/odbc/odbc-basics.md). Mechanismus RFX je typově bezpečný a šetří práci volání `::SQLBindCol`funkcí ROZHRANÍ ODBC, jako je například . Další informace o ddx naleznete [v tématu Dialog Data Exchange and Validation](../../mfc/dialog-data-exchange-and-validation.md).

RFX je pro vás většinou transparentní. Pokud deklarujete třídy sady záznamů pomocí Průvodce aplikací knihovny MFC nebo **Přidat třídu** (jak je popsáno v [tématu Přidání příjemce rozhraní MFC ODBC),](../../mfc/reference/adding-an-mfc-odbc-consumer.md)rfx je integrován do nich automaticky. Vaše třída sady záznamů musí být `CRecordset` odvozena ze základní třídy poskytované rámcem. Průvodce aplikací knihovny MFC umožňuje vytvořit počáteční třídu sady záznamů. **Add Class** umožňuje přidávat další třídy sady záznamů podle potřeby. Další informace a příklady naleznete [v tématu Přidání příjemce knihovny MFC ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md).

Je nutné ručně přidat malé množství kódu RFX ve třech případech, pokud chcete:

- Použijte parametrizované dotazy. Další informace naleznete v [tématu Recordset: Parameterizing a Recordset (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).

- Proveďte spojení (pomocí jedné sady záznamů pro sloupce ze dvou nebo více tabulek). Další informace naleznete v [tématu Recordset: Provedení spojení (ODBC).](../../data/odbc/recordset-performing-a-join-odbc.md)

- Dynamicky spojte datové sloupce. To je méně časté než parametrizace. Další informace naleznete v [tématu Recordset: Dynamicky vazebné datové sloupce (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).

Pokud potřebujete pokročilejší znalostrního efektu RFX, přečtěte si část [Výměna pole záznamu: Jak RFX funguje](../../data/odbc/record-field-exchange-how-rfx-works.md).

Následující témata vysvětlují podrobnosti použití objektů sady záznamů:

- [Výměna polí záznamu: Použití funkce RFX](../../data/odbc/record-field-exchange-using-rfx.md)

- [Výměna polí záznamu: Použití funkcí RFX](../../data/odbc/record-field-exchange-using-the-rfx-functions.md)

- [Výměna polí záznamu: Jak funkce RFX pracuje](../../data/odbc/record-field-exchange-how-rfx-works.md)

## <a name="see-also"></a>Viz také

[Připojení k otevřené databázi (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)<br/>
[Sada záznamů (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Spotřebovávat rozhraní ODBC knihovny MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)<br/>
[Podpora databáze, Průvodce aplikací knihovny MFC](../../mfc/reference/database-support-mfc-application-wizard.md)<br/>
[CRecordset – třída](../../mfc/reference/crecordset-class.md)
