---
title: Členské funkce ovládacího prvku jezdec
ms.date: 11/04/2016
helpviewer_keywords:
- CSliderCtrl class [MFC], methods
- slider controls [MFC], member functions
ms.assetid: dbde49ee-7306-4d14-a6ce-d09aa198178f
ms.openlocfilehash: a88dd1a49eb928261393a4473ee7eb53628c607a
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57296901"
---
# <a name="slider-control-member-functions"></a>Členské funkce ovládacího prvku jezdec

Aplikace může volat posuvník členské funkce ovládacího prvku k načtení informací o ovládacím prvku posuvník ([atributu CSliderCtrl](../mfc/reference/csliderctrl-class.md)) a změnit jeho vlastnosti.

Chcete-li načíst pozice posuvníku (to znamená, že hodnota uživatel se rozhodl), použijte [GetPos](../mfc/reference/csliderctrl-class.md#getpos) členskou funkci. Pokud chcete nastavit pozice posuvníku, použijte [SetPos](../mfc/reference/csliderctrl-class.md#setpos) členskou funkci. Kdykoli můžete použít `VerifyPos` členskou funkci, abyste měli jistotu, že je posuvník mezi minimální a maximální hodnoty.

Rozsah ovládacím prvku posuvník je sada souvislých hodnot, které mohou představovat v ovládacím prvku posuvník. Většina aplikací používá [SetRange](../mfc/reference/csliderctrl-class.md#setrange) členskou funkci pro nastavení rozsahu ovládacím prvku posuvník při prvním vytvoření. Aplikace můžete dynamicky měnit rozsahu po vytvoření s použitím ovládacího prvku posuvník [SetRangeMax](../mfc/reference/csliderctrl-class.md#setrangemax) a [SetRangeMin](../mfc/reference/csliderctrl-class.md#setrangemin) členské funkce. Aplikace, která umožňuje rozsahu, který chcete změnit dynamicky obvykle načte nastavení konečného rozsahu, po dokončení práce s ovládacím prvkem posuvníku uživatelem. Chcete-li načíst tato nastavení, použijte [getrange –](../mfc/reference/csliderctrl-class.md#getrange), [GetRangeMax](../mfc/reference/csliderctrl-class.md#getrangemax), a [GetRangeMin](../mfc/reference/csliderctrl-class.md#getrangemin) členské funkce.

Aplikace může použít styl TBS_AUTOTICKS mít ovládací prvek posuvník osové značky zobrazeny automaticky. Pokud aplikace potřebuje k řízení polohy nebo frekvence osové značky, ale počet členských funkcí, které můžete použít.

Nastavit pozici značky zaškrtnutí, může aplikace použít [SetTic](../mfc/reference/csliderctrl-class.md#settic) členskou funkci. [SetTicFreq](../mfc/reference/csliderctrl-class.md#setticfreq) členská funkce umožňuje aplikaci nastavit značky, které se zobrazují v pravidelných intervalech v rozsahu v ovládacím prvku posuvník osových značek. Například aplikace tuto funkci člena můžete použít k zobrazení jen 10 osové značky v rozsahu od 1 do 100.

Pro načtení indexu v rozsahu odpovídající značky zaškrtnutí, použijte [GetTic](../mfc/reference/csliderctrl-class.md#gettic) členskou funkci. [GetTicArray](../mfc/reference/csliderctrl-class.md#getticarray) členskou funkci načte pole tyto indexy. Pokud chcete načíst umístění značky zaškrtnutí v souřadnice klienta, použijte [GetTicPos](../mfc/reference/csliderctrl-class.md#getticpos) členskou funkci. Aplikace můžete načíst pomocí počet značek [GetNumTics](../mfc/reference/csliderctrl-class.md#getnumtics) členskou funkci.

[ClearTics](../mfc/reference/csliderctrl-class.md#cleartics) členská funkce odebere všechny značky ovládacího prvku posuvník.

Velikost řádku posuvník ovládacího prvku určuje, nakolik se posuvník posune po přijetí oznámení TB_LINEDOWN nebo TB_LINEUP aplikace. Podobně velikost stránky určuje odpověď na TB_PAGEDOWN a TB_PAGEUP zprávy s oznámením. Aplikace můžete načítat a nastavovat hodnoty velikosti řádku a stránky s použitím [GetLineSize](../mfc/reference/csliderctrl-class.md#getlinesize), [SetLineSize](../mfc/reference/csliderctrl-class.md#setlinesize), [GetPageSize](../mfc/reference/csliderctrl-class.md#getpagesize), a [SetPageSize](../mfc/reference/csliderctrl-class.md#setpagesize) členské funkce.

Aplikace můžete členské funkce použít k načtení rozměrů posuvníku. [GetThumbRect](../mfc/reference/csliderctrl-class.md#getthumbrect) načte členské funkce ohraničující obdélník pro posuvník. [GetChannelRect](../mfc/reference/csliderctrl-class.md#getchannelrect) načte členské funkce ohraničující obdélník kanálu v ovládacím prvku posuvník. (Kanál je oblast, přes který se posuvník posune a který obsahuje zvýraznění, když je vybrána oblast.)

Pokud má ovládací prvek posuvník TBS_ENABLESELRANGE styl, může uživatel vybrat rozsah souvislých hodnot z něj. Počet členských funkcí, které umožňují výběr rozsahu upraví dynamicky. [SetSelection](../mfc/reference/csliderctrl-class.md#setselection) členská funkce nastaví počáteční a koncová pozice výběru. Po dokončení nastavení oblast výběru uživatel aplikace můžete načíst nastavení pomocí [GetSelection](../mfc/reference/csliderctrl-class.md#getselection) členskou funkci. Chcete-li zrušit výběr uživatele, použijte [ClearSel](../mfc/reference/csliderctrl-class.md#clearsel) členskou funkci.

## <a name="see-also"></a>Viz také:

[Používání atributu CSliderCtrl](../mfc/using-csliderctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
