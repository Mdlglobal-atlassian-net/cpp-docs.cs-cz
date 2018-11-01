---
title: Více typů dokumentů, zobrazení a oken s rámečkem
ms.date: 11/04/2016
helpviewer_keywords:
- static splitter windows [MFC]
- multiple views [MFC]
- multiple document types [MFC]
- multiple views [MFC], frame windows
- document classes [MFC], multiple
- documents [MFC], multiple types of
- splitter windows [MFC], dynamic
- dynamic splitter windows [MFC]
- windows [MFC], dynamic splitter
- windows [MFC], static splitter
- multiple frame windows [MFC]
- splitter windows [MFC], static
ms.assetid: c6b9e4e0-7c9c-45f1-a804-aeac39c9a128
ms.openlocfilehash: 3c1422aed5535d30a2f9fb79300f6093326d2ef3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50669102"
---
# <a name="multiple-document-types-views-and-frame-windows"></a>Více typů dokumentů, zobrazení a oken s rámečkem

Standardní vztah mezi dokument a jeho zobrazení a jeho okno rámce je popsán v [vytváření dokumentů/zobrazení](../mfc/document-view-creation.md). Mnoho aplikací podporují jeden dokument typ (ale může být více otevřených dokumentů daného typu) s jedním zobrazením v dokumentu a pouze jeden snímek okna dokumentu. Ale některé aplikace může potřebovat změnit jeden nebo více těchto výchozích hodnot.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací

