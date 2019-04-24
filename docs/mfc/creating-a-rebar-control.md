---
title: Vytvoření ovládacího prvku matrice
ms.date: 11/04/2016
helpviewer_keywords:
- rebar controls [MFC], creating
- CReBarCtrl class [MFC], creating
ms.assetid: 0a012e08-772b-4f6a-af86-7cb651d11d3e
ms.openlocfilehash: 0fb651aef599b64b787d96a668e2e1496c1dff8e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62153342"
---
# <a name="creating-a-rebar-control"></a>Vytvoření ovládacího prvku matrice

[Crebarctrl –](../mfc/reference/crebarctrl-class.md) objektů by měl být vytvořen před nadřazeného objektu je viditelný. Tím se minimalizují možnosti vykreslování problémy.

Například ovládací prvky matrice (používané objekty oken rámce) se běžně používají jako nadřazeného okna pro ovládací prvky panelu nástrojů. Nadřazeného ovládacího prvku rebar. proto je objekt okna rámce. Vzhledem k tomu, že objekt okna rámce je nadřazeným prvkem, `OnCreate` členské funkce (nadřazené) je vhodné místo pro vytvoření ovládacího prvku rebar.

Použití `CReBarCtrl` objektu, obvykle postupujte podle těchto kroků:

### <a name="to-use-a-crebarctrl-object"></a>Chcete-li použít objekt atributu CReBarCtrl

1. Vytvořit [atributu CReBarCtrl](../mfc/reference/crebarctrl-class.md) objektu.

1. Volání [vytvořit](../mfc/reference/crebarctrl-class.md#create) běžné prvku matrice Windows vytvořit a připojit ji k `CReBarCtrl` objektu zadáte všechny požadované styly.

1. Načíst rastrový obrázek, voláním [CBitmap::LoadBitmap](../mfc/reference/cbitmap-class.md#loadbitmap), který se použije jako pozadí objekt ovládacího prvku rebar.

1. Vytváření a inicializace všechny podřízené objekty oken (panely nástrojů, ovládací prvky dialogového okna a podobně) obsahující objekt ovládacího prvku rebar.

1. Inicializace **REBARBANDINFO** struktura s použitím informací potřebných pro vzdálené Chystáte se vložit.

1. Volání [InsertBand](../mfc/reference/crebarctrl-class.md#insertband) vložit existující podřízených oken (například `m_wndReToolBar`) do nového ovládacího prvku rebar. Další informace o vkládání pruhy do existujícího ovládacího prvku matrice, naleznete v tématu [matrice ovládací prvky a pruhy](../mfc/rebar-controls-and-bands.md).

## <a name="see-also"></a>Viz také:

[Používání atributu CReBarCtrl](../mfc/using-crebarctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
