---
title: "Použití zobrazení | Microsoft Docs"
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
- interacting with users and role of view class [MFC]
- drawing [MFC], data
- rendering data
- view classes [MFC], role in managing user interaction
- CView class [MFC], view architecture
- MFC, views
- views [MFC], using
- painting data
- user input [MFC], interpreting through view class [MFC]
- view classes [MFC], role in displaying application data
ms.assetid: dc3de6ad-5c64-4317-8f10-8bdcc38cdbd5
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 99493657313d480559d232bf9033dfb7a7a585c4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="using-views"></a>Použití zobrazení
Zobrazení odpovědnosti se grafické zobrazení data dokumentu pro uživatele a přijměte a interpretace vstupu uživatele jako operace v dokumentu. Vaše úkoly ve třídě zobrazení zápis je:  
  
-   Zápis třídy zobrazení [OnDraw –](../mfc/reference/cview-class.md#ondraw) členská funkce, která vykreslí data dokumentu.  
  
-   Připojení odpovídající zpráv systému Windows a objekty uživatelského rozhraní, jako je například položek nabídky k obslužné rutiny zpráv členské funkce ve třídě zobrazení.  
  
-   Implementujte tyto rutiny interpretace vstupu uživatele.  
  
 Kromě toho budete muset přepsání dalších `CView` členské funkce ve třídě odvozené zobrazení. Konkrétně může chcete přepsat [OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate) provádět speciální inicializace pro zobrazení a [OnUpdate](../mfc/reference/cview-class.md#onupdate) udělat žádné speciální zpracování potřeby těsně před zobrazení ho překreslí sám sebe. Vícestránkové dokumenty je také nutné přepsat [OnPreparePrinting –](../mfc/reference/cview-class.md#onprepareprinting) k chybě při inicializaci dialogovém okně tisku s číslem stránky tisknout a další informace. Další informace o přepsání `CView` členské funkce v tématu třídy [CView](../mfc/reference/cview-class.md) v *odkaz knihovny MFC*.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o  
  
-   [Odvozené třídy zobrazení dostupné v prostředí MFC](../mfc/derived-view-classes-available-in-mfc.md)  
  
-   [Kreslení v zobrazení](../mfc/drawing-in-a-view.md)  
  
-   [Interpretace vstupu uživatele prostřednictvím zobrazení](../mfc/interpreting-user-input-through-a-view.md)  
  
-   [Role zobrazení v tisku](../mfc/role-of-the-view-in-printing.md)  
  
-   [Posouvání a změna měřítka zobrazení](../mfc/scrolling-and-scaling-views.md)  
  
-   [Inicializace a Uklízení dokumentů a zobrazení](../mfc/initializing-and-cleaning-up-documents-and-views.md)  
  
## <a name="see-also"></a>Viz také  
 [Document/View – architektura](../mfc/document-view-architecture.md)   
 [Třídy CFormView – třída](../mfc/reference/cformview-class.md)   
 [Zobrazení záznamů (Data MFC Access)](../data/record-views-mfc-data-access.md)   
 [Obcházení mechanismu serializace](../mfc/bypassing-the-serialization-mechanism.md)

