---
title: "Obslužné rutiny uživatelských tlačítek | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ON_BN_HILITE
- ON_BN_DOUBLECLICKED
- ON_BN_CLICKED
- ON_BN_PAINT
- ON_BN_DISABLE
- ON_BN_UNHILITE
dev_langs: C++
helpviewer_keywords:
- ON_BN_PAINT
- user buttons [MFC]
- ON_BN_DOUBLECLICKED [MFC]
- ON_BN_DISABLE [MFC]
- ON_BN_UNHILITE [MFC]
- ON_BN_HILITE [MFC]
- ON_BN_CLICKED [MFC]
ms.assetid: 410ea968-478f-4806-b7b8-5d7c8dc2bf42
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: eb5acc7a127af69d65536d131f9b388b4f4ff8f9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="user-button-handlers"></a>Obslužné rutiny uživatelských tlačítek
Následující položky mapy odpovídají prototypy funkcí.  
  
|Položku mapování|Prototyp funkce|  
|---------------|------------------------|  
|ON_BN_CLICKED ( \<id >, \<memberFxn >)|afx_msg void memberFxn ();|  
|ON_BN_DISABLE ( \<id >, \<memberFxn >)|afx_msg void memberFxn ();|  
|ON_BN_DOUBLECLICKED ( \<id >, \<memberFxn >)|afx_msg void memberFxn ();|  
|ON_BN_HILITE ( \<id >, \<memberFxn >)|afx_msg void memberFxn ();|  
|ON_BN_PAINT ( \<id >, \<memberFxn >)|afx_msg void memberFxn ();|  
|ON_BN_UNHILITE ( \<id >, \<memberFxn >)|afx_msg void memberFxn ();|  
  
## <a name="see-also"></a>Viz také  
 [Mapy zpráv](../../mfc/reference/message-maps-mfc.md)