- [Více typů dokumentů](#_core_multiple_document_types)

- [Více zobrazení](#_core_multiple_views)

- [Více oken s rámečkem](#_core_multiple_frame_windows)

- [Rozdělovače oken](#_core_splitter_windows)

##  <a name="_core_multiple_document_types"></a> Více typů dokumentů

Průvodce aplikací MFC vytvoří třídu jednoho dokumentu pro vás. V některých případech ale budete muset podporují více než jeden typ dokumentu. Vaše aplikace může například potřebovat list a graf dokumenty. Každý typ dokumentu je reprezentován třídou svůj vlastní dokument a pravděpodobně ve své vlastní zobrazení třídy. Když uživatel vybere příkaz Nový soubor, zobrazí dialogové okno, které jsou uvedeny typy podporovaných dokumentu rozhraní. Potom vytvoří dokument typu, který uživatel vybere. Každý typ dokumentu spravuje svou vlastní objekt šablony dokumentu.

Vytvoření třídy dalších dokumentů najdete v tématu [přidání třídy](../ide/adding-a-class-visual-cpp.md). Zvolte [CDocument](../mfc/reference/cdocument-class.md) jako typ třídy odvozovat a zadat informace požadované dokumentu. Pak implementujte novou třídu data.

Aby mohl framework vědět o další dokumentové třídy, je nutné přidat druhé volání [AddDocTemplate](../mfc/reference/cwinapp-class.md#adddoctemplate) ve své třídě aplikace [InitInstance](../mfc/reference/cwinapp-class.md#initinstance) přepsat. Další informace najdete v tématu [šablony dokumentů](../mfc/document-templates-and-the-document-view-creation-process.md).

##  <a name="_core_multiple_views"></a> Více zobrazení

Počet dokumentů vyžadují pouze jedno zobrazení, ale je možné pro podporu více než jedno zobrazení jednotlivý dokument. Aby vám pomohly implementovat více zobrazení, objekt dokumentu udržuje seznam své názory, poskytuje členské funkce pro přidávání a odebírání zobrazení a poskytuje [UpdateAllViews](../mfc/reference/cdocument-class.md#updateallviews) členskou funkci pro umožníte tím více zobrazení vědět, kdy dokumentu se data změnila.

MFC podporuje tři běžné uživatelské rozhraní vyžaduje více pohledy v jednom dokumentu. Tyto modely jsou:

- Zobrazit objekty stejné třídy, každou v samostatném okně rámce MDI dokumentu.

   Můžete chtít podporují vytváření druhém okně s rámečkem v dokumentu. Uživatel může zvolit příkaz nové okno k zobrazení stejný dokument otevřít na druhý snímek a potom použít dvěma snímky chcete-li zobrazit různé části dokumentu současně. Rozhraní framework podporuje nové okno příkaz v nabídce okno pro aplikace MDI tak, že duplikujete počáteční rámec okna a zobrazení, které jsou připojené k dokumentu.

- Zobrazit objekty stejné třídy ve stejném okně rámce dokumentu.

   Rozdělovače oken rozdělit do více samostatných zobrazení dokumentu místo zobrazení okna jednotlivý dokument. Rozhraní vytvoří několik zobrazení objektů ze stejné třídy zobrazení. Další informace najdete v tématu [rozdělovač Windows](#_core_splitter_windows).

- Zobrazit objekty jiné třídy v rámci jednoho okna.

   V tomto modelu varianta okna s rozdělovačem více zobrazení sdílet jeden snímek okna. Zobrazení se vytvářejí na základě různých tříd, každé zobrazení jiný způsob, jak zobrazit stejný dokument. Jedno zobrazení může například zobrazit textový dokument v normálním režimu ostatní zobrazení se zobrazí ho v režimu osnovy. Ovládací prvek splitter umožňuje uživateli upravit relativní velikosti zobrazení.

Na následujícím obrázku je rozdělena na oddíly a, b a c, ukazuje tři modely uživatelského rozhraní v uvedeném pořadí výše.

![Více&#45;uživatelské rozhraní zobrazit](../mfc/media/vc37a71.gif "vc37a71") více zobrazení uživatelského rozhraní

Rozhraní poskytuje tyto modely pomocí implementace příkazu nové okno a tím, že poskytuje třídy [CSplitterWnd](../mfc/reference/csplitterwnd-class.md), jak je popsáno v [rozdělovač Windows](#_core_splitter_windows). Můžete implementovat další modely využít jako výchozí bod. Pro ukázkové programy, které demonstrují různé konfigurace najdete v zobrazení oken s rámečkem a příčky, [ukázky knihovny MFC](../visual-cpp-samples.md).

Další informace o `UpdateAllViews`, naleznete v tématu třídy [CView](../mfc/reference/cview-class.md) v *odkaz knihovny MFC* a [ukázky Scribble](../visual-cpp-samples.md).

##  <a name="_core_multiple_frame_windows"></a> Více rámce Windows

Nové okno příkaz v nabídce okno pro aplikace MDI můžete vytvořit druhý okno rámce na stejný dokument. Další informace podívejte se na první model obrázku více zobrazení uživatelského rozhraní.

##  <a name="_core_splitter_windows"></a> Rozdělovač Windows

V okně rozdělovač v okně je nebo lze rozdělit na dvě nebo více posuvný podoken. Rozdělování ovládací prvek (nebo "rozdělit pole") v rámci okna vedle posuvníky umožňuje uživateli upravit relativní velikosti podoken. Každé podokno je zobrazení na stejný dokument. V "dynamické" příčky zobrazení mají stejné třídy, jak je uvedeno v části b obrázek více zobrazení uživatelského rozhraní. V "statických" příčky může být zobrazení různých tříd. Rozdělovače oken oba typy podporovaných třídou [CSplitterWnd](../mfc/reference/csplitterwnd-class.md).

Dynamické rozdělovače oken pomocí zobrazení stejné třídy, umožnit uživatelům rozdělení okna do několika podoken budete a posuňte různými podokny zobrazíte různých částech tohoto dokumentu. Uživatele můžete také zrušit rozdělení okna odebrat další zobrazení. Rozdělovače oken do [ukázky Scribble](../visual-cpp-samples.md) jsou příkladem. Toto téma popisuje postup pro vytvoření dynamické rozdělovače oken. Dynamické okno s rozdělovačem se zobrazí v části b obrázek více zobrazení uživatelského rozhraní.

Statické rozdělovače oken se zobrazeními z různých tříd, spusťte v okně Rozdělit do několika podoken, každý s jiným způsobem. Například v editoru rastrových obrázků Visual C++, image okno zobrazuje dvě podokna vedle sebe. V levém podokně se zobrazí life-sized obraz bitmapy. V pravém podokně se zobrazí obrázek přiblíženou nebo zvětšenou stejné rastrového obrázku. Podokna jsou odděleny "rozdělovač bar", který uživatel můžete přetáhnout do změnit tak relativní velikosti podoken. Statický rozdělovač okna se zobrazí v části c obrázek více zobrazení uživatelského rozhraní.

Další informace najdete v tématu třídy [CSplitterWnd](../mfc/reference/csplitterwnd-class.md) v *odkaz knihovny MFC* a [ukázky knihovny MFC](../visual-cpp-samples.md).

## <a name="see-also"></a>Viz také

[Document/View – architektura](../mfc/document-view-architecture.md)

