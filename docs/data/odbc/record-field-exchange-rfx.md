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
ms.openlocfilehash: e1ba9f29ebf2cb3b1f94620e815882c850bbc7cc
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213054"
---
# <a name="record-field-exchange-rfx"></a>Výměna pole záznamu (Record Field Exchange – RFX)

Třídy databáze knihovny MFC rozhraní ODBC automatizují přesouvání dat mezi zdrojem dat a objektem [sady záznamů](../../data/odbc/recordset-odbc.md) . Když odvodíte třídu z [CRecordset](../../mfc/reference/crecordset-class.md) a nepoužíváte hromadné načítání řádků, data se přenáší pomocí mechanismu výměny pole záznamu (RFX).

> [!NOTE]
>  Pokud jste implementovali hromadné načítání řádků v odvozené `CRecordset` třídě, používá rozhraní k přenosu dat mechanismus hromadné výměny pole záznamu (Bulk RFX). Další informace naleznete v tématu [Sada záznamů: hromadné načítání záznamů (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

RFX je podobný jako výměna dialogových dat (DDX). Přesun dat mezi zdrojem dat a poli datových členů pole sady záznamů vyžaduje více volání funkce [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) sady záznamů a značnou interakci mezi rozhraním a [rozhraním ODBC](../../data/odbc/odbc-basics.md). Mechanismus RFX je typově bezpečný a šetří práci s voláním funkcí ODBC, jako je `::SQLBindCol`. Další informace o DDX naleznete v tématu [Výměna a ověřování dat dialogových oken](../../mfc/dialog-data-exchange-and-validation.md).

RFX je hlavně transparentní pro vás. Pokud deklarujete třídy sady záznamů pomocí Průvodce aplikací knihovny MFC nebo **přidáte třídu** (jak je popsáno v tématu [Přidání příjemce knihovny MFC rozhraní ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)), je RFX do nich integrován automaticky. Třída sady záznamů musí být odvozena od základní třídy `CRecordset` dodané v rámci rozhraní. Průvodce aplikací knihovny MFC umožňuje vytvořit počáteční třídu sady záznamů. **Přidat třídu** umožňuje přidat další třídy sady záznamů, jak je potřebujete. Další informace a příklady naleznete v tématu [Přidání příjemce knihovny MFC rozhraní ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md).

Je nutné ručně přidat malé množství RFX kódu ve třech případech, pokud chcete:

- Používejte parametrizované dotazy. Další informace naleznete v tématu [Sada záznamů: Parametrizace sady záznamů (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).

- Provede spojení (pomocí jedné sady záznamů pro sloupce ze dvou nebo více tabulek). Další informace naleznete v tématu [Sada záznamů: provádí se spojení (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md).

- Dynamicky navazovat datové sloupce Toto je méně běžné než Parametrizace. Další informace naleznete v tématu [Sada záznamů: dynamické vazby datových sloupců (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).

Pokud potřebujete pokročilejší porozumění RFX, přečtěte si téma [Výměna pole záznamu: Jak funguje RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

V následujících tématech najdete vysvětlení podrobností o použití objektů sady záznamů:

- [Výměna polí záznamu: Použití funkce RFX](../../data/odbc/record-field-exchange-using-rfx.md)

- [Výměna polí záznamu: Použití funkcí RFX](../../data/odbc/record-field-exchange-using-the-rfx-functions.md)

- [Výměna polí záznamu: Jak funkce RFX pracuje](../../data/odbc/record-field-exchange-how-rfx-works.md)

## <a name="see-also"></a>Viz také

[Open Database Connectivity (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)<br/>
[Sada záznamů (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Využití MFC rozhraní ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)<br/>
[Podpora databáze, Průvodce aplikací MFC](../../mfc/reference/database-support-mfc-application-wizard.md)<br/>
[CRecordset – třída](../../mfc/reference/crecordset-class.md)
