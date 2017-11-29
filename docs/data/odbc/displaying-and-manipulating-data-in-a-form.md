---
title: "Zobrazení a manipulace dat ve formuláři | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- forms [C++], displaying data
- displaying data [C++], forms
- ODBC [C++], forms
- record views [C++], displaying data
- data [MFC]
- data [MFC], displaying in a form
ms.assetid: c56185c4-12cb-40b1-b499-02b29ea83e3a
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: eb286e837d06ca12ebffa22d15ff9c534d815e83
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="displaying-and-manipulating-data-in-a-form"></a>Zobrazení dat ve formuláři a manipulace s nimi
Mnoho aplikací přístup k datům vyberte data a zobrazit ji v pole ve formuláři. Třída databáze [CRecordView](../../mfc/reference/crecordview-class.md) vám dává [CFormView](../../mfc/reference/cformview-class.md) objekt připojení přímo na objekt sady záznamů. Zobrazení záznamu používá [výměna dialogových dat (DDX)](../../mfc/dialog-data-exchange-and-validation.md) přesunutí hodnoty polí na aktuální záznam ze sady záznamů ovládacích prvků na formuláři a přesouvá aktualizované informace zpět do sady záznamů. Sady záznamů se pak používá výměna pole záznamu (RFX) pro přesun dat mezi její pole datových členů a odpovídající sloupce v tabulce na datovém zdroji.  
  
 Můžete použít Průvodce aplikací knihovny MFC nebo **přidat třídu** (jak je popsáno v [přidání příjemce rozhraní ODBC knihovny MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)) k vytvoření třídy zobrazení a jeho přidružené třídy sady záznamů ve spojení.  
  
 Zobrazení záznamu a jeho sady záznamů jsou zničen po zavření dokumentu. Další informace o zobrazení záznamů najdete v tématu [zobrazení záznamů](../../data/record-views-mfc-data-access.md). Další informace o RFX najdete v tématu [výměna pole záznamu (RFX)](../../data/odbc/record-field-exchange-rfx.md).  
  
## <a name="see-also"></a>Viz také  
 [ODBC a MFC](../../data/odbc/odbc-and-mfc.md)