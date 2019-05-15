---
title: Výběr záznamů a manipulace s nimi
ms.date: 05/09/2019
helpviewer_keywords:
- records, selecting
- record selection, MFC ODBC classes
- ODBC recordsets, selecting records
ms.assetid: 7f0b3a4a-9941-4475-a612-9ec8d15b7691
ms.openlocfilehash: 745c0c35e42426242d92d720d5dcd3de631fb17b
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65707810"
---
# <a name="selecting-and-manipulating-records"></a>Výběr záznamů a manipulace s nimi

> [!NOTE] 
> Průvodce příjemcem ODBC knihovny MFC není k dispozici v aplikaci Visual Studio 2019 a novějším. Příjemce měli stále můžete vytvořit ručně.

Obvykle Pokud vyberete záznamy ze zdroje dat pomocí SQL **vyberte** příkazu získat sadu výsledků dotazu, což je sada záznamů z tabulky nebo dotaz. S databázovými třídami použít objekt sady záznamů a vyberte přístup k sadě výsledků. Toto je objekt třídy specifické pro aplikaci, která je odvozena od třídy [CRecordset](../../mfc/reference/crecordset-class.md). Při definování třídy sady záznamů, můžete zadat zdroje dat a přidružte jej k, tabulku použít a sloupce v tabulce. Průvodce aplikací knihovny MFC nebo **přidat třídu** (jak je popsáno v [přidání příjemce ODBC knihovny MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)) s připojením ke konkrétnímu zdroji dat vytvoří třídu. Průvodci zápis [GetDefaultSQL](../../mfc/reference/crecordset-class.md#getdefaultsql) členské funkce třídy `CRecordset` vrátit název tabulky.

Použití [CRecordset](../../mfc/reference/crecordset-class.md) objektu za běhu, můžete:

- Prozkoumejte datová pole z aktuální záznam.

- Filtr nebo řazení záznamů.

- Přizpůsobení výchozí SQL **vyberte** příkazu.

- Projděte si vybrané záznamy.

- Přidání, aktualizace nebo odstranění záznamů (Pokud je zdroj dat a sady záznamů jsou aktualizovatelné).

- Otestujte, zda sada záznamů umožňuje opětovné spuštění dotazu a aktualizovat obsah sady záznamů.

Po dokončení používání objektu sady záznamů, zavřete a zničte jej. Další informace o sadách záznamů najdete v tématu [sada záznamů (ODBC)](../../data/odbc/recordset-odbc.md).

## <a name="see-also"></a>Viz také:

[Rozhraní ODBC a knihovna MFC](../../data/odbc/odbc-and-mfc.md)