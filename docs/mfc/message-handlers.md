---
title: Obslužné rutiny zpráv | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- message handlers [MFC]
- command handling [MFC], message handlers
- handlers [MFC]
- message handling [MFC], message handler functions
- handlers [MFC], command
- handlers [MFC], message
ms.assetid: 51bc4e76-dbe3-4cc2-b026-3199d56b2fa9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: be4ccf9ec33e5ddf497193c1942e9f300f8cae57
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="message-handlers"></a>Obslužné rutiny zpráv
V prostředí MFC vyhrazená *obslužná rutina* funkce zpracuje každou samostatnou zprávu. Funkce obslužné rutiny zpráv jsou funkce člena třídy. Tato dokumentace používá podmínky *obslužné rutiny zpráv – členská funkce*, *funkce obslužné rutiny zpráv*, *obslužné rutiny zpráv*, a *obslužná rutina*zcela zaměnitelným významem. Některé druhy obslužné rutiny zpráv se také označují jako "obslužné rutiny příkazů."  
  
 Zápis účty obslužné rutiny zpráv pro velkou část vaší práce v zápisu framework aplikace. Rodina Tento článek popisuje, jak funguje mechanismus zpracování zprávy.  
  
 Jaké jsou obslužnou rutinu pro zprávu provést nemá všechno done v odpovědi na tuto zprávu. Můžete vytvořit obslužných rutin pomocí okna Vlastnosti třídy a potom vyplňte v editoru kódu zdrojový kód obslužné rutiny.  
  
 Všechna zařízení Microsoft Visual C++ a MFC můžete použít k zápisu vaší obslužné rutiny. Seznam všechny třídy, naleznete v části [– přehled knihovny tříd](../mfc/class-library-overview.md) v *odkaz knihovny MFC*.  
  
## <a name="see-also"></a>Viz také  
 [Zprávy a příkazy v prostředí .NET Framework](../mfc/messages-and-commands-in-the-framework.md)

