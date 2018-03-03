---
title: "Dokumenty, zobrazení a Framework | Microsoft Docs"
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
- document templates [MFC], template objects
- applications [MFC]
- MFC, application framework
- application objects [MFC], relation to other MFC objects
- documents [MFC]
- MFC, documents
- document objects [MFC], in relation to other MFC objects
- view objects [MFC], relation to other MFC objects
- MFC, views
- document/view architecture [MFC], about document/view architecture
- objects [MFC], MFC applications
- MFC object relationships
- thread objects [MFC]
ms.assetid: 409ddd9b-66ad-4625-84f7-bf55a41d697b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e48872907b07b0adf18cf17cca6ec6ecabe9e2de
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="documents-views-and-the-framework"></a>Dokumenty, zobrazení a framework
Jádrem rozhraní MFC framework jsou koncepty dokumentů a zobrazení. Dokument je datový objekt, pomocí kterého uživatel pracuje v relaci úpravy. Je vytvořený `New` nebo **otevřete** příkaz na **souboru** nabídky a je obvykle uložen v souboru. (Standardní MFC dokumenty, odvozené od třídy **CDocument**, se liší od aktivní dokumenty a složené dokumenty OLE.) Zobrazení je objekt okno, pomocí kterého uživatel pracuje s dokumentem.  
  
 Objekty klíče v běžící aplikaci jsou:  
  
-   Tento dokument nebo dokumenty.  
  
     Třídě dokumentů (odvozený z [CDocument](../mfc/reference/cdocument-class.md)) určuje data aplikace.  
  
     Pokud chcete v aplikaci OLE funkčnost, jsou odvozeny třídě dokumentu z [COleDocument](../mfc/reference/coledocument-class.md) nebo jeden z jejich odvozené třídy, v závislosti na typu funkce, které potřebujete.  
  
-   Zobrazení nebo zobrazení.  
  
     Zobrazení třídy (odvozený z [CView](../mfc/reference/cview-class.md)) je uživatele "okno na data." Třídy zobrazení řídí, jak uživateli se zobrazí data vašeho dokumentu a komunikuje s ním. V některých případech můžete dokument obsahovat dat více zobrazení.  
  
     Pokud potřebujete posouvání, odvozena od [CScrollView](../mfc/reference/cscrollview-class.md). Pokud zobrazení obsahuje uživatelské rozhraní, které je nastíněny v prostředku šablony dialogového okna, odvozena od [CFormView](../mfc/reference/cformview-class.md). Jednoduchý text data, použijte nebo odvozena od [CEditView](../mfc/reference/ceditview-class.md). Pro aplikaci na základě formulářů přístup k datům, jako je například program zadávání dat, jsou odvozeny od [CRecordView](../mfc/reference/crecordview-class.md) (pro rozhraní ODBC). K dispozici jsou také třídy [CTreeView](../mfc/reference/ctreeview-class.md), [CListView](../mfc/reference/clistview-class.md), a [cricheditview –](../mfc/reference/cricheditview-class.md).  
  
-   Okna s rámečkem  
  
     Zobrazení se zobrazí uvnitř "dokumentu rámce windows." V aplikaci SDI rámce okna dokumentu je také "hlavního okna rámce" pro aplikaci. V aplikaci MDI dokumentu windows jsou podřízená okna zobrazí uvnitř okno rámce. Třídě odvozené hlavní oken s rámečkem určuje stylů a dalších vlastností obsahující zobrazení okna s rámečkem. Pokud potřebujete k přizpůsobení okna s rámečkem, odvozena od [CFrameWnd](../mfc/reference/cframewnd-class.md) přizpůsobit rámce okna dokumentu pro aplikace SDI. Odvozena od [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md) přizpůsobit hlavního rámce okna pro aplikace MDI. Také odvození třídy z [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md) přizpůsobit jednotlivé odlišné typy oken MDI dokumentu rámečku, které podporuje vaše aplikace.  
  
-   Dokument šablony nebo šablony  
  
     Šablona dokumentu orchestruje vytvářet dokumenty, zobrazení a oken s rámečkem. Třídy šablony dokumentu konkrétní, odvozené od třídy [CDocTemplate](../mfc/reference/cdoctemplate-class.md), vytváří a spravuje všechny otevřené dokumenty jednoho typu. Aplikace, které podporují víc než jeden typ dokumentu mít více šablon dokumentů. Použití třídy [CSingleDocTemplate](../mfc/reference/csingledoctemplate-class.md) pro aplikace SDI nebo použijte třídu [CMultiDocTemplate](../mfc/reference/cmultidoctemplate-class.md) pro aplikace MDI.  
  
-   Objekt aplikace  
  
     Třídě aplikace (získané z [CWinApp](../mfc/reference/cwinapp-class.md)) řídí všechny výše uvedené objekty a určuje chování aplikace, jako je například inicializace a čištění. Jedna aplikace a aplikace pouze objekt vytváří a spravuje šablony dokumentů pro libovolného dokumentu typy aplikace podporuje.  
  
-   Objekty vláken  
  
     Pokud vaše aplikace vytvoří samostatných vláknech provádění – například provádět výpočty na pozadí – použijete třídy odvozené od třídy [CWinThread](../mfc/reference/cwinthread-class.md). [CWinApp](../mfc/reference/cwinapp-class.md) samotné je odvozený od `CWinThread` a představuje primární vlákno provádění (nebo proces hlavní) ve vaší aplikaci. Můžete také použít MFC v sekundární vláken.  
  
 Ve spuštěné aplikaci tyto objekty spolupráce při reagovat na akce uživatele, spojuje příkazy a další zprávy. Objekt jednu aplikaci spravuje jednu nebo více šablon dokumentů. Každá šablona dokumentu vytváří a spravuje jeden nebo více dokumentů (v závislosti na tom, zda je aplikace SDI a MDI). Zobrazení a umožňuje pracovat s dokumentem prostřednictvím zobrazení nachází v okně s rámečkem uživatele. Následující obrázek znázorňuje vztahy mezi tyto objekty pro aplikace SDI.  
  
 ![Objekty v běžící aplikaci SDI](../mfc/media/vc386v1.gif "vc386v1")  
Objekty v běžící aplikaci SDI  
  
 Zbývající část této rodině článků vysvětluje, jak framework nástroje, Průvodce aplikací knihovny MFC a editory prostředků vytvořit tyto objekty, jak pracují společně a jak je používat ve vaší programování. Dokumenty, zobrazení a oken s rámečkem jsou podrobněji popsána v [objekty oken](../mfc/window-objects.md) a [Document/View – architektura](../mfc/document-view-architecture.md).  
  
## <a name="see-also"></a>Viz také  
 [Použití tříd pro psaní aplikací pro Windows](../mfc/using-the-classes-to-write-applications-for-windows.md)
