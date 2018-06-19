---
title: Zobrazení a manipulace dat ve formuláři | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- forms [C++], displaying data
- displaying data [C++], forms
- ODBC [C++], forms
- record views [C++], displaying data
- data [MFC]
- data [MFC], displaying in a form
ms.assetid: c56185c4-12cb-40b1-b499-02b29ea83e3a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 3b86c58c8e5afb53cb02174beb3553378dd0efc8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33089363"
---
# <a name="displaying-and-manipulating-data-in-a-form"></a>Zobrazení dat ve formuláři a manipulace s nimi
Mnoho aplikací přístup k datům vyberte data a zobrazit ji v pole ve formuláři. Třída databáze [CRecordView](../../mfc/reference/crecordview-class.md) vám dává [CFormView](../../mfc/reference/cformview-class.md) objekt připojení přímo na objekt sady záznamů. Zobrazení záznamu používá [výměna dialogových dat (DDX)](../../mfc/dialog-data-exchange-and-validation.md) přesunutí hodnoty polí na aktuální záznam ze sady záznamů ovládacích prvků na formuláři a přesouvá aktualizované informace zpět do sady záznamů. Sady záznamů se pak používá výměna pole záznamu (RFX) pro přesun dat mezi její pole datových členů a odpovídající sloupce v tabulce na datovém zdroji.  
  
 Můžete použít Průvodce aplikací knihovny MFC nebo **přidat třídu** (jak je popsáno v [přidání příjemce rozhraní ODBC knihovny MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)) k vytvoření třídy zobrazení a jeho přidružené třídy sady záznamů ve spojení.  
  
 Zobrazení záznamu a jeho sady záznamů jsou zničen po zavření dokumentu. Další informace o zobrazení záznamů najdete v tématu [zobrazení záznamů](../../data/record-views-mfc-data-access.md). Další informace o RFX najdete v tématu [výměna pole záznamu (RFX)](../../data/odbc/record-field-exchange-rfx.md).  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní ODBC a knihovna MFC](../../data/odbc/odbc-and-mfc.md)