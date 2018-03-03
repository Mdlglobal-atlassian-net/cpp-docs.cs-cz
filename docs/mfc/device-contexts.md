---
title: "Kontexty zařízení | Microsoft Docs"
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
- OnPrepareDC method [MFC]
- windows [MFC], and device context
- drawing [MFC], device context
- CClientDC class [MFC], and GetDC method [MFC]
- drawing [MFC], in mouse and device contexts
- CDC class [MFC], objects
- device contexts [MFC]
- client areas
- CMetaFileDC class [MFC], and OnPrepareDC method [MFC]
- GDI objects [MFC], device contexts
- graphic objects [MFC], device contexts
- frame windows [MFC], device contexts
- metafiles and device contexts
- EndPaint method [MFC]
- printers [MFC], device contexts
- mouse [MFC], drawing and device contexts
- BeginPaint method, CPaintDC
- CPaintDC class [MFC], device context for painting
- windows [MFC], drawing directly into
- client areas, and device context
- device contexts [MFC], CDC class [MFC]
- user interface [MFC], device contexts
- device-independent drawing
- GetDC method and CClientDC class [MFC]
- CClientDC class [MFC], and ReleaseDC method [MFC]
- ReleaseDC method [MFC]
- device contexts [MFC], about device contexts
- drawing [MFC], directly into windows
- painting and device context
ms.assetid: d0cd51f1-f778-4c7e-bf50-d738d10433c7
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 26d4a0e32a8b24a72447cf4227be128659316c0b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="device-contexts"></a>Kontexty zařízení
Kontext zařízení je datová struktura Windows obsahující informace o kreslení atributy zařízení, například zobrazení nebo tiskárnu. Všechny kreslení volání prostřednictvím objektu kontextu zařízení, který zapouzdřuje rozhraní API systému Windows pro kreslení čáry, tvary a text. Kontexty zařízení povolí kreslení nezávislé na zařízení v systému Windows. Kontexty zařízení lze použít k vykreslení na obrazovku, na tiskárnu nebo metasoubory.  
  
 [CPaintDC](../mfc/reference/cpaintdc-class.md) objekty zapouzdřují běžné stylu systému Windows, volání `BeginPaint` funkce, a kreslení v kontextu zařízení a potom volání `EndPaint` funkce. `CPaintDC` Volá konstruktor `BeginPaint` , a volání destruktoru `EndPaint`. Zjednodušený proces je vytvoření [CDC](../mfc/reference/cdc-class.md) objektu, kreslení a pak odstraňte `CDC` objektu. V rozhraní framework většinu i tento proces automatizovat. Konkrétně vaše `OnDraw` funkce je předána `CPaintDC` již připravena (prostřednictvím `OnPrepareDC`), a jednoduše kreslení do ní. Byla rámcem a základního kontextu zařízení vydání systému Windows po návratu z volání vaší `OnDraw` funkce.  
  
 [CClientDC](../mfc/reference/cclientdc-class.md) objekty zapouzdřují práci s kontext zařízení, který představuje pouze klientské oblasti časového období. `CClientDC` Volá konstruktor `GetDC` funkce a volání destruktoru `ReleaseDC` funkce. [CWindowDC](../mfc/reference/cwindowdc-class.md) objekty zapouzdřují kontextu zařízení, která představuje celou okna, včetně jeho rámečku.  
  
 [CMetaFileDC](../mfc/reference/cmetafiledc-class.md) objekty zapouzdřují kreslení do WMF. Rozdíl k `CPaintDC` předaný `OnDraw`, v takovém případě musí volat [onpreparedc –](../mfc/reference/cview-class.md#onpreparedc) sami.  
  
## <a name="mouse-drawing"></a>Kreslení myši  
 Většina kreslení v rámci programu – a tedy většinu práce kontextu zařízení – se provádí v zobrazení `OnDraw` – členská funkce. Objekty kontextu zařízení ale můžete použít pro jiné účely. Například k poskytnutí zpětné vazby sledování pohybu myši v zobrazení, budete muset kreslení přímo do zobrazení bez čekání na `OnDraw` k volání.  
  
 V takovém případě můžete použít [CClientDC](../mfc/reference/cclientdc-class.md) objekt kontextu zařízení kreslení přímo do zobrazení.  
  
### <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o  
  
-   [Kontexty zařízení (definice)](http://msdn.microsoft.com/library/windows/desktop/dd183553)  
  
-   [Kreslení v zobrazení](../mfc/drawing-in-a-view.md)  
  
-   [Interpretace vstupu uživatele prostřednictvím zobrazení](../mfc/interpreting-user-input-through-a-view.md)  
  
-   [Čar a křivek](http://msdn.microsoft.com/library/windows/desktop/dd145028)  
  
-   [Vyplněné tvary](http://msdn.microsoft.com/library/windows/desktop/dd162714)  
  
-   [Písma a text.](http://msdn.microsoft.com/library/windows/desktop/dd144819)  
  
-   [Barvy](http://msdn.microsoft.com/library/windows/desktop/dd183450)  
  
-   [Mezery souřadnic a transformace](http://msdn.microsoft.com/library/windows/desktop/dd183475)  
  
## <a name="see-also"></a>Viz také  
 [Objekty oken](../mfc/window-objects.md)

