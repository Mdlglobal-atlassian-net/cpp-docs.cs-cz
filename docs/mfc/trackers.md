---
title: "Snímače | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- trackers [MFC]
- OLE applications [MFC], trackers
- applications [OLE], trackers
- tracking OLE items [MFC]
- OLE containers [MFC], trackers
- CDC class [MFC], trackers
- CRectTracker class [MFC], implementing trackers
- OLE server applications [MFC], trackers
ms.assetid: dcd09399-6637-4621-80e5-d12670429787
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 29e4d3c556a5f7b6b3aed5daa0285ea6c2c15447
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="trackers"></a>Snímače
[Crecttracker –](../mfc/reference/crecttracker-class.md) třída poskytuje uživatelské rozhraní mezi obdélníkovou položek v aplikaci a uživatelů tím, že poskytuje celou řadu styly zobrazení. Tyto styly obsahují plný, šrafované nebo přerušovaný ohraničení; šrafované vzor, který obsahuje položky; a změňte velikost obslužných rutin, které může být umístěn na vnější nebo součástí ohraničení. Snímače se často používají ve spojení s OLE – položky, tedy odvozené objekty z `COleClientItem`. Sledovací modul obdélníků poskytnout vizuální upozornění na aktuální stav položky.  
  
 Ukázka MFC OLE [OCLIENT](../visual-cpp-samples.md) ukazuje společné rozhraní pomocí snímačů a klientské položky OLE z hlediska kontejneru aplikace. Ukázka různými styly a dalo objektu sledovací modul najdete v tématu obecné ukázka MFC [sledovací modul](../visual-cpp-samples.md).  
  
 Další informace o implementace snímačů ve vašich aplikacích OLE najdete v tématu [snímače: implementace snímačů ve vašem OLE aplikaci](../mfc/trackers-implementing-trackers-in-your-ole-application.md)  
  
## <a name="see-also"></a>Viz také  
 [OLE](../mfc/ole-in-mfc.md)   
 [COleClientItem – třída](../mfc/reference/coleclientitem-class.md)
