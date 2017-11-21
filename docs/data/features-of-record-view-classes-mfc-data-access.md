---
title: "Funkce záznamu zobrazit třídy (MFC Data Access) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- record views, classes
- record view classes
ms.assetid: e7b2820f-09c4-483f-83c0-317e8be42bdf
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d1a30742a538d941220cf099c33445089c9a907c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="features-of-record-view-classes--mfc-data-access"></a>Funkce tříd zobrazení záznamu (Data MFC Access)
Můžete provést pomocí formuláře přístup k datům programování pomocí třídy [CFormView](../mfc/reference/cformview-class.md), ale [CRecordView](../mfc/reference/crecordview-class.md) je obecně lepší třída k odvozování z. Kromě jeho `CFormView` funkce `CRecordView`:  
  
-   Poskytuje výměna dialogových dat (DDX) mezi ovládacích prvků formuláře a objekt přidružené sady záznamů.  
  
-   Zpracovává přesunout na první, přesunout na další, přesunout na předchozí a přesunout na poslední příkazy pro procházení záznamy v objektu přidružené sady záznamů.  
  
-   Když se uživatel přesune na jiný záznam se změní aktualizace na aktuální záznam.  
  
 Další informace o navigační najdete v tématu [zobrazení záznamů: Podpora navigace v zobrazení záznamu](../data/supporting-navigation-in-a-record-view-mfc-data-access.md).  
  
## <a name="see-also"></a>Viz také  
 [Zobrazení záznamů (Data MFC Access)](../data/record-views-mfc-data-access.md)   
 [Seznam ovladačů ODBC](../data/odbc/odbc-driver-list.md)