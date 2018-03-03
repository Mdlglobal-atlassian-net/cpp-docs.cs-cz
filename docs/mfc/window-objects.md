---
title: Objekty oken | Microsoft Docs
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
- Windows window [MFC]
- MFC, windows
- frame windows [MFC], C++ window objects
- window objects [MFC]
- windows [MFC], C++ window objects
- window messages [MFC]
- HWND
- messages [MFC], Windows
- Visual C++, window objects [MFC]
- HWND, window objects [MFC]
ms.assetid: 28b33ce2-af05-4617-9d03-1cb9a02be687
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 15f53db2d0ec6a57261e22c58abd3e5e8423b716
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="window-objects"></a>Objekty oken
Poskytuje třídy MFC [CWnd](../mfc/reference/cwnd-class.md) k zapouzdření `HWND` popisovač okna. `CWnd` C++ okno objektů, liší od `HWND` Windows, která představuje okno, ale který jej obsahuje. Použít `CWnd` odvození vlastní podřízeného okna třídy, nebo použijte jednu z mnoha tříd MFC odvozené od `CWnd`. Třída `CWnd` je základní třída pro všechny windows, včetně okna s rámečkem, dialogová okna, podřízená okna, ovládací prvky a ovládací pruhy například panely nástrojů. Dobrou znalost jazyka [vztah mezi objektem okna v C++ a popisovačem HWND](../mfc/relationship-between-a-cpp-window-object-and-an-hwnd.md) je zásadní pro efektivní programování s knihovnou MFC.  
  
 MFC poskytuje některé výchozí funkce a správy systému windows, ale lze odvodit vlastní třídu z `CWnd` a použít jeho členské funkce k přizpůsobení zadané funkce. Můžete vytvořit podřízenou windows vytvořením `CWnd` objekt a volání jeho [vytvořit](../mfc/reference/cwnd-class.md#create) členské funkce a potom přizpůsobit podřízená okna pomocí `CWnd` členské funkce. Můžete vložit objekty, které jsou odvozené z [CView](../mfc/reference/cview-class.md), jako jsou například zobrazení formulářů a stromové zobrazení, v okně s rámečkem. A může podporovat více zobrazení dokumentů prostřednictvím podokna rozdělovače, poskytl třída [CSplitterWnd](../mfc/reference/csplitterwnd-class.md).  
  
 Každý objekt odvozené od třídy `CWnd` obsahuje mapy zpráv, pomocí kterého můžete mapování zpráv systému Windows nebo příkaz ID pro svoje vlastní obslužné rutiny.  
  
 Obecné dokumentace v programování pro systém Windows je dobré prostředku pro naučit se používat `CWnd` členské funkce, které zapouzdření `HWND` rozhraní API.  
  
## <a name="functions-for-operating-on-a-cwnd"></a>Funkce pro práci na třídy CWnd  
 `CWnd`a jeho [odvozené třídy oken](../mfc/derived-window-classes.md) poskytují konstruktory, destruktory a členské funkce k inicializaci objektu, vytvořit základní struktury systému Windows a přístup zapouzdřené `HWND`. `CWnd`také poskytuje členské funkce, které zapouzdření rozhraní API systému Windows pro odesílání zpráv, přístup k okna stavu, převod souřadnice, aktualizaci, posouvání, přístup k schránky a mnoho dalších úkolů. Většina rozhraní API systému Windows Správa oken, který trvat `HWND` argument se zapouzdřené jako členské funkce `CWnd`. Názvy funkcí a jejich parametrů se zachovají v `CWnd` – členská funkce. Podrobnosti o rozhraní API systému Windows zapouzdřené pomocí `CWnd`, najdete v části třídy [CWnd](../mfc/reference/cwnd-class.md).  
  
## <a name="cwnd-and-windows-messages"></a>CWnd a zpráv systému Windows  
 Jedním z primárních účelů `CWnd` je poskytnout rozhraní pro zpracování zpráv systému Windows, jako například `WM_PAINT` nebo `WM_MOUSEMOVE`. Mnoho z členské funkce `CWnd` jsou obslužné rutiny pro standardní zprávy – těch, které začínají s identifikátorem **afx_msg** a předponu "Na", například `OnPaint` a **onmousemove –**. [Zpracování a mapování zpráv](../mfc/message-handling-and-mapping.md) zahrnuje zprávy a zpracování podrobně zpráv. Informace o existuje vztahuje stejnou měrou na rozhraní framework windows a ty vytvořit sami pro zvláštní účely.  
  
### <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o  
  
-   [Vztah mezi objektem okna v C++ a popisovačem HWND](../mfc/relationship-between-a-cpp-window-object-and-an-hwnd.md)  
  
-   [Odvozené třídy oken](../mfc/derived-window-classes.md)  
  
-   [Vytváření oken](../mfc/creating-windows.md)  
  
-   [Zničení objektů oken](../mfc/destroying-window-objects.md)  
  
-   [Odpojení třídy CWnd od jejího prvku HWND](../mfc/detaching-a-cwnd-from-its-hwnd.md)  
  
-   [Práce s objekty oken](../mfc/working-with-window-objects.md)  
  
-   [Kontexty zařízení](../mfc/device-contexts.md): objekty, které Windows kreslení zařízení nezávislé  
  
-   [Grafické objekty](../mfc/graphic-objects.md): pera, štětce, písma, rastrové obrázky, palety, oblastí  
  
## <a name="see-also"></a>Viz také  
 [Windows](../mfc/windows.md)

