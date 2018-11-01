---
title: Posouvání a změna měřítka zobrazení
ms.date: 11/04/2016
helpviewer_keywords:
- message handlers [MFC]
- scaling views [MFC]
- message handling [MFC], scroll bars in view class [MFC]
- scroll bars [MFC], messages
- scrolling views [MFC]
ms.assetid: f98a3421-c336-407e-97ee-dbb2ffd76fbd
ms.openlocfilehash: acef79a89da88773da564fc965a607e2fd5b53f7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50626093"
---
# <a name="scrolling-and-scaling-views"></a>Posouvání a změna měřítka zobrazení

MFC podporuje zobrazení, která posuňte zobrazení a zobrazení, které se automaticky upraví tak velikost okna rámce, který zobrazí je. Třída `CScrollView` podporuje oba typy zobrazení.

Další informace o posouvání a změna měřítka, naleznete v tématu třídy [cscrollview –](../mfc/reference/cscrollview-class.md) v *odkaz knihovny MFC*. Posouvání příklad naleznete v tématu [ukázky Scribble](../visual-cpp-samples.md).

## <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací

- Posouvání zobrazení

- Změna měřítka zobrazení

- [Zobrazení souřadnic](/windows/desktop/gdi/window-coordinate-system)

##  <a name="_core_scrolling_a_view"></a> Posouvání zobrazení

Často velikosti dokumentu je větší než velikost, kterou můžete zobrazit jeho zobrazení. To může nastat, protože data dokumentu zvyšuje nebo uživatel zmenší okno rámce zobrazení. V takovém případě musí podporovat zobrazení posouvání.

Všechna zobrazení dokáže zpracovávat zprávy posuvníku v jeho `OnHScroll` a `OnVScroll` členské funkce. Můžete buď implementovat posuvníku zpráva zpracování těchto funkcí, stačí to sami, nebo můžete použít `CScrollView` třídy pro zpracování posouvání za vás.

`CScrollView` provede následující akce:

- Spravuje mapování režimů a velikosti oken a zobrazení

- Posune automaticky v reakci na posuvníku zprávy

Kolik můžete zadat posun "stránky" (když uživatel klikne na posuvníku šachty) a "řádek" (když uživatel klikne v posouvací šipky). Tyto hodnoty tak, aby odpovídala povahu zobrazení plánu. Můžete například chtít přejděte v přírůstcích po 1 pixelu pro grafické zobrazení, ale v přírůstcích po podle výšky řádku v textové dokumenty.

##  <a name="_core_scaling_a_view"></a> Změna měřítka zobrazení

Pokud chcete zobrazit automaticky přizpůsobit velikost okna rámce, můžete použít `CScrollView` pro škálování místo posouvání. Logické zobrazení je vyčerpávat nebo zmenšit přesně podle klientské oblasti okna. Dokončeno škálování zobrazení nemá žádné posuvníky.

## <a name="see-also"></a>Viz také

[Použití zobrazení](../mfc/using-views.md)

