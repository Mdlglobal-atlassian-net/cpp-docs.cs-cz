---
title: Více typů dokumentů, zobrazení a oken s rámečkem
ms.date: 11/19/2018
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
ms.openlocfilehash: f2948564b9008f9a89c89d58e3249b20b3dc2ffd
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80168639"
---
# <a name="multiple-document-types-views-and-frame-windows"></a>Více typů dokumentů, zobrazení a oken s rámečkem

Standardní vztah mezi dokumentem, jeho zobrazením a oknem rámce je popsán v tématu [vytváření dokumentů a zobrazení](../mfc/document-view-creation.md). Mnoho aplikací podporuje jeden typ dokumentu (ale možná několik otevřených dokumentů tohoto typu) s jedním zobrazením na dokumentu a pouze jedním oknem rámců na dokument. Některé aplikace ale můžou potřebovat změnit některé z těchto výchozích hodnot.

## <a name="what-do-you-want-to-know-more-about"></a>K čemu chcete získat další informace

- [Více typů dokumentů](#_core_multiple_document_types)

- [Více zobrazení](#_core_multiple_views)

- [Více oken s rámečkem](#_core_multiple_frame_windows)

- [Okna s rozdělovačem](#_core_splitter_windows)

##  <a name="multiple-document-types"></a><a name="_core_multiple_document_types"></a>Více typů dokumentů

Průvodce aplikací knihovny MFC vytvoří pro vás jednu třídu dokumentu. V některých případech ale možná budete muset podporovat více než jeden typ dokumentu. Vaše aplikace může například potřebovat sešit a dokument grafu. Každý typ dokumentu je reprezentován vlastní třídou dokumentu a pravděpodobně také vlastní třídou zobrazení. Když uživatel zvolí nový příkaz soubor, zobrazí se dialogové okno se seznamem podporovaných typů dokumentů. Pak vytvoří dokument typu, který uživatel zvolí. Každý typ dokumentu je spravován pomocí vlastního objektu šablony dokumentu.

Chcete-li vytvořit další třídy dokumentu, přečtěte si téma [Přidání třídy](../ide/adding-a-class-visual-cpp.md). Vyberte možnost [objektu CDocument](../mfc/reference/cdocument-class.md) jako typ třídy, která se má odvodit, a zadejte požadované informace o dokumentu. Potom implementujte data nové třídy.

Chcete-li dát rozhraní ví o vaší další třídě dokumentu, je nutné přidat druhé volání [AddDocTemplate](../mfc/reference/cwinapp-class.md#adddoctemplate) v přepsání [InitInstance](../mfc/reference/cwinapp-class.md#initinstance) třídy aplikace. Další informace naleznete v tématu [šablony dokumentů](../mfc/document-templates-and-the-document-view-creation-process.md).

##  <a name="multiple-views"></a><a name="_core_multiple_views"></a>Více zobrazení

Mnoho dokumentů vyžaduje pouze jedno zobrazení, ale je možné podporovat více než jedno zobrazení jednoho dokumentu. Aby bylo možné implementovat více zobrazení, objekt dokumentu udržuje seznam jeho zobrazení, poskytuje členské funkce pro přidávání a odebírání zobrazení a poskytuje členskou funkci [UpdateAllViews](../mfc/reference/cdocument-class.md#updateallviews) pro zajištění více zobrazení, když se změní data dokumentu.

Knihovna MFC podporuje tři společná uživatelská rozhraní vyžadující více zobrazení ve stejném dokumentu. Tyto modely:

- Zobrazit objekty stejné třídy, každé v samostatném okně rámce dokumentu MDI.

   Je možné, že budete chtít vytvořit druhé okno rámce v dokumentu. Uživatel může zvolit nový příkaz okna, aby otevřel druhý rámec se zobrazením stejného dokumentu a pak pomocí dvou rámců zobrazily různé části dokumentu současně. Rozhraní podporuje příkaz nové okno v nabídce okna pro aplikace MDI duplikováním počátečního okna rámce a zobrazení připojeného k dokumentu.

- Zobrazit objekty stejné třídy ve stejném okně rámce dokumentu.

   Rozdělovačová okna rozdělí prostor zobrazení jednoho okna dokumentu na více samostatných zobrazení dokumentu. Rozhraní vytvoří více objektů zobrazení ze stejné třídy zobrazení. Další informace najdete v tématu [rozdělená okna](#_core_splitter_windows).

- Zobrazení objektů různých tříd v jednom okně rámce.

   V tomto modelu proměnlivé okno s rozdělovačem, více zobrazení sdílí jedno okno rámce. Zobrazení jsou vytvořena z různých tříd, přičemž každé zobrazení poskytuje jiný způsob zobrazení stejného dokumentu. Například jedno zobrazení může zobrazit dokument zpracování textu v normálním režimu, zatímco v jiném zobrazení je v režimu osnovy. Rozdělovací ovládací prvek umožňuje uživateli upravit relativní velikosti zobrazení.

Následující obrázek dělený do částí a, b a c zobrazuje tři modely uživatelského rozhraní v uvedeném pořadí.

![Více&#45;uživatelských rozhraní pro zobrazení](../mfc/media/vc37a71.gif "Více&#45;uživatelských rozhraní pro zobrazení") <br/>
Uživatelská rozhraní s více zobrazeními

Rozhraní poskytuje tyto modely implementací nového příkazu okna a poskytnutím třídy [CSplitterWnd](../mfc/reference/csplitterwnd-class.md), jak je popsáno v části [rozdělení oken](#_core_splitter_windows). Můžete implementovat jiné modely, které používají jako výchozí bod. Ukázkové programy, které ilustrují různé konfigurace zobrazení, oken s rámečkem a příčky, naleznete v tématu [MFC Samples](../overview/visual-cpp-samples.md#mfc-samples).

Další informace o `UpdateAllViews`naleznete v tématu Třída [CView](../mfc/reference/cview-class.md) v *referenci MFC* a v [ukázce Klikyháky](../overview/visual-cpp-samples.md).

##  <a name="multiple-frame-windows"></a><a name="_core_multiple_frame_windows"></a>Více oken s rámečkem

Pomocí příkazu nové okno v nabídce okno pro aplikace MDI můžete vytvořit druhé okno rámce na stejném dokumentu. Další informace najdete v prvním modelu na obrázku s více zobrazeními uživatelského rozhraní.

##  <a name="splitter-windows"></a><a name="_core_splitter_windows"></a>Okna s rozdělovačem

V okně s rozdělovačem je okno nebo může být rozděleno do dvou nebo více rolovacích podoken. Rozdělovačový ovládací prvek (neboli "rozdělit pole") v rámci okna vedle posuvníků umožňuje uživateli upravit relativní velikosti podoken. Každé podokno je zobrazení stejného dokumentu. V "dynamických" rozdělovačech jsou zobrazení stejné třídy, jak je znázorněno v části b obrázku uživatelského rozhraní s více zobrazeními. V "statických" rozdělovačech mohou být zobrazení různých tříd. Rozdělená okna obou druhů jsou podporována třídou [CSplitterWnd](../mfc/reference/csplitterwnd-class.md).

Dynamické rozdělovače okna s zobrazeními stejné třídy umožňují uživateli rozdělit okno na více podoken na více podoknech a potom posouvat různá podokna, aby viděli různé části dokumentu. Uživatel může také zrušit rozdělení okna a odebrat tak další zobrazení. Příkladem je dělicí příčka přidaná do [ukázky Klikyháky](../overview/visual-cpp-samples.md) . Toto téma popisuje techniku pro vytváření dynamických rozdělovačových oken. V části b obrázku uživatelského rozhraní s více zobrazeními se zobrazuje dynamické okno s rozdělovačem.

Statické rozdělovače okna, s zobrazeními různých tříd, začínají oknem rozděleným na více podoken, z nichž každý má jiný účel. Například v editoru vizuální C++ bitmapy zobrazuje okno obrázek dvě podokna vedle sebe. V levém podokně se zobrazí obrázek velikosti rastrového obrázku. V pravém podokně se zobrazí zvětšený nebo zvětšený obrázek stejné bitmapy. Podokna jsou oddělená "dělicí příčkou", kterou může uživatel změnit, aby se změnily relativní velikosti podoken. Statické okno s rozdělovačem je znázorněno v části c grafického uživatelského rozhraní s více zobrazeními.

Další informace naleznete v tématu Class [CSplitterWnd](../mfc/reference/csplitterwnd-class.md) in *MFC Reference* a [MFC Samples](../overview/visual-cpp-samples.md#mfc-samples).

## <a name="see-also"></a>Viz také

[Architektura dokumentu/zobrazení](../mfc/document-view-architecture.md)
