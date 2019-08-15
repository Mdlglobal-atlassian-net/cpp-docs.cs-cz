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
ms.openlocfilehash: 7064880c5ceef8e7dc3e35bb7ef5bc700b0842d2
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69511228"
---
# <a name="scrolling-and-scaling-views"></a>Posouvání a změna měřítka zobrazení

MFC podporuje zobrazení, která jsou posunuta a zobrazení, která se automaticky škálují na velikost okna rámce, které je zobrazí. Třída `CScrollView` podporuje oba typy zobrazení.

Další informace o posouvání a škálování naleznete v tématu Class [CScrollView](../mfc/reference/cscrollview-class.md) in *MFC Reference*. Příklad posouvání najdete v [ukázce Klikyháky](../overview/visual-cpp-samples.md).

## <a name="what-do-you-want-to-know-more-about"></a>K čemu chcete získat další informace

- Posouvání zobrazení

- Změna měřítka zobrazení

- [Zobrazit souřadnice](/windows/win32/gdi/window-coordinate-system)

##  <a name="_core_scrolling_a_view"></a>Posouvání zobrazení

Velikost dokumentu je často větší, než může zobrazit jeho velikost. K tomu může dojít, protože se zvětší data dokumentu nebo uživatel zmenší okno, které zobrazení zaznamená. V takových případech musí zobrazení podporovat posouvání.

Jakékoli zobrazení může zpracovávat zprávy v rolovacím panelu ve `OnHScroll` svých `OnVScroll` členských funkcích. V těchto funkcích můžete implementovat zpracování zpráv pomocí posuvníku, provádět veškerou práci sami nebo můžete použít `CScrollView` třídu pro zpracování posouvání.

`CScrollView`provede následující akce:

- Spravuje okna a velikosti zobrazení a režimy mapování.

- Automaticky posouvá zprávy v reakci na panel zprávy s posuvníky.

Můžete určit, kolik se má posunout na "stránku" (když uživatel klikne na posuvník) a znak "line" (když uživatel klikne na šipku posuvníku). Tyto hodnoty Naplánujte tak, aby vyhovovaly povaze vašeho zobrazení. Například se můžete chtít posunout o 1 pixel přírůstcích pro zobrazení grafiky, ale v přírůstcích v závislosti na výšce čáry v textových dokumentech.

##  <a name="_core_scaling_a_view"></a>Změna měřítka zobrazení

Pokud chcete, aby zobrazení automaticky odpovídalo velikosti jeho okna rámce, můžete místo posouvání použít `CScrollView` pro škálování. Logické zobrazení je roztaženo nebo zmenšeno, aby se vešlo přesně do klientské oblasti okna. Zobrazení s měřítkem nemá žádné posuvníky.

## <a name="see-also"></a>Viz také:

[Použití zobrazení](../mfc/using-views.md)
