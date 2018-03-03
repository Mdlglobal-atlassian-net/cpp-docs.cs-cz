---
title: "Architektura zobrazení dokumentů | Microsoft Docs"
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 45c595b78b17ed00691533369ec4837345fcce03
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="documentview-architecture"></a>Architektonický model dokument/zobrazení
Ve výchozím nastavení vytvoří Průvodce aplikací MFC kostru aplikace s dokumentové třídy a třídy zobrazení. MFC odděluje Správa dat do těchto dvou tříd. Dokument ukládá data a spravuje tisk data a koordinuje aktualizace dat více zobrazení. Zobrazení zobrazí data a spravuje interakci s uživatelem s ním, včetně výběru a úpravy.  
  
 V tomto modelu objektu dokumentu MFC čte a zapisuje data do trvalého úložiště. Dokument může také poskytuje rozhraní pro data, kde se nachází (například jako v databázi). Objekt samostatné zobrazení spravuje zobrazení dat z čtení dat v okně pro výběr uživatele a úpravy dat. Zobrazení získá zobrazí data z dokumentu a komunikuje zpět do dokumentu změny data.  
  
 Sice možné snadno přepsat nebo ignorovat document/view – oddělení, existují pádných důvodů, proč postupujte podle tohoto modelu ve většině případů. Jedním z nejlepší je, pokud potřebujete více zobrazení stejného dokumentu, jako jsou tabulky a zobrazení grafu. Model dokumentů/zobrazení umožňuje objekt samostatné zobrazení představují jednotlivých zobrazení dat, při běžné kódu ke všem zobrazení (jako je například modul výpočtu) může být umístěn v dokumentu. Dokument také převezme úlohy aktualizaci všech zobrazení vždy, když se mění data.  
  
 Document/view – architektura MFC usnadňuje podporu více zobrazení, více typů dokumentů, rozdělovače oken a další funkce cenné uživatelského rozhraní.  
  
 Části rozhraní MFC framework nejvíce viditelné pro uživatele a pro vás, programátory, jsou dokumentů a zobrazení. Většinu práce při vývoji aplikace pomocí rozhraní přejde do zápis třídy dokumentů a zobrazení. Rodina Tento článek popisuje:  
  
-   Účely dokumentů a zobrazení a způsob, jakým interagují v rozhraní framework.  
  
-   Co je potřeba udělat pro jejich implementaci.  
  
 Jádrem document/view – jsou čtyři klíče třídy:  
  
 [CDocument](../mfc/reference/cdocument-class.md) (nebo [COleDocument](../mfc/reference/coledocument-class.md)) třída podporuje objekty použité k uložení nebo řízení vašeho programu data a poskytuje základní funkce pro třídy programátorem definované dokumentů. Dokument představuje jednotku data, která uživatel obvykle otevře pomocí příkazu Otevřít v nabídce Soubor a uloží pomocí příkazu Uložit v nabídce Soubor.  
  
 [CView](../mfc/reference/cview-class.md) (nebo jedna z jeho mnoho odvozených tříd) poskytuje základní funkce pro třídy programátorem definované zobrazení. Zobrazení je připojena k dokumentu a funguje jako zprostředkovatel mezi dokumentu a uživatel: zobrazení vykreslí obrázek dokumentu na obrazovce a interpretuje jako operations při dokumentu vstup uživatele. Zobrazení vykreslí také bitovou kopii pro tisku a tiskového náhledu.  
  
 [CFrameWnd](../mfc/reference/cframewnd-class.md) (nebo jeden z jeho variant) podporuje objekty, které poskytuje rámečku kolem jedno nebo více zobrazení dokumentu.  
  
 [CDocTemplate](../mfc/reference/cdoctemplate-class.md) (nebo [CSingleDocTemplate](../mfc/reference/csingledoctemplate-class.md) nebo [CMultiDocTemplate](../mfc/reference/cmultidoctemplate-class.md)) podporuje objekt, který koordinuje jeden nebo více existujících dokumentů daného typu a spravuje vytváření správný dokumentu, zobrazení a rámečku objekty oken pro tento typ.  
  
 Následující obrázek znázorňuje vztahy mezi dokumentu a jeho zobrazení.  
  
 ![Zobrazení je součástí dokumentu, který se zobrazí](../mfc/media/vc379n1.gif "vc379n1")  
Zobrazení a dokumentů  
  
 Document/view – implementace v knihovně tříd odděluje samotná data z jeho zobrazení a uživatel operace s daty. Všechny změny dat jsou spravované prostřednictvím třídy dokumentu. Zobrazení volá toto rozhraní pro přístup k a aktualizovat data.  
  
 Dokumenty, jejich přidružené zobrazení a které rámce zobrazení okna s rámečkem vytvořené šablony dokumentu. Šablona dokumentu je zodpovědná za vytváření a správa všechny dokumenty typu jeden dokument.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o  
  
-   [Portrét architektury dokument/zobrazení](../mfc/a-portrait-of-the-document-view-architecture.md)  
  
-   [Výhody architektury dokument/zobrazení](../mfc/advantages-of-the-document-view-architecture.md)  
  
-   [Třídy dokumentů a zobrazení vytvořené průvodcem aplikací](../mfc/document-and-view-classes-created-by-the-mfc-application-wizard.md)  
  
-   [Alternativy k architektuře dokument/zobrazení](../mfc/alternatives-to-the-document-view-architecture.md)  
  
-   [Přidání více zobrazení do jednoho dokumentu](../mfc/adding-multiple-views-to-a-single-document.md)  
  
-   [Použití dokumentů](../mfc/using-documents.md)  
  
-   [Použití zobrazení](../mfc/using-views.md)  
  
-   [Více typů dokumentů, zobrazení a oken s rámečkem](../mfc/multiple-document-types-views-and-frame-windows.md)  
  
-   [Inicializace a Uklízení dokumentů a zobrazení](../mfc/initializing-and-cleaning-up-documents-and-views.md)  
  
-   [Inicializace vlastní doplňky třídy dokumentů a zobrazení](../mfc/creating-new-documents-windows-and-views.md)  
  
-   [Použití databázových tříd s dokumenty a zobrazeními](../data/mfc-using-database-classes-with-documents-and-views.md)  
  
-   [Použití databázových tříd bez objektů Document a zobrazení](../data/mfc-using-database-classes-without-documents-and-views.md)  
  
-   [Ukázky](../visual-cpp-samples.md)  
  
## <a name="see-also"></a>Viz také  
 [Prvky uživatelského rozhraní](../mfc/user-interface-elements-mfc.md)   
 [Windows](../mfc/windows.md)   
 [Okna s rámečkem](../mfc/frame-windows.md)   
 [Šablony dokumentů a proces vytváření dokumentů/zobrazení](../mfc/document-templates-and-the-document-view-creation-process.md)   
 [Vytváření dokumentů/zobrazení](../mfc/document-view-creation.md)   
 [Vytváření nových dokumentů, oken a zobrazení](../mfc/creating-new-documents-windows-and-views.md)

