---
title: Více typů dokumentů, zobrazení a oken s rámečkem | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5640c3bb66bee0641b0c153ae10dc146bb1c1dd8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33352155"
---
# <a name="multiple-document-types-views-and-frame-windows"></a>Více typů dokumentů, zobrazení a oken s rámečkem
Standardní vztah mezi dokumentu, jeho zobrazení a jeho oken s rámečkem je popsán v [Document/View – vytvoření](../mfc/document-view-creation.md). Mnoho aplikací podporují jeden dokumentu typu (ale může být více otevřené dokumenty daného typu) s jedním zobrazením na dokument a pouze jeden rámec okna na dokumentu. Ale některé aplikace je nutné změnit nejméně jeden z těchto výchozí hodnoty.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o  
  
-   [Více typů dokumentů.](#_core_multiple_document_types)  
  
-   [Více zobrazení](#_core_multiple_views)  
  
-   [Více oken s rámečkem](#_core_multiple_frame_windows)  
  
-   [Rozdělovače oken](#_core_splitter_windows)  
  
##  <a name="_core_multiple_document_types"></a> Více typů dokumentů.  
 Průvodce aplikací MFC pro vás vytvoří třídu jednotlivý dokument. V některých případech ale musíte podporovat více než jeden typ dokumentu. Aplikace může například vyžadovat listu a graf dokumenty. Každý typ dokumentu je reprezentováno své vlastní třídy dokumentů a pravděpodobně vlastní zobrazení třídy. Když uživatel vybere soubor nový příkaz, rozhraní zobrazí dialogové okno s jsou uvedeny typy podporované dokumentu. Pak vytvoří dokument typu, které uživatel vybere. Každý typ dokumentu spravuje vlastní objekt šablony dokumentu.  
  
 Vytvoření třídy navíc dokumentů, naleznete v části [přidání třídy](../ide/adding-a-class-visual-cpp.md). Zvolte [CDocument](../mfc/reference/cdocument-class.md) jako typ třídy odvozovat a zadat informace požadovaný dokument. Potom implementujte novou třídu data.  
  
 Umožníte framework vědět o třídě navíc dokumentu, musíte přidat druhý volání [AddDocTemplate](../mfc/reference/cwinapp-class.md#adddoctemplate) v třídy aplikace [InitInstance](../mfc/reference/cwinapp-class.md#initinstance) přepsat. Další informace najdete v tématu [šablony dokumentů](../mfc/document-templates-and-the-document-view-creation-process.md).  
  
##  <a name="_core_multiple_views"></a> Více zobrazení  
 Mnoho dokumenty vyžadují jenom jednoho zobrazení, ale je možné podporovat více než jedno zobrazení jednotlivý dokument. Můžete implementovat více zobrazení, objekt, který dokument udržuje seznam jeho zobrazení, poskytuje členské funkce pro přidávání a odebírání zobrazení a poskytuje [UpdateAllViews](../mfc/reference/cdocument-class.md#updateallviews) – členská funkce více zobrazení vědět, kdy se kterými můžete data dokumentu se změnila.  
  
 MFC podporuje tři běžné uživatelské rozhraní nutnosti více zobrazení na stejném dokumentu. Tyto modely jsou:  
  
-   Objekty zobrazení stejné třídy, každou v samostatném okně rámce MDI dokumentu.  
  
     Můžete chtít podporují vytváření druhé okně s rámečkem v dokumentu. Uživatel může zvolit příkaz nové okno otevřít druhý snímek se zobrazením stejného dokumentu a potom pomocí dvou rámce současně zobrazit různé části dokumentu. Rozhraní framework podporuje nové okno příkazu v nabídce okno pro aplikace MDI duplikováním počáteční rámec okna a zobrazení, které jsou připojené k dokumentu.  
  
-   Objekty zobrazení stejné třídy ve stejné rámce okna dokumentu.  
  
     Rozdělovače oken rozdělte do více samostatných zobrazení dokumentu místo zobrazení okna jednotlivý dokument. Rozhraní framework vytvoří více zobrazení objektů ze stejné třídy zobrazení. Další informace najdete v tématu [rozdělovače oken](#_core_splitter_windows).  
  
-   Objekty zobrazení různých tříd v rámci jednoho okna.  
  
     V tomto modelu varianta okno rozdělovače více zobrazení sdílet jeden rámce okna. Zobrazení se vytvářejí na základě různých tříd jednotlivých zobrazení poskytuje jiný způsob, jak zobrazit stejného dokumentu. Zobrazení může například zobrazovat textového dokumentu v normálním režimu a ostatní zobrazení se zobrazí je v režimu outline. Ovládací prvek typu rozdělovač umožňuje uživateli upravit relativní velikosti zobrazení.  
  
 Na následujícím obrázku je rozdělený do částí a, b a c, ukazuje tři modely uživatelského rozhraní ve výše uvedeném pořadí.  
  
 ![Více&#45;zobrazení uživatelského rozhraní](../mfc/media/vc37a71.gif "vc37a71")  
Více zobrazení uživatelského rozhraní  
  
 Rozhraní framework poskytuje tyto modely implementací příkaz nové okno a tím, že poskytuje třídu [CSplitterWnd](../mfc/reference/csplitterwnd-class.md), jak je popsáno v [rozdělovače oken](#_core_splitter_windows). Můžete implementovat jinými modely využít jako počáteční bod. Pro ukázkové aplikace, které ilustrují různé konfigurace zobrazení okna s rámečkem a příčky, najdete v tématu [MFC ukázky](../visual-cpp-samples.md).  
  
 Další informace o `UpdateAllViews`, najdete v části třídy [CView](../mfc/reference/cview-class.md) v *odkaz knihovny MFC* a [Scribble ukázka](../visual-cpp-samples.md).  
  
##  <a name="_core_multiple_frame_windows"></a> Více oken s rámečkem  
 Příkaz nové okno v nabídce okno pro aplikace MDI slouží k vytvoření druhého okně s rámečkem na stejném dokumentu. Další informace najdete v tématu první model na obrázku více zobrazení uživatelského rozhraní.  
  
##  <a name="_core_splitter_windows"></a> Rozdělovače oken  
 V okně rozdělovače okna je nebo lze rozdělit na dvě nebo více posouvatelného podokna. Rozdělovače ovládacího prvku (nebo "rozdělit pole") v rámci okna vedle posuvníky umožňuje uživateli upravit relativní velikosti podoken. Každý podokno je zobrazení na stejném dokumentu. V "dynamická" příčky zobrazení mají stejnou třídu, jak je uvedeno v části b obrázek více zobrazení uživatelského rozhraní. V "statická" příčky může být zobrazení různých tříd. Rozdělovače oken oba typy jsou podporovány třídou [CSplitterWnd](../mfc/reference/csplitterwnd-class.md).  
  
 Dynamické rozdělovače oken, se zobrazeními stejné třídy, umožnit uživatelům rozdělení okna do několika podokny chtít a posuňte se různých podoken zobrazíte různé části dokumentu. Uživatel může také zrušit rozdělení okna odebrat další zobrazení. Rozdělovače oken, přidat do [Scribble ukázka](../visual-cpp-samples.md) jsou příklad. Toto téma popisuje postup pro vytvoření dynamické rozdělovače oken. Dynamické rozdělovače okno se zobrazí v části b obrázek více zobrazení uživatelského rozhraní.  
  
 Statické rozdělovače oken s zobrazení různých tříd, začínat okno rozdělit do několika podoken, každý s jinému účelu. Například v editoru Visual C++ rastrový obrázek bitové kopie okně zobrazí dvě podokna vedle sebe. V levém podokně se zobrazí life-sized obrázek bitové mapy. V pravém podokně zobrazí přiblížení či oddálení nebo oddálit image stejné bitmapy. Podokna jsou odděleny "rozdělovače panel", který chcete-li změnit relativní velikosti podoken můžete přetáhnout uživatele. Statické rozdělovače okno se zobrazí v části c obrázek více zobrazení uživatelského rozhraní.  
  
 Další informace najdete v tématu třídy [CSplitterWnd](../mfc/reference/csplitterwnd-class.md) v *odkaz knihovny MFC* a [MFC ukázky](../visual-cpp-samples.md).  
  
## <a name="see-also"></a>Viz také  
 [Document/View – architektura](../mfc/document-view-architecture.md)

