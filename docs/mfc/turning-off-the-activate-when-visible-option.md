---
title: "Aktivovat při viditelné možnost vypnutí | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], activate options
- Activate When Visible option [MFC]
ms.assetid: 8f7ddc5a-a7a6-4da8-bcb9-1b569f0ecb48
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 9ecc0257cf087a28c0186adaffb795f3e33253b2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="turning-off-the-activate-when-visible-option"></a>Vypnutí možnosti Activate When Visible
Ovládací prvek má dva základní stavy: aktivní a neaktivní. Dříve bylo zvykem, že tyto stavy byly rozlišeny skutečností, zda ovládací prvek má okno. Aktivní ovládací prvek okno měl, neaktivní nikoli. Se zavedením aktivace bez oken není již toto rozlišení univerzální, ale pro mnoho ovládacích prvků je stále platné.  
  
 Vytvoření okna ve srovnání s ostatními inicializace obvykle provádí ovládací prvek ActiveX, je velmi náročná operace. V ideálním případě by ovládacího prvku odložení vytváření její okno, dokud je to nezbytně nutné.  
  
 Mnoho ovládacích prvků nemusíte být aktivní po celou dobu, které jsou viditelné v kontejneru. Ovládací prvek často, může zůstat v neaktivním stavu, dokud uživatel provede operaci, která vyžaduje, aby se aktivní (například kliknutí myší nebo stisknutím klávesy TAB). Aby zůstat neaktivní, dokud kontejneru musí být aktivován ovládací prvek, odeberte **OLEMISC_ACTIVATEWHENVISIBLE** příznak z ovládacího prvku různé příznaky:  
  
 [!code-cpp[NVC_MFC_AxOpt#9](../mfc/codesnippet/cpp/turning-off-the-activate-when-visible-option_1.cpp)]  
  
 **OLEMISC_ACTIVATEWHENVISIBLE** příznak automaticky vynecháte Pokud vypnete **Activate When Visible** možnost [nastavení řízení](../mfc/reference/control-settings-mfc-activex-control-wizard.md) stránky MFC ActiveX Průvodce ovládacím prvkem při vytváření vlastního ovládacího prvku.  
  
## <a name="see-also"></a>Viz také  
 [MFC – ovládací prvky ActiveX: optimalizace](../mfc/mfc-activex-controls-optimization.md)
