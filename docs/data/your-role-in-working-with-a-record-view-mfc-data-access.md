---
title: "Vaše Role při práci se zobrazením záznamu (MFC Data Access) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- record views, customizing default code
- MFC, record views
ms.assetid: 691e89a5-ff21-4ca3-9278-69d4678288bb
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 03d64715f3bdfb6028fdb039451d4b4b004a059e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="your-role-in-working-with-a-record-view--mfc-data-access"></a>Vaše Role při práci se zobrazením záznamu (Data MFC Access)
Následující tabulka uvádí, co je obvykle nutné udělat pro práci se zobrazením záznamu a co rozhraní framework za vás.  
  
### <a name="working-with-a-record-view-you-and-the-framework"></a>Práce se zobrazením záznamu: vy a architektura  
  
|Vy|Rozhraní framework|  
|---------|-------------------|  
|Návrh formuláře pomocí Visual C++ dialogové okno editoru.|Vytvoří prostředek šablony dialogové okno s ovládacími prvky.|  
|Použití [Průvodce aplikací knihovny MFC](../mfc/reference/database-support-mfc-application-wizard.md) pro vytvoření třídy odvozené od třídy [CRecordView](../mfc/reference/crecordview-class.md) a [CRecordset](../mfc/reference/crecordset-class.md).|Zapíše třídy pro vás.|  
|Ovládací prvky zobrazení záznamu mapovat do sady záznamů pole datových členů.|Poskytuje DDX mezi ovládacími prvky a pole sady záznamů.|  
||Poskytuje výchozí obslužné rutiny příkazů pro **přesunout na první**, **přesunout na poslední**, **přesunout na další**, a **přesunout na předchozí** příkazy z nabídek nebo panelu nástrojů tlačítka.|  
||Zdroj dat změny aktualizace.|  
|[Nepovinné] Napište kód k vyplnění pole se seznamem nebo seznamu polí nebo jiných ovládacích prvků s daty z druhé sady záznamů.||  
|[Nepovinné] Psaní kódu pro všechny speciální ověření.||  
|[Nepovinné] Napište kód pro přidání nebo odstranění záznamů.||  
  
 Programování založené na formulářích je pouze jeden z přístupů k práci s databází. Informace o aplikacích pomocí některé jiné uživatelské rozhraní ani žádné uživatelské rozhraní najdete v tématu [MFC: použití databázových tříd s dokumenty a zobrazeními](../data/mfc-using-database-classes-with-documents-and-views.md) a [MFC: použití třídy databáze bez dokumentů a zobrazení](../data/mfc-using-database-classes-without-documents-and-views.md). Alternativní přístupy k zobrazení záznamů databáze najdete v tématu třídy [CListView](../mfc/reference/clistview-class.md) a [CTreeView](../mfc/reference/ctreeview-class.md).  
  
## <a name="see-also"></a>Viz také  
 [Zobrazení záznamů (Data MFC Access)](../data/record-views-mfc-data-access.md)   
 [Seznam ovladačů ODBC](../data/odbc/odbc-driver-list.md)