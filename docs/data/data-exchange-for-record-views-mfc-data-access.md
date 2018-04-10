---
title: Výměna dat pro zobrazení záznamu (MFC Data Access) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- RFX (record field exchange), data exchange mechanism
- RFX (record field exchange), record views
- record views, data exchange
- DDX (dialog data exchange), record views
- RFX (record field exchange)
ms.assetid: abc52ca7-6997-47a7-98f3-f347f52b1f72
caps.latest.revision: 9
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 1db5adaab66fec2b587f7a15005caa3a9374ff12
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="data-exchange-for-record-views---mfc-data-access"></a>Výměna dat pro zobrazení záznamů (Data MFC Access)
Při použití [přidat třídu](../mfc/reference/adding-an-mfc-odbc-consumer.md) mapovat ovládacích prvků v zobrazení záznamu prostředku šablony dialogového okna polí sady záznamů, rozhraní spravuje výměny dat v obou směrech – od sady záznamů s ovládacími prvky a z ovládacích prvků do sady záznamů. Pomocí mechanizmu DDX znamená, že není nutné napsat kód pro přenos dat a zpět, sami.  
  
 DDX pro zobrazení záznamů funguje ve spojení s [RFX](../data/odbc/record-field-exchange-rfx.md) pro sady záznamů třídy `CRecordset` (ODBC).  RFX přesouvá data mezi na aktuální záznam zdroje dat a pole datových členů objektu sady záznamů. DDX přesune data z pole datových členů do ovládacích prvků ve formuláři. Tato kombinace doplní ovládacích prvků formuláře počátečním a jak se uživatel přesune mezi záznamy. Je také můžete přesunout aktualizovaná data zpět do sady záznamů a poté ke zdroji dat.  
  
 Následující obrázek znázorňuje vztah mezi DDX a RFX pro zobrazení záznamů.  
  
 ![Dialogové okno & č. 45; výměny dat a záznam & č. 45; pole exchange](../data/media/vc37xt1.gif "vc37xt1")  
Výměna dat dialogových oken a výměna pole záznamu  
  
 Další informace o rozhraní DDX najdete v tématu [výměna dialogových dat a ověření](../mfc/dialog-data-exchange-and-validation.md). Další informace o RFX najdete v tématu [výměna pole záznamu (RFX)](../data/odbc/record-field-exchange-rfx.md).  
  
## <a name="see-also"></a>Viz také  
 [Zobrazení záznamů (Data MFC Access)](../data/record-views-mfc-data-access.md)   
 [Seznam ovladačů ODBC](../data/odbc/odbc-driver-list.md)