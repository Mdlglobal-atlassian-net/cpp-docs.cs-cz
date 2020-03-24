---
title: Změny, které můžete provést ve výchozím kódu (přístup k datům MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- record views [C++], customizing default code
ms.assetid: 9992ed37-a6bf-45a5-a572-5c14e42b6628
ms.openlocfilehash: 7ea616caf176cd1e9e2f26bee1339640067b4e3e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213458"
---
# <a name="changes-you-might-make-to-the-default-code--mfc-data-access"></a>Změny, které můžete provést ve výchozím kódu (přístup k datům MFC)

[Průvodce aplikací knihovny MFC](../mfc/reference/database-support-mfc-application-wizard.md) zapíše třídu sady záznamů, která vybere všechny záznamy v jedné tabulce. Často budete chtít toto chování upravit v jednom nebo několika následujících způsobech:

- Nastavte filtr nebo pořadí řazení pro sadu záznamů. Tuto operaci proveďte v `OnInitialUpdate` po vytvoření objektu Recordset, ale před voláním členské funkce `Open`. Další informace naleznete v tématu [Sada záznamů: filtrování záznamů (ODBC)](../data/odbc/recordset-filtering-records-odbc.md) a [Sada záznamů: řazení záznamů (ODBC)](../data/odbc/recordset-sorting-records-odbc.md).

- Parametrizovat sadu záznamů. Zadejte za filtr skutečnou hodnotu parametru run-time. Další informace naleznete v tématu [Sada záznamů: Parametrizace sady záznamů (ODBC).](../data/odbc/recordset-parameterizing-a-recordset-odbc.md)

- Předání přizpůsobeného řetězce SQL do [otevřené](../mfc/reference/crecordset-class.md#open) členské funkce. Diskuzi o tom, co můžete s tímto postupem dosáhnout, najdete v tématu [SQL: Přizpůsobení příkazu SQL sady záznamů (ODBC)](../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md).

## <a name="see-also"></a>Viz také

[Používání zobrazení záznamu](../data/using-a-record-view-mfc-data-access.md)
