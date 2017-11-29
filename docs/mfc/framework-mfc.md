---
title: Framework (MFC) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- encapsulation [MFC], Win32 API
- MFC, application framework
- wrapper classes [MFC], explained
- Win32 [MFC], API encapsulation by MFC
- application framework [MFC], about MFC application framework
- APIs [MFC], encapsulation by MFC Win32
- encapsulation [MFC]
- Windows API [MFC], encapsulation by MFC
- encapsulated Win32 API [MFC]
ms.assetid: 3be0fec8-9843-4119-ae42-ece993ef500b
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 09be7a5efbf3f78aa3cbc1862b811fff3d487c75
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="framework-mfc"></a>Framework (MFC)
Práci s framework knihovna Microsoft Foundation Class (MFC) vychází z velké části několik hlavní třídy a několik nástrojů Visual C++. Některé třídy zapouzdřují velkou část Win32 aplikační programovací rozhraní (API). Ostatní třídy zapouzdřovat koncepty aplikace, jako jsou dokumenty, zobrazení a vlastní aplikace. Stále ostatní zapouzdřovat OLE a rozhraní ODBC a DAO funkcí přístup k datům.  
  
 Například je Win32 na konceptu okno zapouzdřený třídou MFC `CWnd`. Tedy třídu C++ názvem `CWnd` zapouzdří nebo "zabalí" `HWND` popisovač, který představuje okno Windows. Podobně třídy `CDialog` zapouzdří Win32 dialogových oken.  
  
 Zapouzdření znamená, že třídami C++ `CWnd`, například obsahuje členské proměnné typu `HWND`, a členské funkce třídy zapouzdření volání Win32 funkcí, které přijímají `HWND` jako parametr. Členské funkce tříd obvykle mají stejný název jako Win32 funkce, které budou zapouzdření.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [SDI a MDI](../mfc/sdi-and-mdi.md)  
  
 [Dokumenty, zobrazení a Framework](../mfc/documents-views-and-the-framework.md)  
  
 [Průvodci a editory prostředků](../mfc/wizards-and-the-resource-editors.md)  
  
## <a name="in-related-sections"></a>V související oddíly  
 [Vytváření v rozhraní Framework](../mfc/building-on-the-framework.md)  
  
 [Jakým způsobem volá rámec váš kód](../mfc/how-the-framework-calls-your-code.md)  
  
 [CWinApp – Třída aplikace](../mfc/cwinapp-the-application-class.md)  
  
 [Šablony dokumentů a proces vytváření dokumentů/zobrazení](../mfc/document-templates-and-the-document-view-creation-process.md)  
  
 [Zpracování a mapování zpráv](../mfc/message-handling-and-mapping.md)  
  
 [Objekty oken](../mfc/window-objects.md)  
  
## <a name="see-also"></a>Viz také  
 [Použití tříd pro psaní aplikací pro Windows](../mfc/using-the-classes-to-write-applications-for-windows.md)