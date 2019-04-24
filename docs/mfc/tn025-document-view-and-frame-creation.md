---
title: 'TN025: Dokumentu, zobrazení a vytváření snímků'
ms.date: 11/04/2016
f1_keywords:
- vc.creation
helpviewer_keywords:
- documents [MFC], view and frame creation
- TN025
ms.assetid: 09254d72-6e1d-43db-80e9-693887dbeda2
ms.openlocfilehash: 4958e7c4ca2c3cf9eed6420d72d0399fa112098d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62305993"
---
# <a name="tn025-document-view-and-frame-creation"></a>TN025: Dokumentu, zobrazení a vytváření snímků

> [!NOTE]
>  Následující Technická poznámka nebyla aktualizována, protože byla poprvé zahrnuta v online dokumentaci. V důsledku toho některé postupy a témata mohou být nesprávné nebo zastaralé. Nejnovější informace se doporučuje vyhledat téma zájmu v dokumentaci online index.

Tato poznámka popisuje problémy s vytvořením a vlastnictví pro WinApps, DocTemplates, dokumentů, snímky a zobrazení.

## <a name="winapp"></a>WinApp

Existuje jedna `CWinApp` objektu v systému.

Je staticky vytvořen a inicializován pomocí vnitřní implementace rozhraní framework `WinMain`. Musí být odvozen od `CWinApp` k dělat něco užitečného (výjimka: MFC – rozšiřující knihovny DLL by neměl mít `CWinApp` instance – inicializace se provádí v `DllMain` místo).

Ten `CWinApp` objektu vlastní seznam šablon dokumentů ( `CPtrList`). Existuje jeden nebo více šablonu dokumentu na aplikaci. DocTemplates jsou obvykle načtena ze souboru prostředků (to znamená, že pole řetězců) v `CWinApp::InitInstance`.

```
pTemplate = new CDocTemplate(IDR_MYDOCUMENT, ...);

AddDocTemplate(pTemplate);
```

Ten `CWinApp` objekt je vlastníkem všech oken s rámečkem v aplikaci. Hlavní okno rámce aplikace by měla být uložena v `CWinApp::m_pMainWnd`; obvykle nastavené *m_pMainWnd* v `InitInstance` implementace, pokud ještě necháte AppWizard udělal za vás. Pro rozhraní jednoho dokumentu (SDI). to je jedna `CFrameWnd` , který slouží jako hlavního rámce okna aplikace, stejně jako pouze okna rámce dokumentu. Pro rozhraní více dokumentů (MDI). to je rámce MDI (třída `CMDIFrameWnd`), který slouží jako hlavního rámce okna aplikace, která obsahuje všechny podřízené `CFrameWnd`s. Každé podřízené okno je třídy `CMDIChildWnd` (odvozený od `CFrameWnd`) a slouží jako jeden z potenciálně mnoha oken s rámečkem v dokumentu.

## <a name="doctemplates"></a>DocTemplates

`CDocTemplate` Je tvůrce a správce dokumentů. Vlastní dokumenty, které vytvoří. Pokud vaše aplikace používá přístup podle prostředků je popsáno níže, nebude nutné odvozovat z `CDocTemplate`.

Pro třídu v aplikaci SDI `CSingleDocTemplate` uchovává informace o jeden dokument otevřít. Pro aplikace MDI, třída `CMultiDocTemplate` udržuje seznam ( `CPtrList`) všechny aktuálně otevřené dokumenty vytvořené z této šablony. `CDocTemplate::AddDocument` a `CDocTemplate::RemoveDocument` poskytují virtuální členské funkce při přidání nebo odebrání ze šablony dokumentu. `CDocTemplate` je přátelská `CDocument` tak můžete nastavíme chráněný `CDocument::m_pDocTemplate` zpětný ukazatel na přejděte zpět na šablonu dokumentu, který vytvořil dokument.

`CWinApp` zpracovává výchozí `OnFileOpen` implementaci, což bude zase dotaz na všechny šablony dokumentu. Implementace zahrnuje hledají už otevřené dokumenty a rozhodování o tom, co chcete-li otevřít nové dokumenty v formátování.

`CDocTemplate` spravuje vazbu uživatelského rozhraní pro dokumenty a snímků.

`CDocTemplate` sleduje počet nepojmenované dokumenty.

## <a name="cdocument"></a>CDocument

A `CDocument` vlastní `CDocTemplate`.

Dokumenty k dispozici seznam aktuálně otevřít zobrazení (odvozený od `CView`), který se zobrazuje dokument ( `CPtrList`).

Dokumenty není vytvoření/odstranění zobrazení, ale jsou připojené k sobě navzájem po jejich vytvoření. Při zavření dokumentu (to znamená, až soubor/zavřít), všechny připojené zobrazení se zavře. Při zavření posledního zobrazení dokumentu (to znamená, okno nebo pravá) dokumentu se zavře.

`CDocument::AddView`, `RemoveView` Rozhraní umožňuje udržovat seznam zobrazení. `CDocument` je přátelská `CView` tak jsme můžete nastavit `CView::m_pDocument` zpětný ukazatel.

## <a name="cframewnd"></a>CFrameWnd

A `CFrameWnd` (také označované jako rámce) hraje roli stejné jako v MFC 1.0, ale nyní `CFrameWnd` třídy je určen pro použití v mnoha případech bez odvození nové třídy. Odvozené třídy `CMDIFrameWnd` a `CMDIChildWnd` jsou taky vylepšené tak, aby se již implementují mnoho standardních příkazů.

`CFrameWnd` Je zodpovědný za vytváření oken v klientské oblasti rámce. Obvykle je jeden hlavní okno vyplnění klientské oblasti rámce.

Pro oknem rámce MDI klientské oblasti je vyplněna MDICLIENT ovládacího prvku, které se pak nadřazené všechna okna rámce MDI – podřízená. Pro oknem rámce SDI nebo oknem rámce MDI – podřízená je klientské oblasti obvykle vyplněna `CView`-odvozené objekt okna. V případě třídy `CSplitterWnd`, je vyplněna klientské oblasti zobrazení `CSplitterWnd` objekt okna a `CView`-okno odvozené objekty (jeden na podokno) jsou vytvořeny jako podřízeného okna `CSplitterWnd`.

## <a name="see-also"></a>Viz také:

[Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)<br/>
[Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)
