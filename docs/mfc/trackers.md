---
title: Snímače | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6f0a0cc52e3a5150702af4acd293def38df758fd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33381534"
---
# <a name="trackers"></a>Snímače
[Crecttracker –](../mfc/reference/crecttracker-class.md) třída poskytuje uživatelské rozhraní mezi obdélníkovou položek v aplikaci a uživatelů tím, že poskytuje celou řadu styly zobrazení. Tyto styly obsahují plný, šrafované nebo přerušovaný ohraničení; šrafované vzor, který obsahuje položky; a změňte velikost obslužných rutin, které může být umístěn na vnější nebo součástí ohraničení. Snímače se často používají ve spojení s OLE – položky, tedy odvozené objekty z `COleClientItem`. Sledovací modul obdélníků poskytnout vizuální upozornění na aktuální stav položky.  
  
 Ukázka MFC OLE [OCLIENT](../visual-cpp-samples.md) ukazuje společné rozhraní pomocí snímačů a klientské položky OLE z hlediska kontejneru aplikace. Ukázka různými styly a dalo objektu sledovací modul najdete v tématu obecné ukázka MFC [sledovací modul](../visual-cpp-samples.md).  
  
 Další informace o implementace snímačů ve vašich aplikacích OLE najdete v tématu [snímače: implementace snímačů ve vašem OLE aplikaci](../mfc/trackers-implementing-trackers-in-your-ole-application.md)  
  
## <a name="see-also"></a>Viz také  
 [OLE](../mfc/ole-in-mfc.md)   
 [COleClientItem – třída](../mfc/reference/coleclientitem-class.md)
