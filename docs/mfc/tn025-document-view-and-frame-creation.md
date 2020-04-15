---
title: 'TN025: Vytvoření dokumentu, zobrazení a rámečku'
ms.date: 11/04/2016
f1_keywords:
- vc.creation
helpviewer_keywords:
- documents [MFC], view and frame creation
- TN025
ms.assetid: 09254d72-6e1d-43db-80e9-693887dbeda2
ms.openlocfilehash: 2fdabdcb1a87d4a5661348588d49303290c966ce
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370373"
---
# <a name="tn025-document-view-and-frame-creation"></a>TN025: Vytvoření dokumentu, zobrazení a rámečku

> [!NOTE]
> Následující technická poznámka nebyla aktualizována od doby, kdy byla poprvé zahrnuta do online dokumentace. V důsledku toho mohou být některé postupy a témata zastaralé nebo nesprávné. Chcete-li získat nejnovější informace, doporučujeme vyhledat téma zájmu v online indexu dokumentace.

Tato poznámka popisuje problémy s vytvářením a vlastnictvím winapps, doctemplates, dokumentů, rámců a zobrazení.

## <a name="winapp"></a>Aplikace WinApp

V systému je jeden `CWinApp` objekt.

Je staticky konstruován a inicializován `WinMain`vnitřní implementací rozhraní . Musíte odvodit z `CWinApp` dělat něco užitečného (výjimka: `CWinApp` Knihovny DLL rozšíření `DllMain` knihovny MFC by neměly mít instanci – inicializace se provádí v místo).

Jeden `CWinApp` objekt vlastní seznam šablon dokumentů (a). `CPtrList` V jedné aplikaci je jedna nebo více šablon dokumentu. DocTemplates jsou obvykle načteny ze souboru prostředků (tj. pole řetězců) v . `CWinApp::InitInstance`

```
pTemplate = new CDocTemplate(IDR_MYDOCUMENT, ...);

AddDocTemplate(pTemplate);
```

Jeden `CWinApp` objekt vlastní všechna okna rámce v aplikaci. Okno hlavního rámce pro aplikaci `CWinApp::m_pMainWnd`by mělo být uloženo v ; obvykle nastavíte `InitInstance` *m_pMainWnd* v implementaci, pokud jste nedovolili AppWizard to za vás. Pro rozhraní s jedním dokumentem (SDI) je to okno, `CFrameWnd` které slouží jako okno hlavního rámce aplikace a také jako jediné okno rámce dokumentu. Pro více rozhraní dokumentu (MDI) se jedná o `CMDIFrameWnd`MDI-Frame (třída), který slouží `CFrameWnd`jako okno hlavního rámce aplikace, které obsahuje všechny podřízené s. Každé podřízené okno `CMDIChildWnd` je třídy (odvozené z) `CFrameWnd`a slouží jako jedno z potenciálně mnoha oken rámečků dokumentu.

## <a name="doctemplates"></a>DocTemplates

Je `CDocTemplate` tvůrcem a správcem dokumentů. Vlastní dokumenty, které vytvoří. Pokud vaše aplikace používá přístup založený na prostředku popsané níže, `CDocTemplate`nebude nutné odvodit z .

Pro aplikaci SDI `CSingleDocTemplate` třída sleduje jeden otevřený dokument. Pro aplikaci MDI `CMultiDocTemplate` třída uchovává seznam (a) `CPtrList`všech aktuálně otevřených dokumentů vytvořených z této šablony. `CDocTemplate::AddDocument`a `CDocTemplate::RemoveDocument` poskytují virtuální členské funkce pro přidání nebo odebrání dokumentu ze šablony. `CDocTemplate`je přítel, `CDocument` takže můžeme nastavit `CDocument::m_pDocTemplate` chráněný zpět ukazatel přejděte zpět na šablonu doc, která vytvořila dokument.

`CWinApp`zpracovává výchozí `OnFileOpen` implementaci, která se zase dotazuje na všechny šablony dokumentu. Implementace zahrnuje hledání již otevřených dokumentů a rozhodování o tom, v jakém formátu se mají nové dokumenty otevírat.

`CDocTemplate`spravuje vazbu vazby uj pro dokumenty a rámce.

`CDocTemplate`uchovává počet nepojmenovaných dokumentů.

## <a name="cdocument"></a>CDokument

A `CDocument` je ve `CDocTemplate`vlastnictví .

Dokumenty mají seznam aktuálně otevřených zobrazení `CView`(odvozených z ) `CPtrList`, které jsou prohlížet dokument (a ).

Dokumenty nevytvářejí nebo neničí zobrazení, ale jsou k sobě po vytvoření připojeny. Když je dokument uzavřen (tj. prostřednictvím souboru nebo zavření), budou uzavřeny všechny připojené pohledy. Při zavření posledního zobrazení dokumentu (tj. okna/zavření) bude dokument uzavřen.

Rozhraní `CDocument::AddView` `RemoveView` , slouží k udržování seznamu zobrazení. `CDocument`je přítel, `CView` takže můžeme `CView::m_pDocument` nastavit zadní ukazatel.

## <a name="cframewnd"></a>CFrameWnd

A `CFrameWnd` (také známý jako snímek) hraje stejnou roli jako v `CFrameWnd` knihovně MFC 1.0, ale nyní je třída navržena pro použití v mnoha případech bez odvození nové třídy. Odvozené `CMDIFrameWnd` třídy `CMDIChildWnd` a jsou také rozšířené tolik standardní příkazy jsou již implementovány.

Je `CFrameWnd` zodpovědný za vytváření oken v klientské oblasti rámce. Za normálních okolností je jedno hlavní okno vyplňující klientskou oblast rámu.

Pro okno MDI-Frame je klientská oblast vyplněna ovládacím prvkem MDICLIENT, který je zase nadřazenou částí všech oken rámce MDI-Child. Pro okno SDI-Frame nebo okno rámce MDI-Child je klientská `CView`oblast obvykle vyplněna objektem okna -derived. V případě `CSplitterWnd`, klientská oblast zobrazení je `CSplitterWnd` vyplněna objektem `CView`okna a odvozené objekty okna (jeden na `CSplitterWnd`dílčí podokno) jsou vytvořeny jako podřízená okna .

## <a name="see-also"></a>Viz také

[Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)<br/>
[Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)
