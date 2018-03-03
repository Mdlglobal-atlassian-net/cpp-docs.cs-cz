---
title: "Postupy: použití křížových odkazů mapování zpráv | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.mfc.messages
dev_langs:
- C++
helpviewer_keywords:
- windows [MFC], message maps
ms.assetid: 2e863d23-9e58-45ba-b5e4-a8ceefccd0c8
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 25f78fb2e2c5700cbb1f7c8dcb093795ce001c13
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-use-the-message-map-cross-reference"></a>Postupy: Použití křížových odkazů mapování zpráv
V položkách s názvem bez přípony \<memberFxn >, napište vlastní funkci člena pro odvozený [CWnd](../../mfc/reference/cwnd-class.md) třídy. Zadejte funkce libovolný název, který chcete. Další funkce, jako například `OnActivate`, jsou funkce člena třídy `CWnd`. Pokud je volána, předají zprávu, která se `DefWindowProc` funkce systému Windows. Při zpracování zprávy oznámení Windows, přepsání odpovídající `CWnd` funkce v odvozené třídě. Funkce by měly volat funkci přepsaného v základní třídě umožníte základní třídy a Windows reagovat na zprávu.  
  
 Ve všech případech se umístí prototyp funkce `CWnd`– hlavička odvozené třídy a kód položku mapování zpráv, jak je vidět.  
  
 Se používají následující termíny:  
  
|Termín|Definice|  
|----------|----------------|  
|id|Žádné uživatelské ID položky nabídky (**wm_command –** zpráv) nebo ovládat ID (zprávy v podřízených oknech oznámení).|  
|"zpráva" a "wNotifyCode"|Windows zpráva ID, jak jsou definovány v systému WINDOWS. H.|  
|nMessageVariable|Název proměnné, která obsahuje vrácenou hodnotu z **RegisterWindowMessage** funkce systému Windows.|  
  
## <a name="see-also"></a>Viz také  
 [Mapy zpráv](../../mfc/reference/message-maps-mfc.md)

