---
title: Výběr záznamů a manipulace s nimi
ms.date: 05/09/2019
helpviewer_keywords:
- records, selecting
- record selection, MFC ODBC classes
- ODBC recordsets, selecting records
ms.assetid: 7f0b3a4a-9941-4475-a612-9ec8d15b7691
ms.openlocfilehash: 8388cd5c8c53a4595dc9b44430077421ee8680bf
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80079801"
---
# <a name="selecting-and-manipulating-records"></a>Výběr záznamů a manipulace s nimi

> [!NOTE]
> Průvodce příjemcem knihovny MFC rozhraní ODBC není dostupný v aplikaci Visual Studio 2019 a novějším. Příjemce můžete přesto vytvořit ručně.

Když vyberete záznamy ze zdroje dat pomocí příkazu SQL **Select** , dostanete sadu výsledků, což je sada záznamů z tabulky nebo dotazu. S databázovými třídami použijete objekt sady záznamů pro výběr a přístup k sadě výsledků. Toto je objekt třídy specifické pro aplikaci, kterou můžete odvodit z třídy [CRecordset](../../mfc/reference/crecordset-class.md). Při definování třídy sady záznamů zadáte zdroj dat, ke kterému se má přidružit, tabulka, která se má použít, a sloupce tabulky. Průvodce aplikací knihovny MFC nebo **Přidat třídu** (jak je popsáno v tématu [Přidání příjemce knihovny MFC rozhraní ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)) vytvoří třídu s připojením ke konkrétnímu zdroji dat. Průvodci zapisují členskou funkci [GetDefaultSQL](../../mfc/reference/crecordset-class.md#getdefaultsql) třídy `CRecordset`, která vrátí název tabulky.

Pomocí objektu [CRecordset](../../mfc/reference/crecordset-class.md) v době běhu můžete:

- Projděte si datová pole aktuálního záznamu.

- Filtrovat nebo seřadit sadu záznamů.

- Přizpůsobení výchozího příkazu SQL **Select** .

- Procházejte vybranými záznamy.

- Přidejte, aktualizujte nebo odstraňte záznamy (Pokud je zdroj dat i sada záznamů aktualizovatelný).

- Otestujte, zda sada záznamů umožňuje dotazování a aktualizaci obsahu sady záznamů.

Po dokončení práce s objektem sady záznamů jej zavřete a zničit. Další informace o sadách záznamů naleznete v tématu [Sada záznamů (ODBC)](../../data/odbc/recordset-odbc.md).

## <a name="see-also"></a>Viz také

[Rozhraní ODBC a knihovna MFC](../../data/odbc/odbc-and-mfc.md)