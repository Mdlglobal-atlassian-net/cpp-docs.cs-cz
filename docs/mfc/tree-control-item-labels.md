---
title: Popisky položek ovládacího prvku strom
ms.date: 11/04/2016
helpviewer_keywords:
- tree controls [MFC], item labels
- labels, CTreeCtrl items
- CTreeCtrl class [MFC], item labels
- item labels, tree controls
- item labels
ms.assetid: fe834107-1a25-4280-aced-774c11565805
ms.openlocfilehash: 16bb2bbe63eaf8ea4ce30040589d4a8a4cf4dfd3
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70741467"
---
# <a name="tree-control-item-labels"></a>Popisky položek ovládacího prvku strom

Při přidávání položky do ovládacího prvku stromu ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) obvykle určujete text popisku položky. Členská funkce může předat strukturu TVITEM, která definuje vlastnosti položky, včetně řetězce obsahujícího text popisku. [](/windows/win32/api/commctrl/ns-commctrl-tvitemw) `InsertItem` `InsertItem`má několik přetížení, které lze volat s různými kombinacemi parametrů.

Ovládací prvek stromu přiděluje paměť pro ukládání každé položky; text popisků položek zabere významnou část této paměti. Pokud vaše aplikace udržuje kopii řetězců v ovládacím prvku stromu, můžete snížit požadavky na paměť ovládacího prvku zadáním hodnoty **LPSTR_TEXTCALLBACK** v *pszText* členu `TV_ITEM` nebo v *lpszItem* namísto předání skutečných řetězců ovládacímu prvku stromu. Pomocí **LPSTR_TEXTCALLBACK** způsobí, že ovládací prvek stromu načte text popisku položky z aplikace vždy, když je nutné překreslit položku. Chcete-li načíst text, ovládací prvek stromové zprávy pošle zprávu s oznámením [TVN_GETDISPINFO](/windows/win32/Controls/tvn-getdispinfo) , která obsahuje adresu [NMTVDISPINFO](/windows/win32/api/commctrl/ns-commctrl-nmtvdispinfow) struktury. Je nutné odpovědět nastavením příslušných členů zahrnuté struktury.

Strom ovládacího prvku používá paměť přidělenou z haldy procesu, který vytváří ovládací prvek stromu. Maximální počet položek v ovládacím prvku stromu je založen na množství paměti dostupné v haldě. Každá položka zabere 64 bajtů.

## <a name="see-also"></a>Viz také:

[Používání atributu CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
