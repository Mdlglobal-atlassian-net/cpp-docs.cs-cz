---
title: Změny může provádět výchozího kódu (přístup k datům MFC) | Dokumentace Microsoftu
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
ms.openlocfilehash: b54b585d2f179cfedf69cd3236228c0cb1ebe7c1
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46035146"
---
# <a name="changes-you-might-make-to-the-default-code--mfc-data-access"></a>Změny, které můžete provést výchozího kódu (přístup k datům MFC)

[Průvodce aplikací knihovny MFC](../mfc/reference/database-support-mfc-application-wizard.md) zapíše třídy sady záznamů, který vybere všechny záznamy v jedné tabulky. Často budete chtít upravit toto chování v jedné nebo více z následujících způsobů:  
  
- Nastavte filtr nebo řazení záznamů. K tomu `OnInitialUpdate` po objekt sady záznamů je vytvořen ale ještě před jeho `Open` členská funkce je volána. Další informace najdete v tématu [sada záznamů: filtrování záznamů (ODBC)](../data/odbc/recordset-filtering-records-odbc.md) a [sada záznamů: řazení záznamů (ODBC)](../data/odbc/recordset-sorting-records-odbc.md).  
  
- Parametrizace sady záznamů. Zadejte hodnotu parametru skutečné za běhu za filtru. Další informace najdete v tématu [sada záznamů: Parametrizace sady záznamů (ODBC)](../data/odbc/recordset-parameterizing-a-recordset-odbc.md)  
  
- Dokončete vlastní řetězec SQL na [otevřít](../mfc/reference/crecordset-class.md#open) členskou funkci. Diskuzi o můžete provést s touto technikou, naleznete v tématu [SQL: SQL příkazu přizpůsobení sady záznamů (ODBC)](../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md).  
  
## <a name="see-also"></a>Viz také  

[Použití zobrazení záznamů](../data/using-a-record-view-mfc-data-access.md)