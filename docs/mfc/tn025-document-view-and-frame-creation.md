---
title: 'Tn025: vytvoření Dokumentu, zobrazení a rámečku | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.creation
dev_langs:
- C++
helpviewer_keywords:
- documents [MFC], view and frame creation
- TN025
ms.assetid: 09254d72-6e1d-43db-80e9-693887dbeda2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 97db14dcb8c0b8b5b71823cf39d6bf36f0d19f25
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2018
ms.locfileid: "36956691"
---
# <a name="tn025-document-view-and-frame-creation"></a>TN025: Vytvoření dokumentu, zobrazení a rámečku
> [!NOTE]
>  Následující Technická poznámka nebyla aktualizována vzhledem k tomu, že byla poprvé zahrnuta v online dokumentaci. V důsledku toho některé postupy a témata může být zastaralý nebo není správný. Nejnovější informace se doporučuje, vyhledejte téma týkající se v indexu online dokumentaci.  
  
 Tato poznámka popisuje problémy vytváření a vlastnictví pro WinApps, DocTemplates, dokumentů, snímky a zobrazení.  
  
## <a name="winapp"></a>WinApp  
 Existuje `CWinApp` objektu v systému.  
  
 Je staticky sestavený a inicializuje pomocí rozhraní framework interní implementace `WinMain`. Musí být odvozeny od `CWinApp` udělat nic užitečného (výjimka: MFC – rozšiřující knihovny DLL by neměl mít `CWinApp` instance – inicializace se provádí v `DllMain` místo).  
  
 Ten `CWinApp` seznam šablon dokumentů, které vlastní objekt ( `CPtrList`). Je jeden nebo více šablona dokumentu na aplikaci. DocTemplates jsou obvykle načtený ze souboru prostředků (to znamená, pole řetězců) v `CWinApp::InitInstance`.  
  
```  
pTemplate = new CDocTemplate(IDR_MYDOCUMENT, ...);

AddDocTemplate(pTemplate);
```  
  
 Ten `CWinApp` objektu vlastní všechna okna s rámečkem v aplikaci. Hlavní okno rámce pro aplikace by měly být uložené v `CWinApp::m_pMainWnd`; obvykle nastavíte *m_pMainWnd* v `InitInstance` implementace Pokud necháte nebyly objekty AppWizard to pro vás udělal. Pro jednotlivý dokument (SDI rozhraní) Toto je jedna `CFrameWnd` sloužícím jako hlavního rámce okna aplikace a také pouze rámce okna dokumentu. Pro rozhraní více dokumentů (MDI) jde MDI rámce (třída `CMDIFrameWnd`) sloužícím jako rámec okna hlavní aplikace, který obsahuje všechny podřízené `CFrameWnd`s. Každý podřízeného okna je třídy `CMDIChildWnd` (odvozený z `CFrameWnd`) a slouží jako jeden z okna s rámečkem potenciálně mnoho dokumentu.  
  
## <a name="doctemplates"></a>DocTemplates  
 `CDocTemplate` Je creator a správce dokumentů. Vlastní dokumenty, které vytvoří. Pokud vaše aplikace používá přístup podle prostředků popsaných níže, nebude potřebovat k odvozování z `CDocTemplate`.  
  
 Pro aplikace SDI třída `CSingleDocTemplate` uchovává informace o jeden dokument otevřít. Pro aplikace MDI třída `CMultiDocTemplate` udržuje seznam ( `CPtrList`) z všechny aktuálně otevřené dokumenty vytvořené z této šablony. `CDocTemplate::AddDocument` a `CDocTemplate::RemoveDocument` zadejte člena virtuální funkce pro přidání nebo odebrání dokumentu ze šablony. `CDocTemplate` je přítel z `CDocument` tak jsme můžete nastavit chráněného `CDocument::m_pDocTemplate` zpětný ukazatel odkazovat zpět do dokumentů šablony, která vytvořila dokumentu.  
  
 `CWinApp` zpracovává výchozí `OnFileOpen` implementace, které pak odešle dotaz všech šablon dokumentů. Implementace zahrnuje hledá již otevřené dokumenty a při rozhodování o tom, co chcete-li otevřít nové dokumenty ve formátu.  
  
 `CDocTemplate` spravuje vazby uživatelského rozhraní pro dokumenty a rámce.  
  
 `CDocTemplate` zachová počet nepojmenované dokumenty.  
  
## <a name="cdocument"></a>CDocument  
 A `CDocument` je vlastněna `CDocTemplate`.  
  
 Dokumenty mít seznam aktuálně otevřít zobrazení (odvozený z `CView`), jsou zobrazení dokumentu ( `CPtrList`).  
  
 Dokumenty není vytvoření nebo odstranění zobrazení, ale jsou připojené k sobě navzájem po jejich vytvoření. Při uzavření dokumentu (to znamená, pomocí souboru nebo ukončení), všechny připojené zobrazení bude uzavřeno. Při zavření posledního zobrazení v dokumentu (to znamená, okno nebo ukončení) bude uzavřen dokumentu.  
  
 `CDocument::AddView`, `RemoveView` Rozhraní slouží k udržování zobrazení seznamu. `CDocument` je přítel z `CView` tak jsme můžete nastavit `CView::m_pDocument` zpětný ukazatel.  
  
## <a name="cframewnd"></a>CFrameWnd  
 A `CFrameWnd` (také označované jako rámečkem) hraje roli stejné jako MFC 1.0, ale nyní `CFrameWnd` třída je určen k použití v mnoha případech bez odvozování novou třídu. Odvozené třídy `CMDIFrameWnd` a `CMDIChildWnd` také líp, jsou už implementované mnoho standardní příkazy.  
  
 `CFrameWnd` Zodpovídá za vytvoření windows v klientské oblasti rámečku. Obvykle je jeden hlavní okno vyplnění klientské oblasti rámečku.  
  
 Klientské oblasti pro okno s rámečkem MDI je vyplněn MDICLIENT řídit, která je zase nadřazeného všechny MDI – podřízená okna rámce. Okno s rámečkem SDI nebo okno s rámečkem podřízeného MDI, je klientské oblasti obvykle vyplněn `CView`-odvozené objektu okna. U `CSplitterWnd`, klientské oblasti zobrazení, naplní se `CSplitterWnd` objektu okna a `CView`-okno odvozené objekty (jeden na podokně rozdělení) jsou vytvořené jako podřízená okna z `CSplitterWnd`.  
  
## <a name="see-also"></a>Viz také  
 [Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)   
 [Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)

