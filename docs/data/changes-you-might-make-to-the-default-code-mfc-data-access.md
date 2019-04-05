---
title: Změny, které můžete provést výchozího kódu (přístup k datům MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- record views [C++], customizing default code
ms.assetid: 9992ed37-a6bf-45a5-a572-5c14e42b6628
ms.openlocfilehash: fc448ae1e13025a83b33386c2845bdf7bb4d5eec
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "59038632"
---
# <a name="changes-you-might-make-to-the-default-code--mfc-data-access"></a>Změny, které můžete provést výchozího kódu (přístup k datům MFC)

[Průvodce aplikací knihovny MFC](../mfc/reference/database-support-mfc-application-wizard.md) zapíše třídy sady záznamů, který vybere všechny záznamy v jedné tabulky. Často budete chtít upravit toto chování v jedné nebo více z následujících způsobů:

- Nastavte filtr nebo řazení záznamů. K tomu `OnInitialUpdate` po objekt sady záznamů je vytvořen ale ještě před jeho `Open` členská funkce je volána. Další informace najdete v tématu [sada záznamů: Filtrování záznamů (ODBC)](../data/odbc/recordset-filtering-records-odbc.md) a [sada záznamů: Řazení záznamů (ODBC)](../data/odbc/recordset-sorting-records-odbc.md).

- Parametrizace sady záznamů. Zadejte hodnotu parametru skutečné za běhu za filtru. Další informace najdete v tématu [sada záznamů: Parametrizace sady záznamů (ODBC)](../data/odbc/recordset-parameterizing-a-recordset-odbc.md)

- Dokončete vlastní řetězec SQL na [otevřít](../mfc/reference/crecordset-class.md#open) členskou funkci. Diskuzi o můžete provést s touto technikou, naleznete v tématu [SQL: Přizpůsobení příkazu SQL sady záznamů (ODBC)](../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md).

## <a name="see-also"></a>Viz také:

[Použití zobrazení záznamů](../data/using-a-record-view-mfc-data-access.md)