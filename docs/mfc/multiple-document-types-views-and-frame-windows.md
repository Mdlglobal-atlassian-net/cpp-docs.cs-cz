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
ms.openlocfilehash: 5d8cec0a4ba1580e7ac5fb0e3b81052de08223fc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370723"
---
# <a name="multiple-document-types-views-and-frame-windows"></a>Více typů dokumentů, zobrazení a oken s rámečkem

Standardní vztah mezi dokumentem, jeho zobrazením a oknem rámce je popsán v [dokumentu/vytvoření zobrazení](../mfc/document-view-creation.md). Mnoho aplikací podporuje jeden typ dokumentu (ale možná více otevřených dokumentů tohoto typu) s jedním zobrazením v dokumentu a pouze jedním oknem rámce na dokument. Některé aplikace však možná budou muset změnit jeden nebo více těchto výchozích hodnot.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o

- [Více typů dokumentů](#_core_multiple_document_types)

- [Více zobrazení](#_core_multiple_views)

- [Více oken rámečků](#_core_multiple_frame_windows)

- [Okna rozdělovače](#_core_splitter_windows)

## <a name="multiple-document-types"></a><a name="_core_multiple_document_types"></a>Více typů dokumentů

Průvodce aplikací knihovny MFC vytvoří pro vás jednu třídu dokumentu. V některých případech však může být nutné podporovat více než jeden typ dokumentu. Aplikace může například potřebovat list a dokumenty grafu. Každý typ dokumentu je reprezentován vlastní třídou dokumentu a pravděpodobně také vlastní třídou zobrazení. Když uživatel zvolí příkaz Nový soubor, rozhraní se zobrazí dialogové okno se seznamem podporovaných typů dokumentů. Potom vytvoří dokument typu, který uživatel zvolí. Každý typ dokumentu je spravován vlastním objektem šablony dokumentu.

Další třídy dokumentů najdete v [tématu Přidání třídy](../ide/adding-a-class-visual-cpp.md). Zvolte [CDocument](../mfc/reference/cdocument-class.md) jako typ třídy, ze které chcete odvodit a zadejte požadované informace o dokumentu. Pak implementujte data nové třídy.

Chcete-li, aby rozhraní bylo uvedeno v rámci o vaší třídě dokumentu, je nutné přidat druhé volání do [addDocTemplate](../mfc/reference/cwinapp-class.md#adddoctemplate) v přepsání [InitInstance](../mfc/reference/cwinapp-class.md#initinstance) vaší třídy aplikace. Další informace naleznete v [tématu Document Templates](../mfc/document-templates-and-the-document-view-creation-process.md).

## <a name="multiple-views"></a><a name="_core_multiple_views"></a>Více zobrazení

Mnoho dokumentů vyžaduje pouze jedno zobrazení, ale je možné podporovat více než jedno zobrazení jednoho dokumentu. Chcete-li implementovat více zobrazení, objekt dokumentu uchovává seznam jeho zobrazení, poskytuje členské funkce pro přidávání a odebírání zobrazení a poskytuje [updateallviews](../mfc/reference/cdocument-class.md#updateallviews) členské funkce pro umožnění více zobrazení vědět, kdy se změnila data dokumentu.

Knihovna MFC podporuje tři běžná uživatelská rozhraní, která vyžadují více zobrazení ve stejném dokumentu. Jedná se o tyto modely:

- Zobrazení objektů stejné třídy, každý v samostatném okně rámce dokumentu MDI.

   Můžete chtít podporovat vytváření druhého okna rámce v dokumentu. Uživatel může zvolit příkaz Nové okno, který otevře druhý snímek se zobrazením stejného dokumentu a potom pomocí dvou snímků zobrazí různé části dokumentu současně. Rozhraní Framework podporuje příkaz Nové okno v nabídce Window pro aplikace MDI duplikováním okna počátečního rámce a zobrazení připojeného k dokumentu.

- Zobrazení objektů stejné třídy ve stejném okně rámce dokumentu.

   Rozdělovač oken rozdělí prostor zobrazení jednoho okna dokumentu do více samostatných zobrazení dokumentu. Rozhraní framework vytvoří více objektů zobrazení ze stejné třídy zobrazení. Další informace naleznete v tématu [Splitter Windows](#_core_splitter_windows).

- Zobrazení objektů různých tříd v okně jednoho snímku.

   V tomto modelu, varianta okna rozdělovače, více pohledů sdílet jedno okno rámce. Zobrazení jsou vytvořena z různých tříd, z nichž každé zobrazení poskytuje jiný způsob zobrazení stejného dokumentu. Jedno zobrazení může například zobrazit textový dokument v normálním režimu, zatímco druhé zobrazení jej zobrazuje v režimu osnovy. Ovládací prvek rozdělovač eviduje uživateli relativní velikosti zobrazení.

Následující obrázek, rozdělený do částí a, b a c, zobrazuje tři modely uživatelského rozhraní ve výše uvedeném pořadí.

![Více&#45;zobrazení uživatelských rozhraní](../mfc/media/vc37a71.gif "Více&#45;zobrazení uživatelských rozhraní") <br/>
Vícenásobná uživatelská rozhraní

Rámec poskytuje tyto modely implementací příkazu New Window a poskytnutím třídy [CSplitterWnd](../mfc/reference/csplitterwnd-class.md), jak je popsáno v [systému Splitter Windows](#_core_splitter_windows). Můžete implementovat jiné modely pomocí těchto jako výchozí bod. Ukázkové programy, které ilustrují různé konfigurace zobrazení, oken rámců a rozdělovačů, naleznete [v tématu Ukázky knihovny MFC](../overview/visual-cpp-samples.md#mfc-samples).

Další informace `UpdateAllViews`o , naleznete v části [CView](../mfc/reference/cview-class.md) třídy v *referenční příručce knihovny MFC* a [ukázce klikacích](../overview/visual-cpp-samples.md).

## <a name="multiple-frame-windows"></a><a name="_core_multiple_frame_windows"></a>Windows s více rámy

Pomocí příkazu Nové okno v nabídce Okno pro aplikace MDI můžete vytvořit druhé okno rámce ve stejném dokumentu. Další informace naleznete v prvním modelu na obrázku Vícezobrazení uživatelské rozhraní.

## <a name="splitter-windows"></a><a name="_core_splitter_windows"></a>Splitter Windows

V okně rozdělovače je nebo může být rozděleno do dvou nebo více posuvných podoken. Ovládací prvek rozdělovače (nebo "rozdělovací rámeček") v rámečku okna vedle posuvníků umožňuje uživateli upravit relativní velikosti podoken. Každé podokno je zobrazení ve stejném dokumentu. V "dynamické" rozdělovače pohledy jsou stejné třídy, jak je znázorněno v části b obrázku více zobrazení uživatelského rozhraní. V "statické" rozdělovače zobrazení mohou být různých tříd. Splitter okna obou druhů jsou podporovány třídou [CSplitterWnd](../mfc/reference/csplitterwnd-class.md).

Dynamická okna rozdělovače se zobrazeními stejné třídy umožňují uživateli rozdělit okno do více podoken podle potřeby a potom posouvat různá podokna, aby viděli různé části dokumentu. Uživatel může také zrušit rozdělení okna odebrat další zobrazení. Příkladem jsou okna rozdělovače přidaná do [ukázky klikyháky.](../overview/visual-cpp-samples.md) Toto téma popisuje techniku pro vytváření dynamických dělicích oken. Dynamické okno rozdělovače je zobrazeno v části b obrázku Vícezobrazení uživatelského rozhraní.

Statická okna rozdělovače, s zobrazenírůzných tříd, začínají s oknem rozděleným do více podoken, z nichž každý má jiný účel. Například v bitmapovém editoru Visual C++ se v okně obrázku zobrazí dvě podokna vedle sebe. V levém podokně se zobrazí obraz bitmapy v životní velikosti. Pravé podokno zobrazuje zvětšený nebo zvětšený obraz stejné bitmapy. Podokna jsou oddělena "rozdělovačem", který může uživatel přetáhnout a změnit relativní velikost i podlomena. V části c obrázku Vícezobrazení uživatelských rozhraní je zobrazeno statické okno rozdělovače.

Další informace naleznete v části Třída [CSplitterWnd](../mfc/reference/csplitterwnd-class.md) v *odkazové ms* a [vzorky knihovny MFC](../overview/visual-cpp-samples.md#mfc-samples).

## <a name="see-also"></a>Viz také

[Architektura dokumentu/zobrazení](../mfc/document-view-architecture.md)
