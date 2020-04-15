---
title: Vztahy mezi objekty MFC
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, relationships between key objects
- objects [MFC], relationships
- relationships, MFC objects
- MFC object relationships
ms.assetid: 6e8f3b51-e80f-4d88-94c8-4c1e4ee163ad
ms.openlocfilehash: d7e40e25b405d3f8ec50a518889cc2b89bc8c725
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372810"
---
# <a name="relationships-among-mfc-objects"></a>Vztahy mezi objekty MFC

Chcete-li proces vytváření dokumentu/zobrazení uvést do perspektivy, zvažte spuštěný program: dokument, okno rámce použité k zobrazení a pohled přidružený k dokumentu.

- Dokument uchovává seznam zobrazení tohoto dokumentu a ukazatel na šablonu dokumentu, která dokument vytvořila.

- Zobrazení zachová ukazatel na dokument a je podřízeným oknem nadřazeného rámečku.

- Okno rámce dokumentu zachová ukazatel na aktuální aktivní pohled.

- Šablona dokumentu uchovává seznam otevřených dokumentů.

- Aplikace uchovává seznam svých šablon dokumentů.

- Systém Windows sleduje všechna otevřená okna, takže jim může odesílat zprávy.

Tyto vztahy jsou vytvořeny během vytváření dokumentu/zobrazení. Následující tabulka ukazuje, jak mohou objekty v spuštěném programu přistupovat k jiným objektům. Libovolný objekt může získat ukazatel na objekt aplikace voláním globální funkce [AfxGetApp](../mfc/reference/application-information-and-management.md#afxgetapp).

### <a name="gaining-access-to-other-objects-in-your-application"></a>Získání přístupu k jiným objektům ve vaší aplikaci

|Z objektu|Jak získat přístup k jiným objektům|
|-----------------|---------------------------------|
|Dokument|Pomocí [GetFirstViewPosition](../mfc/reference/cdocument-class.md#getfirstviewposition) a [GetNextView](../mfc/reference/cdocument-class.md#getnextview) pro přístup k seznamu zobrazení dokumentu.<br /><br /> Volání [GetDocTemplate](../mfc/reference/cdocument-class.md#getdoctemplate) získat šablonu dokumentu.|
|Zobrazit|Volání [GetDocument](../mfc/reference/cview-class.md#getdocument) získat dokument.<br /><br /> Volání [GetParentFrame](../mfc/reference/cwnd-class.md#getparentframe) získat okno rámce.|
|Okno rámce dokumentu|Volání [GetActiveView](../mfc/reference/cframewnd-class.md#getactiveview) získat aktuální zobrazení.<br /><br /> Volání [GetActiveDocument](../mfc/reference/cframewnd-class.md#getactivedocument) získat dokument připojený k aktuálnímu zobrazení.|
|Okno rámce MDI|Volání [MDIGetActive](../mfc/reference/cmdiframewnd-class.md#mdigetactive) získat aktuálně aktivní [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md).|

Okno rámce má obvykle jedno zobrazení, ale někdy, stejně jako v rozbočovačích oken, stejné okno rámce obsahuje více zobrazení. Okno rámce zachová ukazatel na aktuálně aktivní zobrazení; ukazatel se aktualizuje při každém aktivaci jiného zobrazení.

> [!NOTE]
> Ukazatel na okno hlavního rámce je uložen v [proměnné m_pMainWnd](../mfc/reference/cwinthread-class.md#m_pmainwnd) člena aplikačního objektu. Volání `OnFileNew` v přepsání `InitInstance` členské funkce `CWinApp` sad *m_pMainWnd* pro vás. Pokud nezavoláte `OnFileNew`, musíte nastavit hodnotu `InitInstance` proměnné v sobě. (Aplikace komponenty (server) modelu SDI COM nemusí proměnnou nastavit, pokud je parametr /Embedding na příkazovém řádku.) Všimněte *m_pMainWnd* si, že m_pMainWnd `CWinThread` je `CWinApp`nyní členem třídy spíše než .

## <a name="see-also"></a>Viz také

[Šablony dokumentů a proces vytváření dokumentů/zobrazení](../mfc/document-templates-and-the-document-view-creation-process.md)<br/>
[Vytváření šablon dokumentů](../mfc/document-template-creation.md)<br/>
[Vytváření dokumentů/zobrazení](../mfc/document-view-creation.md)<br/>
[Vytváření nových dokumentů, oken a zobrazení](../mfc/creating-new-documents-windows-and-views.md)
