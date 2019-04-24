---
title: 'Postupy: Implementace sledování v kódu'
ms.date: 11/04/2016
helpviewer_keywords:
- CRectTracker class [MFC], implementing trackers
ms.assetid: baaeca2c-5114-485f-bf58-8807db1bc973
ms.openlocfilehash: 0f037480e83b8ca1ba12af56904afe25a33e4d6c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62160299"
---
# <a name="how-to-implement-tracking-in-your-code"></a>Postupy: Implementace sledování v kódu

Ke sledování položky OLE, musí zpracovat určité události související s položkou, například klepnutím na příslušnou položku nebo aktualizuje zobrazení dokumentu. Ve všech případech stačí deklarovat dočasný [crecttracker –](../mfc/reference/crecttracker-class.md) objektu a manipulaci s položkou prostřednictvím tohoto objektu.

Když uživatel vybere položku nebo vloží objekt pomocí příkazu nabídky, je třeba inicializovat sledování správné styly představující stav položky OLE. Následující tabulka popisuje konvencích použitých v příkladu OCLIENT. Další informace o těchto stylů, najdete v části `CRectTracker`.

### <a name="container-styles-and-states-of-the-ole-item"></a>Styly kontejneru a stavy položky OLE.

|Styl zobrazení|Stav položky OLE.|
|---------------------|-----------------------|
|Tečkované ohraničení|Propojené položky|
|Pevné ohraničení|Položka je vložen do dokumentu|
|Úchyty pro změnu velikosti|Aktuálně vybraná položka|
|Šrafované ohraničení|Položka je aktuálně místě aktivní.|
|Šrafování vzor překrytí položky|Položky serveru je otevřený|

Tato inicializace snadno pomocí procedury, která kontroluje stav položky OLE a nastaví odpovídající styly dokáže zpracovat. `SetupTracker` Funkce najít v ukázce OCLIENT ukazuje sledování inicializace. Parametry pro tuto funkci jsou adresy sledovací modul, *pTracker*; ukazatel na položku klienta týkající se sledování, *pItem*; a ukazatel na obdélník, *pTrueRect* . Kompletní příklad této funkce najdete v ukázce MFC OLE [OCLIENT](../overview/visual-cpp-samples.md).

**SetupTracker** příklad kódu představuje jedinou funkci; řádky jsou proložená diskuzi o funkce funkce:

[!code-cpp[NVC_MFCOClient#1](../mfc/codesnippet/cpp/how-to-implement-tracking-in-your-code_1.cpp)]

Sledovacímu modulu je inicializován pomocí nastavení minimální velikosti a Vymazat styl sledovacímu modulu.

[!code-cpp[NVC_MFCOClient#2](../mfc/codesnippet/cpp/how-to-implement-tracking-in-your-code_2.cpp)]

Následující řádky zkontrolujte, zda je aktuálně vybrána položka a určuje, zda je položka propojené v dokumentu nebo vložené v ní. Úchyty pro změnu velikosti umístěný uvnitř ohraničení se přidají do styl označující, že je aktuálně vybrána položka. Pokud položka je propojený s váš dokument zobrazil, je použít styl ohraničení tečkovaná. Pevné ohraničení se používá, pokud položka vložena.

[!code-cpp[NVC_MFCOClient#3](../mfc/codesnippet/cpp/how-to-implement-tracking-in-your-code_3.cpp)]

Otevřete položky s šrafované vzor, pokud položka je aktuálně následující kód překrytí.

[!code-cpp[NVC_MFCOClient#4](../mfc/codesnippet/cpp/how-to-implement-tracking-in-your-code_4.cpp)]

Potom můžete zavolat tuto funkci vždy, když má sledovacímu modulu, který se má zobrazit. Například voláním této funkce z `OnDraw` funkce třídy zobrazení. Tím se aktualizuje sledování vzhled pokaždé, když je zobrazení překreslit. Úplný příklad, najdete v článku `CMainView::OnDraw` funkce ukázky MFC OLE [OCLIENT](../overview/visual-cpp-samples.md).

Ve vaší aplikaci dojde k události, které vyžadují sledování kódu, jako je zjištění změny velikosti, přesunutí nebo přístupů. Tato akce obvykle naznačují, že je Probíhá pokus o zkopírovat nebo přesunout položku. V těchto případech je potřeba rozhodnout, co byl obstaral: úchyt pro změnu velikosti nebo část ohraničení mezi úchyty pro změnu velikosti. `OnLButtonDown` Obslužná rutina zprávy je vhodné místo pro test polohu myši ve vztahu k položce. Volání `CRectTracker::HitTest`. Pokud se test vrátí něco kromě `CRectTracker::hitOutside`, položka je právě velikost nebo přesunout. Proto by měl provést volání `Track` členskou funkci. Zobrazit `CMainView::OnLButtonDown` najít funkci v ukázce MFC OLE [OCLIENT](../overview/visual-cpp-samples.md) kompletní příklad.

`CRectTracker` Třída poskytuje několik různých kurzor tvary, které slouží k určení, zda přesunutí, změna velikosti nebo přetáhněte operace probíhá. Pro zpracování této události, zkontrolujte, zda je vybrána položka aktuálně pod myší. Pokud se jedná, volají `CRectTracker::SetCursor`, nebo volat výchozí obslužnou rutinu. Následující příklad je z ukázky MFC OLE [OCLIENT](../overview/visual-cpp-samples.md):

[!code-cpp[NVC_MFCOClient#5](../mfc/codesnippet/cpp/how-to-implement-tracking-in-your-code_5.cpp)]

## <a name="see-also"></a>Viz také:

[Snímače: Implementace snímačů ve vašich aplikacích OLE](../mfc/trackers-implementing-trackers-in-your-ole-application.md)
