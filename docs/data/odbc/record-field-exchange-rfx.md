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
ms.openlocfilehash: f612f4be726707681ffbddff88ccc6b8a672e427
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50522405"
---
# <a name="record-field-exchange-rfx"></a>Výměna pole záznamu (Record Field Exchange – RFX)

Třídy databází MFC ODBC automatizovat přesouvá data mezi zdroji dat a [záznamů](../../data/odbc/recordset-odbc.md) objektu. Pokud odvodíte třídu od [CRecordset](../../mfc/reference/crecordset-class.md) a nepoužívejte hromadné načítání řádků, data se přenáší mechanismus pole záznamu (RFX) systému exchange.

> [!NOTE]
>  Pokud jste implementovali hromadné načítání řádků v odvozené `CRecordset` třídy, rozhraní používá mechanismus exchange (Bulk RFX) pole záznamu přenášet data. Další informace najdete v tématu [sada záznamů: načítání hromadné záznamů (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

RFX je podobný výměna dat dialogových oken (DDX). Přesun dat mezi zdrojem dat a datové členy polí sady záznamů vyžaduje více volání na sadu záznamů [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) funkce a značnou interakce mezi rozhraní framework a [ODBC](../../data/odbc/odbc-basics.md). RFX mechanismus je typově bezpečné a uloží úkoly, jako volání funkcí rozhraní ODBC `::SQLBindCol`. Další informace o rozhraní DDX najdete v tématu [výměna dat dialogových oken a ověření](../../mfc/dialog-data-exchange-and-validation.md).

RFX je ve většině případů transparentní pro vás. Pokud deklarujete vaší třídy sady záznamů pomocí Průvodce aplikací knihovny MFC nebo **přidat třídu** (jak je popsáno v [přidání příjemce ODBC knihovny MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)), funkce RFX je součástí je automaticky. Sada záznamů třídu musí být odvozen od základní třídy `CRecordset` poskytnutých rozhraní framework. Průvodce aplikací MFC umožňuje vytvořit třídu Počáteční sada záznamů. **Přidejte třídu** můžete přidat další třídy sady záznamů, podle potřeby. Další informace a příklady najdete v tématu [přidání příjemce ODBC knihovny MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md).

Je třeba ručně přidat malé množství kódu RFX ve třech případech, když chcete:

- Použití parametrizovaných dotazů. Další informace najdete v tématu [sada záznamů: Parametrizace sady záznamů (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).

- Provedení spojení (použití jedné sady záznamů pro sloupce ze dvou nebo více tabulek). Další informace najdete v tématu [sada záznamů: provedení do připojení (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md).

- Vytvoření vazby datových sloupců dynamicky. To je méně častý než parametrizace. Další informace najdete v tématu [sada záznamů: dynamické vazby dat sloupců (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).

Pokud potřebujete rozsáhlejšími znalostmi RFX, přečtěte si [výměna polí záznamu: jak funkce RFX pracuje](../../data/odbc/record-field-exchange-how-rfx-works.md).

Následující témata popisují podrobnosti o použití objektů sada záznamů:

- [Výměna polí záznamu: Použití funkce RFX](../../data/odbc/record-field-exchange-using-rfx.md)

- [Výměna polí záznamu: Použití funkcí RFX](../../data/odbc/record-field-exchange-using-the-rfx-functions.md)

- [Výměna polí záznamu: Jak funkce RFX pracuje](../../data/odbc/record-field-exchange-how-rfx-works.md)

## <a name="see-also"></a>Viz také

[Open Database Connectivity (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)<br/>
[Sada záznamů (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Knihovny MFC rozhraní ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)<br/>
[Podpora databáze, Průvodce aplikací MFC](../../mfc/reference/database-support-mfc-application-wizard.md)<br/>
[CRecordset – třída](../../mfc/reference/crecordset-class.md)