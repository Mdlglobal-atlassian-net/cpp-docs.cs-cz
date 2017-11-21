---
title: "Zaznamenejte zobrazení (MFC Data Access) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- MFC [C++], record views
- ODBC recordsets [C++], record views
- databases [C++], record views
- record views [C++]
- forms [C++], data access tasks
ms.assetid: 562122d9-01d8-4284-acf6-ea109ab0408d
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 38c5d65e89aa4fb76ff96fa82cd52e42475e2353
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="record-views--mfc-data-access"></a>Zobrazení záznamů (Data MFC Access)
Tato část platí jenom pro třídy MFC rozhraní ODBC. Informace o zobrazení záznamů technologie OLE DB najdete v tématu [COleDBRecordView](../mfc/reference/coledbrecordview-class.md) a [pomocí OLE DB zobrazení záznamů](../data/oledb/using-ole-db-record-views.md).  
  
 Podpora aplikací založené na formulářích přístup k datům, knihovny tříd poskytuje třídu [CRecordView](../mfc/reference/crecordview-class.md). Zobrazení záznamů je objekt zobrazení formuláře, jehož ovládací prvky jsou mapovány přímo na pole datových členů [sada záznamů](../data/odbc/recordset-odbc.md) objektu (a nepřímo na odpovídající sloupce ve výsledku dotazu nebo tabulky ve zdroji dat). Jako její základní třída [CFormView](../mfc/reference/cformview-class.md), `CRecordView` je založena na prostředku šablony dialogové okno.  
  
## <a name="form-uses"></a>Formulář používá  
 Formuláře jsou užitečné pro řadu úloh, přístup k datům:  
  
-   Zadávání dat  
  
-   Provádění jen pro čtení ověření dat  
  
-   Aktualizace dat  
  
## <a name="further-reading-about-record-views"></a>Další informace o zobrazení záznamů  
 Materiály v tématech se vztahuje na základě rozhraní ODBC a třídy založené na rozhraní DAO. Použití `CRecordView` pro rozhraní ODBC a `CDaoRecordView` pro rozhraní DAO.  
  
 Témata zahrnují:  
  
-   [Funkce tříd zobrazení záznamu](../data/features-of-record-view-classes-mfc-data-access.md)  
  
-   [Výměna dat pro zobrazení záznamů](../data/data-exchange-for-record-views-mfc-data-access.md)  
  
-   [Vaše Role při práci se zobrazením záznamu](../data/your-role-in-working-with-a-record-view-mfc-data-access.md)  
  
-   [Navrhování a vytváření zobrazení záznamů](../data/designing-and-creating-a-record-view-mfc-data-access.md)  
  
-   [Použití zobrazení záznamů](../data/using-a-record-view-mfc-data-access.md)  
  
## <a name="see-also"></a>Viz také  
 [Přístup k datům programování (MFC/ATL)](../data/data-access-programming-mfc-atl.md)   
 [Seznam ovladačů ODBC](../data/odbc/odbc-driver-list.md)