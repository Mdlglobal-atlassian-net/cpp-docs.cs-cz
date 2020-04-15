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
ms.openlocfilehash: 366f0e2953e5190f80a2877804bff2fc7dbbd520
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372792"
---
# <a name="scrolling-and-scaling-views"></a>Posouvání a změna měřítka zobrazení

Knihovna MFC podporuje zobrazení, která posouvají a zobrazení, která jsou automaticky škálována na velikost okna rámce, které je zobrazuje. Třída `CScrollView` podporuje oba druhy zobrazení.

Další informace o posouvání a změně velikosti naleznete v tématu [CScrollView](../mfc/reference/cscrollview-class.md) třídy v *odkaz knihovny MFC*. Příklad posouvání najdete v [ukázce Klikyháky](../overview/visual-cpp-samples.md).

## <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o

- Posouvání zobrazení

- Změna velikosti zobrazení

- [Zobrazit souřadnice](/windows/win32/gdi/window-coordinate-system)

## <a name="scrolling-a-view"></a><a name="_core_scrolling_a_view"></a>Posouvání zobrazení

Velikost dokumentu je často větší než velikost, kterou může zobrazit jeho zobrazení. K tomu může dojít, protože se zvýší data dokumentu nebo uživatel zmenší okno, které propojí zobrazení. V takových případech musí zobrazení podporovat posouvání.

Libovolné zobrazení může zpracovávat zprávy `OnHScroll` `OnVScroll` posuvníku ve svých a členských funkcích. Můžete buď implementovat zpracování zpráv posuvníku v těchto funkcích, `CScrollView` dělat všechnu práci sami, nebo můžete použít třídu pro zpracování posouvání za vás.

`CScrollView`provádí následující akce:

- Spravuje velikosti oken a výřezů a režimy mapování.

- Posouvá se automaticky v reakci na zprávy na posuvníku

Můžete určit, jak moc se má posunout po "stránce" (když uživatel klikne na posuvníku) a "čáru" (když uživatel klikne na šipku posuvníku). Naplánujte tyto hodnoty tak, aby vyhovovaly povaze vašeho názoru. Můžete se například posunout po krocích po 1 obrazovém bodu pro grafické zobrazení, ale v krocích na základě výšky řádku v textových dokumentech.

## <a name="scaling-a-view"></a><a name="_core_scaling_a_view"></a>Změna velikosti zobrazení

Pokud chcete, aby se zobrazení automaticky vešel do `CScrollView` velikosti okna rámečku, můžete místo posouvání použít pro změnu velikosti. Logické zobrazení je roztaženo nebo zmenšeno tak, aby přesně odpovídalo klientské oblasti okna. Zobrazení s měřítkem nemá žádné posuvníky.

## <a name="see-also"></a>Viz také

[Použití zobrazení](../mfc/using-views.md)
