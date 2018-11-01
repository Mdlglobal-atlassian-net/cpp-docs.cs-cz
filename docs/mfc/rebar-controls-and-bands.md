---
title: Matrice – ovládací prvky a pruhy
ms.date: 11/04/2016
helpviewer_keywords:
- rebar controls [MFC], working with bands in
- bands, in rebar controls
ms.assetid: b647e7a5-9ea7-48b1-8e5f-096d104748f0
ms.openlocfilehash: aa20e44825ec57dba19dad0b2a11ca51f315743e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50582049"
---
# <a name="rebar-controls-and-bands"></a>Matrice – ovládací prvky a pruhy

Hlavním účelem ovládacím prvkem matrice, je tak, aby fungoval jako kontejner pro podřízená okna, běžné ovládací prvky dialogového okna, nabídky, panely nástrojů a tak dále. Toto členství ve skupině podporuje koncept "vzdálené". Každé vzdálené matrice může obsahovat libovolnou kombinaci úchytu panelu, bitmapy, textový popisek a podřízené okno.

Třída `CReBarCtrl` obsahuje mnoho funkcí členů, můžete použít k načtení a manipulaci s informace pro konkrétní matrice pásmo:

- [GetBandCount](../mfc/reference/crebarctrl-class.md#getbandcount) zjišťuje číslo aktuální pruhy v ovládacím prvku matrice.

- [GetBandInfo](../mfc/reference/crebarctrl-class.md#getbandinfo) inicializuje **REBARBANDINFO** struktura s informacemi ze zadaného obsluhy vzdálené správy. Neexistuje odpovídající [SetBandInfo](../mfc/reference/crebarctrl-class.md#setbandinfo) členskou funkci.

- [GetRect –](../mfc/reference/crebarctrl-class.md#getrect) načte ohraničující obdélník zadané obsluhy vzdálené správy.

- [GetRowCount](../mfc/reference/crebarctrl-class.md#getrowcount) zjišťuje počet vzdálené řádky v ovládacím prvku matrice.

- [IDToIndex](../mfc/reference/crebarctrl-class.md#idtoindex) načte index zadaný obsluhy vzdálené správy.

- [GetBandBorders](../mfc/reference/crebarctrl-class.md#getbandborders) načte ohraničení pásu.

Kromě manipulaci několik členské funkce jsou k dispozici, které umožňují pracovat s pruhy matrice konkrétní.

[InsertBand](../mfc/reference/crebarctrl-class.md#insertband) a [DeleteBand](../mfc/reference/crebarctrl-class.md#deleteband) přidávat a odebírat pruhy matrice. [MinimizeBand](../mfc/reference/crebarctrl-class.md#minimizeband) a [MaximizeBand](../mfc/reference/crebarctrl-class.md#maximizeband) vliv aktuální velikost svazku konkrétní matrice. [MoveBand](../mfc/reference/crebarctrl-class.md#moveband) změní index pásmo konkrétní matrice. [ShowBand](../mfc/reference/crebarctrl-class.md#showband) zobrazí nebo skryje pruhy matrice od uživatele.

Následující příklad ukazuje přidání panelu nástrojů (*m_wndToolBar*) do existujícího ovládacího prvku matrice (*m_wndReBar*). Pásmo je popsán inicializace `rbi` strukturu a následným voláním `InsertBand` členské funkce:

[!code-cpp[NVC_MFCControlLadenDialog#27](../mfc/codesnippet/cpp/rebar-controls-and-bands_1.cpp)]

## <a name="see-also"></a>Viz také

[Používání atributu CReBarCtrl](../mfc/using-crebarctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)

