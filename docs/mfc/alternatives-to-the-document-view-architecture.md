---
title: "Alternativy k architektuře dokument zobrazení | Microsoft Docs"
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
- documents [MFC], applications without
- CDocument class [MFC], space requirements
- views [MFC], applications without
ms.assetid: 2c22f352-a137-45ce-9971-c142173496fb
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 459383474c9ffed9a7ad6cefe01ea21626cb23b1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="alternatives-to-the-documentview-architecture"></a>Alternativy k architektuře dokument/zobrazení
Document/view – Architektura aplikace MFC normálně používat ke správě informací, formáty souborů a vizuální znázornění dat uživatelům. Pro většinu aplikací klasické pracovní plochy architektuře dokument/zobrazení je vhodné a efektivní aplikace architekturu. Tato architektura odděluje data ze zobrazení a ve většině případů, zjednodušuje vaší aplikace a snižuje redundantní kódu.  
  
 Document/view – architektura však není vhodná pro některé situace. Vezměte v úvahu tyto příklady:  
  
-   Pokud provádíte přenos aplikace napsané v C pro systém Windows, můžete chtít dokončit portů před přidáním document/view – podpora do vaší aplikace.  
  
-   Pokud píšete lightweight nástroj, můžete zjistit, že můžete provádět bez architektuře dokument/zobrazení.  
  
-   Pokud původní kód již zkombinuje Správa dat s daty zobrazení, přesunutí kód, který model dokumentů/zobrazení není vhodné úsilí vzhledem k tomu, že je třeba je oddělit dva. Dáváte přednost nechte kód, jak je.  
  
 Chcete-li vytvořit aplikaci, která nepoužívá architektuře dokument/zobrazení, zrušte **Document/View – architektura podporu** políčko v kroku 1 Průvodce aplikací MFC. V tématu [Průvodce aplikací knihovny MFC](../mfc/reference/mfc-application-wizard.md) podrobnosti.  
  
> [!NOTE]
>  Aplikace založené na dialogové okno, které byly vytvořené průvodcem aplikací MFC nepoužívejte architektuře dokument/zobrazení proto **Document/View – architektura podporu** políčko vypnutá, pokud vyberete typ aplikace dialogové okno.  
  
 Průvodci Visual C++, stejně jako zdroj a dialogové okno editory, pracovat s generovaný aplikací, stejně jako všechny ostatní aplikace generované v průvodci. Aplikace může podporovat panely nástrojů, posuvníky a stavového řádku a má **o** pole. Aplikace se neregistruje žádné šablony dokumentů a nebude obsahovat dokumentové třídy.  
  
 Všimněte si, že generovaný aplikace obsahuje třídu, zobrazení, **CChildView**, odvozené z `CWnd`. MFC vytvoří a umisťuje jednu instanci třídy zobrazení v rámci okna s rámečkem vytvořené aplikace. MFC stále vynucuje pomocí okna zobrazení, protože ho zjednodušuje umístění a správu obsahu aplikace. Můžete přidat Malování kódu `OnPaint` členem této třídy. Váš kód měli přidat posuvníky do zobrazení, nikoli do rámečku.  
  
 Vzhledem k architektuře dokument/zobrazení poskytované MFC je zodpovědná za implementaci řadu základní funkce aplikace, jeho absenci ve vašem projektu znamená, že jste zodpovědní za implementaci důležité funkce aplikace:  
  
-   V souladu s pomocí Průvodce aplikací MFC, v nabídce pro vaše aplikace obsahuje pouze `New` a `Exit` příkazy **souboru** nabídky. ( `New` Příkaz je podporován pouze pro aplikace MDI, ne SDI aplikace bez Document/View – podpora.) Vygenerovaný nabídky prostředků nebudou podporovat jenom seznam naposledy použitých (naposledy použili).  
  
-   Musíte přidat funkce obslužných rutin a implementace pro všechny příkazy, které bude aplikace podporovat, včetně **otevřete** a **Uložit** na **souboru** nabídky. MFC kódu, který podporuje tyto funkce poskytuje normálně, ale, že podpora je úzce vázán k architektuře dokument/zobrazení.  
  
-   Panel nástrojů pro vaši aplikaci, pokud jste požádali o jeden, bude minimální.  
  
 Důrazně doporučujeme použít Průvodce aplikací MFC k vytvoření aplikace bez architektuře dokument/zobrazení, protože průvodce zaručuje správné architektury MFC. Pokud se musí vyhnout, pomocí průvodce, tady jsou však několik přístupy k obcházení architektuře dokument/zobrazení ve vašem kódu:  
  
-   Zpracování dokumentu jako nepoužívané appendage a implementovat vaše data správy kód ve třídě zobrazení jako navrhované výše. Režijní náklady pro dokument je relativně nízký. Jediný [CDocument](../mfc/reference/cdocument-class.md) objekt způsobuje malé množství režijní náklady na samostatně, plus malé nároky na **CDocument**na základní třídy, [CCmdTarget](../mfc/reference/ccmdtarget-class.md) a [ CObject](../mfc/reference/cobject-class.md). Obě tyto třídy jsou malé.  
  
     Deklarované v **CDocument**:  
  
    -   Dva `CString` objekty.  
  
    -   Tři **BOOL**s.  
  
    -   Jeden `CDocTemplate` ukazatel.  
  
    -   Jeden `CPtrList` objekt, který obsahuje seznam zobrazení dokumentu.  
  
     Kromě toho dokumentu vyžaduje množství času, vytvořit objekt dokumentu, jeho zobrazení objektů, okně s rámečkem a objekt šablony dokumentu.  
  
-   Pro dokument a zobrazit považovat postranní nepoužité řetězce. Správa dat a kreslení kódu, umístěte v okně s rámečkem místo zobrazení. Tento přístup je blíž ke programovací model jazyka C.  
  
-   Přepsání části rozhraní MFC framework, které vytvoření dokumentů a zobrazení omezit na všech jejich vytváření. Proces vytvoření dokumentu začíná volání `CWinApp::AddDocTemplate`. Odstranění tohoto volání ze třídy aplikace `InitInstance` členské funkce a místo toho vytvořte v okně s rámečkem `InitInstance` sami. Uveďte data správy kódu do vaší třídy oken s rámečkem. Proces vytváření dokumentů/zobrazení je znázorněna v [Document/View – vytvoření](../mfc/document-view-creation.md). To je další práci a vyžaduje podrobnější vysvětlení architektury, ale uvolní je zcela z nároky na dokument/zobrazení.  
  
 Článek [MFC: použití třídy databáze bez dokumentů a zobrazení](../data/mfc-using-database-classes-without-documents-and-views.md) dává konkrétnější příklady document/view – alternativy v kontextu databáze aplikací.  
  
## <a name="see-also"></a>Viz také  
 [Document/View – architektura](../mfc/document-view-architecture.md)

