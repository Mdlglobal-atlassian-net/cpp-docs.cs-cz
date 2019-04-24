---
title: Vztahy mezi objekty MFC
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, relationships between key objects
- objects [MFC], relationships
- relationships, MFC objects
- MFC object relationships
ms.assetid: 6e8f3b51-e80f-4d88-94c8-4c1e4ee163ad
ms.openlocfilehash: bb8d1fcd9737b33d52038746a26f4e1bd1043e95
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62309041"
---
# <a name="relationships-among-mfc-objects"></a>Vztahy mezi objekty MFC

Pokud chcete vložit v procesu vytváření dokumentů/zobrazení perspektivy, vezměte v úvahu spuštěný program: dokument, okno rámce pro nové zobrazení a zobrazení spojené s dokumentem.

- Dokument udržuje seznam zobrazení daný dokument a ukazatel na šablonu dokumentu, který vytvořil dokument.

- Zobrazení uchovává ukazatel na jeho dokument a je podřízeným prvkem nezašle nadřazenému oknu rámce.

- Okno rámce dokumentu uchovává ukazatel na její aktuální aktivní zobrazení.

- Šablona dokumentu udržuje seznam jeho otevřených dokumentů.

- Aplikace udržuje seznam jeho šablony dokumentů.

- Windows uchovává informace o všechna otevřená okna odesílání zpráv do nich.

Tyto vztahy jsou vytvořeny během vytváření dokumentů/zobrazení. Následující tabulka ukazuje, jak objekty v běžící aplikaci můžete získat přístup k jiné objekty. Libovolný objekt lze získat ukazatel objektu aplikace voláním globální funkce [AfxGetApp](../mfc/reference/application-information-and-management.md#afxgetapp).

### <a name="gaining-access-to-other-objects-in-your-application"></a>Získání přístupu k jiným objektům v aplikaci

|Z objektu|Jak získat přístup k jiné objekty|
|-----------------|---------------------------------|
|Dokument|Použití [GetFirstViewPosition](../mfc/reference/cdocument-class.md#getfirstviewposition) a [GetNextView](../mfc/reference/cdocument-class.md#getnextview) pro přístup k dokumentu zobrazení seznamu.<br /><br /> Volání [GetDocTemplate](../mfc/reference/cdocument-class.md#getdoctemplate) získat šablonu dokumentu.|
|Zobrazit|Volání [GetDocument](../mfc/reference/cview-class.md#getdocument) k získání dokumentu.<br /><br /> Volání [GetParentFrame](../mfc/reference/cwnd-class.md#getparentframe) zobrazíte okno rámce.|
|Okna rámce dokumentu|Volání [GetActiveView](../mfc/reference/cframewnd-class.md#getactiveview) zobrazíte aktuální zobrazení.<br /><br /> Volání [GetActiveDocument](../mfc/reference/cframewnd-class.md#getactivedocument) zobrazíte na dokument připojený k aktuální zobrazení.|
|Okno rámce MDI|Volání [MDIGetActive](../mfc/reference/cmdiframewnd-class.md#mdigetactive) zobrazíte aktuálně aktivní [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md).|

Obvykle má okno rámce jedno zobrazení, ale v některých případech jako rozdělovače oken stejné okno rámce obsahuje několik zobrazení. Okno rámce uchovává ukazatel na aktuálně aktivní zobrazení. ukazatel se aktualizuje pokaždé, když se aktivuje jiné zobrazení.

> [!NOTE]
>  Ukazatel na hlavní okno rámce je uložen v [m_pMainWnd](../mfc/reference/cwinthread-class.md#m_pmainwnd) členské proměnné objektu aplikace. Volání `OnFileNew` v přepsání metody `InitInstance` členskou funkci `CWinApp` nastaví *m_pMainWnd* za vás. Pokud není volána `OnFileNew`, je nutné nastavit hodnotu proměnné v `InitInstance` sami. (Aplikace SDI COM součástí (server) se nemusí nastavte proměnnou, je-li/Embedding na příkazovém řádku.) Všimněte si, že *m_pMainWnd* je teď členem třídy `CWinThread` spíše než `CWinApp`.

## <a name="see-also"></a>Viz také:

[Šablony dokumentů a proces vytváření dokumentů/zobrazení](../mfc/document-templates-and-the-document-view-creation-process.md)<br/>
[Vytváření šablon dokumentů](../mfc/document-template-creation.md)<br/>
[Vytváření dokumentů/zobrazení](../mfc/document-view-creation.md)<br/>
[Vytváření nových dokumentů, oken a zobrazení](../mfc/creating-new-documents-windows-and-views.md)
