---
title: Výběr záznamů a manipulace s nimi
ms.date: 11/04/2016
helpviewer_keywords:
- records, selecting
- record selection, MFC ODBC classes
- ODBC recordsets, selecting records
ms.assetid: 7f0b3a4a-9941-4475-a612-9ec8d15b7691
ms.openlocfilehash: d038a0f9d2e7ba1f0e6bcf925eadc2173339b9b8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50550797"
---
# <a name="selecting-and-manipulating-records"></a>Výběr záznamů a manipulace s nimi

Obvykle Pokud vyberete záznamy ze zdroje dat pomocí SQL **vyberte** příkazu získat sadu výsledků dotazu, což je sada záznamů z tabulky nebo dotaz. S databázovými třídami použít objekt sady záznamů a vyberte přístup k sadě výsledků. Toto je objekt třídy specifické pro aplikaci, která je odvozena od třídy [CRecordset](../../mfc/reference/crecordset-class.md). Při definování třídy sady záznamů, můžete zadat zdroje dat a přidružte jej k, tabulku použít a sloupce v tabulce. Průvodce aplikací knihovny MFC nebo **přidat třídu** (jak je popsáno v [přidání příjemce ODBC knihovny MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)) s připojením ke konkrétnímu zdroji dat vytvoří třídu. Průvodci zápis [GetDefaultSQL](../../mfc/reference/crecordset-class.md#getdefaultsql) členské funkce třídy `CRecordset` vrátit název tabulky. Další informace o používání průvodce k vytvoření sady záznamů tříd naleznete v tématu [Podpora databáze, Průvodce aplikací knihovny MFC](../../mfc/reference/database-support-mfc-application-wizard.md) a [přidání příjemce ODBC knihovny MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md).

Použití [CRecordset](../../mfc/reference/crecordset-class.md) objektu za běhu, můžete:

- Prozkoumejte datová pole z aktuální záznam.

- Filtr nebo řazení záznamů.

- Přizpůsobení výchozí SQL **vyberte** příkazu.

- Projděte si vybrané záznamy.

- Přidání, aktualizace nebo odstranění záznamů (Pokud je zdroj dat a sady záznamů jsou aktualizovatelné).

- Otestujte, zda sada záznamů umožňuje opětovné spuštění dotazu a aktualizovat obsah sady záznamů.

Po dokončení používání objektu sady záznamů, zavřete a zničte jej. Další informace o sadách záznamů najdete v tématu [sada záznamů (ODBC)](../../data/odbc/recordset-odbc.md).

## <a name="see-also"></a>Viz také

[Rozhraní ODBC a knihovna MFC](../../data/odbc/odbc-and-mfc.md)