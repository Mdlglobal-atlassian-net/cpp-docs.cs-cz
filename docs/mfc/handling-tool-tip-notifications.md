---
title: "Zpracování oznámení popisů tlačítek | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- TOOLTIPTEXT structure [MFC]
- CToolBarCtrl class [MFC], handling notifications
- notifications [MFC], tool tips
- tool tips [MFC], notifications
ms.assetid: ddb93b5f-2e4f-4537-8053-3453c86e2bbb
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 6d6ec102d38e91389fddb3faf4eb83ace9ba7129
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="handling-tool-tip-notifications"></a>Zpracování oznámení popisů tlačítek
Pokud zadáte `TBSTYLE_TOOLTIPS` styl panelu nástrojů vytváří a spravuje prvkem popis tlačítka. Popis tlačítka je malé místní okno, které obsahuje na řádku textu s popisem tlačítka panelu nástrojů. Popis tlačítka je skrytý, zobrazování, pouze když uživatel uloží kurzor na tlačítka panelu nástrojů a ponechá ji existuje pro přibližně polovinu druhý. Popis tlačítka se zobrazí téměř kurzor.  
  
 Před zobrazením Popis tlačítka, **TTN_NEEDTEXT** oznámení je odeslána zpráva do okna vlastník panelu nástrojů načíst popisný text pro tlačítko. Pokud je okno vlastník panelu nástrojů `CFrameWnd` okno, nástroj tipy zobrazují bez žádné další úsilí, protože `CFrameWnd` má výchozí obslužnou rutinu pro **TTN_NEEDTEXT** oznámení. Pokud okno vlastník panelu nástrojů není odvozen od `CFrameWnd`, například dialogové okno pole nebo formátu zobrazení, musíte přidat položku do nadřazené okno mapy zpráv a poskytnout obslužná rutina oznámení v mapy zpráv. Položka k nadřazené okno mapy zpráv vypadá takto:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#40](../mfc/codesnippet/cpp/handling-tool-tip-notifications_1.cpp)]  
  
## <a name="remarks"></a>Poznámky  
 `memberFxn`  
 Členská funkce se volá, když pro toto tlačítko je nutné zadat text.  
  
 Všimněte si, že id popisku tlačítka je vždy 0.  
  
 Kromě **TTN_NEEDTEXT** oznámení, prvkem popis tlačítka může odesílat následující oznámení do ovládacího prvku panel nástrojů:  
  
|oznámení|Význam|  
|------------------|-------------|  
|**TTN_NEEDTEXTA**|Prvkem popis tlačítka vyžaduje text ASCII (pouze systém Windows 95)|  
|**TTN_NEEDTEXTW**|Text v kódu UNICODE (pouze systém Windows NT) vyžaduje prvkem popis tlačítka|  
|**TBN_HOTITEMCHANGE**|Označuje, že došlo ke změně aktivního (zvýrazněné) položky.|  
|**NM_RCLICK –**|Označuje, že uživatel má klepli pravým tlačítkem myši na tlačítko.|  
|**TBN_DRAGOUT**|Označuje uživatel klikne na tlačítko a přetáhnout ukazatel mimo tlačítko. Umožňuje aplikaci k implementaci přetažení a vyřadit z tlačítka panelu nástrojů. Při příjmu tohoto oznámení, aplikace se začít přetahování a vyřadit operaci.|  
|**TBN_DROPDOWN –**|Označuje uživatel má kliknutí na tlačítko, které používá **TBSTYLE_DROPDOWN** stylu.|  
|**TBN_GETOBJECT**|Označuje uživatel přesunout ukazatel myši nad tlačítko, které používá **TBSTYLE_DROPPABLE** stylu.|  
  
 Příklad funkce obslužné rutiny a další informace o povolení tipů nástrojů najdete v tématu [popisy](../mfc/tool-tips-in-windows-not-derived-from-cframewnd.md).  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CToolBarCtrl](../mfc/using-ctoolbarctrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

