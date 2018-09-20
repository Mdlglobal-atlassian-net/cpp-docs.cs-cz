---
title: Architektuře Document / View | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CView class [MFC], view architecture
- CDocument class [MFC]
- MFC, views
- views [MFC], MFC document/view model
- document objects [MFC]
- document objects [MFC], MFC document/view model
- MFC, documents
- documents [MFC], MFC document/view model
- document objects [MFC], document/view architecture
ms.assetid: 6127768a-553f-462a-b01b-a5ee6068c81e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 42c56ddea19266251bb12c06f6423c278f14bd71
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46404550"
---
# <a name="documentview-architecture"></a>Architektonický model dokument/zobrazení

Ve výchozím nastavení vytvoří Průvodce aplikací knihovny MFC kostru aplikace s třídou dokument a zobrazit třídu. MFC odděluje správy dat do těchto dvou tříd. Dokument se data ukládají a spravuje tisk dat a koordinuje aktualizace více zobrazení dat. Toto zobrazení zobrazí data a spravuje interakci uživatele s ním, včetně výběru a úpravy.

V tomto modelu objektu dokumentu MFC čte a zapisuje data do trvalého úložiště. Dokument může také poskytuje rozhraní pro data, bez ohledu na to se nachází (jako je například databáze). Objekt samostatné zobrazení spravuje zobrazení dat z generování dat v okně pro výběr uživatele a úpravy dat. Zobrazení získá zobrazit data z dokumentu a komunikuje zpět k tomuto dokumentu změny data.

Přestože můžete snadno změnit nebo ignorovat oddělení dokument/zobrazení, postupujte podle tohoto modelu ve většině případů poutavé příčin. Jedním z nejlepší je, když budete potřebovat několik zobrazení stejné dokumentu, jako jsou tabulky a zobrazení grafu. Model dokument/zobrazení umožňuje oddělit zobrazení objektu představují každé zobrazení dat při kód společné pro všechny zobrazení (jako jsou výpočetní modul) mohou být umístěné v dokumentu. Dokument také převezme úlohu aktualizaci všech zobrazení pokaždé, když se data změní.

Architekturu document/view knihovny MFC usnadňuje podporu různých zobrazení, více typů dokumentů, rozdělovače oken a další funkce cenné uživatelského rozhraní.

Části rozhraní MFC nejvíce viditelné pro uživatele a pro vás programátora, jsou dokumentů a zobrazení. Většinu práce při vývoji aplikace pomocí rozhraní přejde do vytváření dokumentů a zobrazení tříd. Tento článek řady popisuje:

- Účely dokumentů a zobrazení a jejich vzájemné interakce v rámci.

- Co musíte udělat pro jejich implementaci.

V srdci dokument/zobrazení jsou čtyři klíče třídy:

[CDocument](../mfc/reference/cdocument-class.md) (nebo [coledocument –](../mfc/reference/coledocument-class.md)) třída podporuje objekty sloužící k ukládání nebo řízení váš program data a poskytuje základní funkce pro třídy dokumentu definované programátorovi. Dokument představuje jednotku dat uživatel obvykle otevře pomocí příkazu Otevřít v nabídce Soubor a uloží pomocí příkazu Uložit v nabídce Soubor.

[CView](../mfc/reference/cview-class.md) (nebo některou z mnoha odvozených tříd) poskytuje základní funkce pro třídy programátorem definované zobrazení. Zobrazení je připojené k dokumentu a funguje jako prostředník mezi dokumentem a uživatelem: zobrazení vykreslí obrázek dokumentu na obrazovce a interpretuje jako operace prováděné na dokument vstup uživatele. Zobrazení také vykresluje obrázek náhledu tisku a tisk.

[CFrameWnd](../mfc/reference/cframewnd-class.md) (nebo některá z jeho variant) podporuje objekty, které poskytuje rámeček kolek jedno nebo více zobrazení dokumentu.

[CDocTemplate –](../mfc/reference/cdoctemplate-class.md) (nebo [csingledoctemplate –](../mfc/reference/csingledoctemplate-class.md) nebo [cmultidoctemplate –](../mfc/reference/cmultidoctemplate-class.md)) podporuje objekt, který koordinuje jeden nebo více existujících dokumentů daného typu a spravuje vytváření správné dokumentu, zobrazení a objekty oken rámce pro daný typ.

Následující obrázek ukazuje vztah mezi dokument a jeho zobrazení.

![Zobrazení je část dokumentu, který se zobrazí](../mfc/media/vc379n1.gif "vc379n1") dokumentů a zobrazení

Document/view – implementace v knihovně tříd odděluje vlastní data z jeho zobrazení a uživatel operace s daty. Všechny změny v datech se spravují pomocí třídy dokumentu. Zobrazení volání tohoto rozhraní pro přístup a aktualizovat data.

Dokumenty, jejich přidružené zobrazení a která ohraničují zobrazení oken s rámečkem vytvořené šablonou dokumentu. Šablona dokumentu je zodpovědný za vytváření a Správa všech dokumentů typu jeden dokument.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací

- [Portrét architektury dokument/zobrazení](../mfc/a-portrait-of-the-document-view-architecture.md)

- [Výhody architektury dokument/zobrazení](../mfc/advantages-of-the-document-view-architecture.md)

- [Třídy dokumentů a zobrazení vytvořené průvodcem aplikací](../mfc/document-and-view-classes-created-by-the-mfc-application-wizard.md)

- [Alternativy k architektuře dokument/zobrazení](../mfc/alternatives-to-the-document-view-architecture.md)

- [Přidání více zobrazení do jednoho dokumentu](../mfc/adding-multiple-views-to-a-single-document.md)

- [Použití dokumentů](../mfc/using-documents.md)

- [Použití zobrazení](../mfc/using-views.md)

- [Více typů dokumentů, zobrazení a oken s rámečkem](../mfc/multiple-document-types-views-and-frame-windows.md)

- [Inicializace a Uklízení dokumentů a zobrazení](../mfc/initializing-and-cleaning-up-documents-and-views.md)

- [Inicializovat vlastní dodatky k zobrazení & dokumentu třídy](../mfc/creating-new-documents-windows-and-views.md)

- [Použití databázových tříd s dokumenty a zobrazeními](../data/mfc-using-database-classes-with-documents-and-views.md)

- [Použití databázových tříd bez dokumentů a zobrazení](../data/mfc-using-database-classes-without-documents-and-views.md)

- [Ukázky](../visual-cpp-samples.md)

## <a name="see-also"></a>Viz také

[Prvky uživatelského rozhraní](../mfc/user-interface-elements-mfc.md)<br/>
[Windows](../mfc/windows.md)<br/>
[Okna s rámečkem](../mfc/frame-windows.md)<br/>
[Šablony dokumentů a proces vytváření dokumentů/zobrazení](../mfc/document-templates-and-the-document-view-creation-process.md)<br/>
[Vytváření dokumentů/zobrazení](../mfc/document-view-creation.md)<br/>
[Vytváření nových dokumentů, oken a zobrazení](../mfc/creating-new-documents-windows-and-views.md)

