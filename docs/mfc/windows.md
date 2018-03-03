---
title: Windows | Microsoft Docs
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
- objects [MFC], window
- windows [MFC]
- MFC, windows
- window objects [MFC], MFC Framework
ms.assetid: dd92bf34-842e-40fe-8aea-3028b55314d5
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e81be5ef0216f7d8a28ea7d5046c127f18670a6c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="windows"></a>Windows
Tato řada článků popisuje objekty oken v rozhraní MFC framework. Všechny systémy windows MFC odvozena od třídy [CWnd](../mfc/reference/cwnd-class.md), včetně okna s rámečkem, zobrazení, dialogových oken a ovládacích prvků.  
  
 První skupina článků popisuje [objekty oken](../mfc/window-objects.md) obecně. Odkazovat na tuto skupinu pro obecné informace o C++ objekty oken, jak zapouzdřují popisovačem HWND a jak je používat při vytváření vlastní windows, jako je například podřízená okna.  
  
 Druhá skupina článků popisuje [okna s rámečkem](../mfc/frame-windows.md)– windows, které ukládají kolem obsahu – konkrétně. Odkazovat na tuto skupinu pro informace o správě rozhraní MFC framework okna s rámečkem a obsah, který se rámce, včetně ovládací pruhy a zobrazení.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o  
 *Témata na objekty oken v obecné*  
  
-   [Objekty oken](../mfc/window-objects.md)  
  
-   [Vztah mezi jazyka C++ zpracovává objekty oken a HWND](../mfc/relationship-between-a-cpp-window-object-and-an-hwnd.md)  
  
-   [Odvozené třídy oken](../mfc/derived-window-classes.md)  
  
-   [Vytváření objektů oken](../mfc/creating-windows.md)  
  
-   [Zničení objektů oken](../mfc/destroying-window-objects.md)  
  
-   [Registrace tříd"oken"](../mfc/registering-window-classes.md)  
  
-   [Práce s objekty oken](../mfc/working-with-window-objects.md)  
  
-   [Kontexty zařízení](../mfc/device-contexts.md): objekty, které Windows kreslení nezávislé na zařízení  
  
-   [Grafické objekty](../mfc/graphic-objects.md): pera, štětce, písma, rastrové obrázky, palety, oblastí  
  
 *Témata týkající se rámce okna*  
  
-   [Okna s rámečkem](../mfc/frame-windows.md): objekty oken, které poskytují rámce  
  
-   [Zobrazení a oken s rámečkem](../mfc/frame-windows.md)  
  
-   [Třídy oken s rámečkem](../mfc/frame-window-classes.md)  
  
-   [Styly oken s rámečkem](../mfc/frame-window-styles-cpp.md)  
  
-   [Změna stylů okna vytvořeného rozhraním MFC](../mfc/changing-the-styles-of-a-window-created-by-mfc.md)  
  
-   [Co dělat okna s rámečkem](../mfc/what-frame-windows-do.md)  
  
-   [Použití oken s rámečkem](../mfc/using-frame-windows.md)  
  
-   [Správa MD/podřízených oken (okno MDICLIENT)](../mfc/managing-mdi-child-windows.md)  
  
-   [Správa nabídek, ovládacích pruhů a akcelerátorů](../mfc/managing-menus-control-bars-and-accelerators.md)  
  
-   [CFrameWnd](../mfc/reference/cframewnd-class.md)  
  
-   [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md)  
  
-   [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md)  
  
-   [Použití zobrazení](../mfc/using-views.md)  
  
-   [Více typů dokumentů, zobrazení a oken s rámečkem (rozdělovače windows)](../mfc/multiple-document-types-views-and-frame-windows.md)  
  
-   [Zprávy (mapy a funkce obslužných rutin)](../mfc/messages.md)  
  
 *Vytvoření a zrušení Windows*  
  
-   [Obecná posloupnost vytvoření okna](../mfc/general-window-creation-sequence.md)  
  
-   [Zničení objektů oken](../mfc/destroying-window-objects.md)  
  
-   [Vytvoření okna s rámečkem v dokumentu](../mfc/creating-document-frame-windows.md)  
  
-   [Zničení oken s rámečkem](../mfc/destroying-frame-windows.md)  
  
 *Vytvoření rozdělovače oken*  
  
-   [Vytvoření rozdělovače oken](../mfc/multiple-document-types-views-and-frame-windows.md)  
  
 *Správa podřízených oken a aktuální zobrazení*  
  
-   [Správa podřízených oken MDI](../mfc/managing-mdi-child-windows.md)  
  
-   [Správa aktuálního zobrazení](../mfc/managing-the-current-view.md)  
  
-   [Správa nabídek, ovládacích pruhů a akcelerátorů](../mfc/managing-menus-control-bars-and-accelerators.md)  
  
 *Práce s kontexty zařízení a styly oken*  
  
-   [Pomocí pera a jiné grafické objekty v kontextu zařízení](../mfc/graphic-objects.md)  
  
-   [Změna stylů okna vytvořeného rozhraním MFC](../mfc/changing-the-styles-of-a-window-created-by-mfc.md)  
  
## <a name="see-also"></a>Viz také  
 [Prvky uživatelského rozhraní](../mfc/user-interface-elements-mfc.md)   
 [Dialogová okna](../mfc/dialog-boxes.md)   
 [Panely nástrojů](../mfc/toolbars.md)   
 [Stavové řádky](../mfc/status-bars.md)   
 [Dialogové pruhy](../mfc/dialog-bars.md)

