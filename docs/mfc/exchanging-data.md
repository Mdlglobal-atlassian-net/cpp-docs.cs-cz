---
title: "Výměna dat | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- property sheets [MFC], data exchange
- exchanging data with property sheets [MFC]
- DDX (dialog data exchange) [MFC], property sheets
ms.assetid: 689f02d0-51a9-455b-8ffb-5b44f0aefa28
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: da94d04a2cddb416ca62a71dbfa232317d55e612
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="exchanging-data"></a>Výměna dat
Stejně jako u většiny dialogových oken, výměnu dat mezi vlastností a aplikace je jedním z nejdůležitějších funkce seznamu vlastností. Tento článek popisuje, jak k provedení této úlohy.  
  
 Výměna dat s vlastností je ve skutečnosti řádu výměna dat s stránkách vlastností jednotlivých seznamu vlastností. Výměna dat s stránky vlastností postup je stejný jako u výměna dat se dialogové okno, protože [CPropertyPage](../mfc/reference/cpropertypage-class.md) objekt je právě specializované [CDialog](../mfc/reference/cdialog-class.md) objektu. Postup využívá rozhraní framework dialogové okno dat systému exchange (DDX) prostředků, což výměny dat mezi ovládacími prvky v dialogovém okně pole a člen proměnné objektu dialogové okno pole.  
  
 Důležitý rozdíl mezi výměna dat s vlastností a dialogové okno normální je, že seznam vlastností má více stránek, proto musí vyměňovat data s všechny stránky v seznamu vlastností. Další informace o DDX najdete v tématu [výměna dialogových dat a ověření](../mfc/dialog-data-exchange-and-validation.md).  
  
 Následující příklad ilustruje výměnou dat mezi zobrazením a dvě stránky vlastností:  
  
 [!code-cpp[NVC_MFCDocView#4](../mfc/codesnippet/cpp/exchanging-data_1.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [Seznam vlastností](../mfc/property-sheets-mfc.md)

