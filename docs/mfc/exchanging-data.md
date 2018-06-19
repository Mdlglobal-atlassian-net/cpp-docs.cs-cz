---
title: Výměna dat | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- property sheets [MFC], data exchange
- exchanging data with property sheets [MFC]
- DDX (dialog data exchange) [MFC], property sheets
ms.assetid: 689f02d0-51a9-455b-8ffb-5b44f0aefa28
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e503bd9268423fbe63ec76de4bcb5443a7d52696
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33345817"
---
# <a name="exchanging-data"></a>Výměna dat
Stejně jako u většiny dialogových oken, výměnu dat mezi vlastností a aplikace je jedním z nejdůležitějších funkce seznamu vlastností. Tento článek popisuje, jak k provedení této úlohy.  
  
 Výměna dat s vlastností je ve skutečnosti řádu výměna dat s stránkách vlastností jednotlivých seznamu vlastností. Výměna dat s stránky vlastností postup je stejný jako u výměna dat se dialogové okno, protože [CPropertyPage](../mfc/reference/cpropertypage-class.md) objekt je právě specializované [CDialog](../mfc/reference/cdialog-class.md) objektu. Postup využívá rozhraní framework dialogové okno dat systému exchange (DDX) prostředků, což výměny dat mezi ovládacími prvky v dialogovém okně pole a člen proměnné objektu dialogové okno pole.  
  
 Důležitý rozdíl mezi výměna dat s vlastností a dialogové okno normální je, že seznam vlastností má více stránek, proto musí vyměňovat data s všechny stránky v seznamu vlastností. Další informace o DDX najdete v tématu [výměna dialogových dat a ověření](../mfc/dialog-data-exchange-and-validation.md).  
  
 Následující příklad ilustruje výměnou dat mezi zobrazením a dvě stránky vlastností:  
  
 [!code-cpp[NVC_MFCDocView#4](../mfc/codesnippet/cpp/exchanging-data_1.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [Seznam vlastností](../mfc/property-sheets-mfc.md)

