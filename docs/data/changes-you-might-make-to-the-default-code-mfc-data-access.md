---
title: Změny můžete provést ve výchozím kódu (MFC Data Access) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- record views [C++], customizing default code
ms.assetid: 9992ed37-a6bf-45a5-a572-5c14e42b6628
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: e647f6350819fa2cccb5f8319f95fbac16ca19fc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33088362"
---
# <a name="changes-you-might-make-to-the-default-code--mfc-data-access"></a>Změny, které můžete provést ve výchozím kódu (Data MFC Access)
[Průvodce aplikací knihovny MFC](../mfc/reference/database-support-mfc-application-wizard.md) zapíše třídy sady záznamů pro vás, která vybere všechny záznamy v jediné tabulce. Často můžete upravit toto chování v jedné nebo více z následujících způsobů:  
  
-   Nastavte filtr nebo pořadí řazení sady záznamů. K tomu `OnInitialUpdate` po objekt sady záznamů je vytvořený ale před jeho **otevřete** členské funkce je volána. Další informace najdete v tématu [sada záznamů: filtrování záznamů (ODBC)](../data/odbc/recordset-filtering-records-odbc.md) a [sada záznamů: řazení záznamů (ODBC)](../data/odbc/recordset-sorting-records-odbc.md).  
  
-   Parametrizace sady záznamů. Zadejte hodnotu skutečný parametr spuštění po filtru. Další informace najdete v tématu [sada záznamů: Parametrizace sady záznamů (ODBC)](../data/odbc/recordset-parameterizing-a-recordset-odbc.md)  
  
-   Dokončete vlastní řetězec SQL k [otevřete](../mfc/reference/crecordset-class.md#open) – členská funkce. Informace o můžete provést s touto technikou, najdete v části [SQL: přizpůsobení vaše SQL příkazu záznamů (ODBC)](../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md).  
  
## <a name="see-also"></a>Viz také  
 [Použití zobrazení záznamů](../data/using-a-record-view-mfc-data-access.md)