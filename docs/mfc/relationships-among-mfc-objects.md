---
title: Vztahy mezi objekty MFC | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- MFC, relationships between key objects
- objects [MFC], relationships
- relationships, MFC objects
- MFC object relationships
ms.assetid: 6e8f3b51-e80f-4d88-94c8-4c1e4ee163ad
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 60d7c2276a980dfe1bfb6a6f99981a3a9d72994e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="relationships-among-mfc-objects"></a>Vztahy mezi objekty MFC
Pomoc při procesu vytváření dokumentů/zobrazení chápat perspektivy, zvažte spuštěným programem: dokument, okně s rámečkem obsahoval zobrazení a zobrazení přidružený k dokumentu.  
  
-   Dokument udržuje seznam zobrazení tento dokument a ukazatel na šablony dokumentu, která vytvořila dokumentu.  
  
-   Zobrazení udržuje ukazatel jeho dokumentu a je podřízená jeho nadřazeného rámce okna.  
  
-   Okně s rámečkem dokumentu udržuje ukazatel na jeho aktuální aktivní zobrazení.  
  
-   Šablona dokumentu udržuje seznam jeho otevřené dokumenty.  
  
-   Aplikace udržuje seznam jeho šablony dokumentu.  
  
-   Windows uchovává informace o všechna otevřená okna odesílání zpráv na ně.  
  
 Tyto vztahy se vytvoří během vytváření dokumentů/zobrazení. Následující tabulka ukazuje, jak jsou pro objekty v spuštěným programem přistupovat k jiné objekty. Jakýkoli objekt můžete získat ukazatele do objektu application voláním globální funkce [AfxGetApp](../mfc/reference/application-information-and-management.md#afxgetapp).  
  
### <a name="gaining-access-to-other-objects-in-your-application"></a>Získá přístup k ostatním objektům v aplikaci  
  
|Z objektu|Jak přistupovat k jiným objektům|  
|-----------------|---------------------------------|  
|Dokument|Použití [GetFirstViewPosition](../mfc/reference/cdocument-class.md#getfirstviewposition) a [GetNextView](../mfc/reference/cdocument-class.md#getnextview) pro přístup k dokumentu zobrazení seznamu.<br /><br /> Volání [GetDocTemplate](../mfc/reference/cdocument-class.md#getdoctemplate) získat šablonu dokumentu.|  
|Zobrazit|Volání [GetDocument](../mfc/reference/cview-class.md#getdocument) získat dokument.<br /><br /> Volání [GetParentFrame](../mfc/reference/cwnd-class.md#getparentframe) získat okně s rámečkem.|  
|Rámec okna dokumentu.|Volání [GetActiveView](../mfc/reference/cframewnd-class.md#getactiveview) získat aktuální zobrazení.<br /><br /> Volání [GetActiveDocument](../mfc/reference/cframewnd-class.md#getactivedocument) získat dokument připojený k aktuální zobrazení.|  
|Rámec okna MDI|Volání [MDIGetActive](../mfc/reference/cmdiframewnd-class.md#mdigetactive) získat aktuálně aktivní [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md).|  
  
 Obvykle okně s rámečkem má jedno zobrazení, ale v některých případech jako rozdělovače oken okně rámce obsahuje více zobrazení. Okně s rámečkem udržuje ukazatel na aktuálně aktivní zobrazení; ukazatel se aktualizuje, když se aktivuje jiného zobrazení.  
  
> [!NOTE]
>  Ukazatel na rámec hlavního okna je uložen v [m_pMainWnd](../mfc/reference/cwinthread-class.md#m_pmainwnd) členské proměnné objektu aplikace. Volání `OnFileNew` v přepsání z `InitInstance` členské funkce `CWinApp` nastaví `m_pMainWnd` za vás. Pokud není volána `OnFileNew`, je nutné nastavit hodnotu proměnné `InitInstance` sami. (Aplikace SDI COM součástí (server) se nemusí nastavte proměnnou, pokud je /Embedding na příkazovém řádku.) Všimněte si, že `m_pMainWnd` je nyní členem třídy `CWinThread` místo `CWinApp`.  
  
## <a name="see-also"></a>Viz také  
 [Šablony dokumentů a proces vytváření dokumentů/zobrazení](../mfc/document-templates-and-the-document-view-creation-process.md)   
 [Vytváření šablon dokumentů](../mfc/document-template-creation.md)   
 [Vytváření dokumentů/zobrazení](../mfc/document-view-creation.md)   
 [Vytváření nových dokumentů, oken a zobrazení](../mfc/creating-new-documents-windows-and-views.md)

