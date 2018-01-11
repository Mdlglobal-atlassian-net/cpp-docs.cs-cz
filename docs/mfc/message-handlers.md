---
title: "Obslužné rutiny zpráv | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- message handlers [MFC]
- command handling [MFC], message handlers
- handlers [MFC]
- message handling [MFC], message handler functions
- handlers [MFC], command
- handlers [MFC], message
ms.assetid: 51bc4e76-dbe3-4cc2-b026-3199d56b2fa9
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d1b906a49d7da7ed8505252a1759d7ea00fcda1f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="message-handlers"></a>Obslužné rutiny zpráv
V prostředí MFC vyhrazená *obslužná rutina* funkce zpracuje každou samostatnou zprávu. Funkce obslužné rutiny zpráv jsou funkce člena třídy. Tato dokumentace používá podmínky *obslužné rutiny zpráv – členská funkce*, *funkce obslužné rutiny zpráv*, *obslužné rutiny zpráv*, a *obslužná rutina*zcela zaměnitelným významem. Některé druhy obslužné rutiny zpráv se také označují jako "obslužné rutiny příkazů."  
  
 Zápis účty obslužné rutiny zpráv pro velkou část vaší práce v zápisu framework aplikace. Rodina Tento článek popisuje, jak funguje mechanismus zpracování zprávy.  
  
 Jaké jsou obslužnou rutinu pro zprávu provést nemá všechno done v odpovědi na tuto zprávu. Můžete vytvořit obslužných rutin pomocí okna Vlastnosti třídy a potom vyplňte v editoru kódu zdrojový kód obslužné rutiny.  
  
 Všechna zařízení Microsoft Visual C++ a MFC můžete použít k zápisu vaší obslužné rutiny. Seznam všechny třídy, naleznete v části [– přehled knihovny tříd](../mfc/class-library-overview.md) v *odkaz knihovny MFC*.  
  
## <a name="see-also"></a>Viz také  
 [Zprávy a příkazy v prostředí .NET Framework](../mfc/messages-and-commands-in-the-framework.md)

