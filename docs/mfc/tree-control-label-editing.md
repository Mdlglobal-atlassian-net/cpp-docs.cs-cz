---
title: Úpravy štítků ovládacích prvků strom
ms.date: 11/04/2016
helpviewer_keywords:
- editing tree control labels
- CTreeCtrl class [MFC], editing labels
- label editing in CTreeCtrl class [MFC]
- tree controls [MFC], label editing
ms.assetid: 6cde2ac3-43ee-468f-bac2-cf1a228ad32d
ms.openlocfilehash: 4b53d2c8e5a26a4dc37dfd7ae0710748bcd27bf6
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70741224"
---
# <a name="tree-control-label-editing"></a>Úpravy štítků ovládacích prvků strom

Uživatel může přímo upravit popisky položek v ovládacím prvku stromu ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)), které mají styl **TVS_EDITLABELS** . Uživatel začne upravovat kliknutím na popisek položky, která má fokus. Aplikace začne upravovat pomocí členské funkce [EditLabel](../mfc/reference/ctreectrl-class.md#editlabel) . Ovládací prvek strom pošle oznámení při zahájení úprav a při jeho zrušení nebo dokončení. Po dokončení úprav zodpovídáte za aktualizaci popisku položky, pokud je to vhodné.

Po zahájení úprav popisku pošle ovládací prvek stromu zprávu s oznámením [TVN_BEGINLABELEDIT](/windows/win32/Controls/tvn-beginlabeledit) . Zpracováním tohoto oznámení můžete umožnit úpravy některých popisků a zabránit úpravám dalších. Vrácení 0 umožňuje úpravy a vrácení nenulového chování.

Když se úpravy popisku zruší nebo dokončí, ovládací prvek stromové zprávy pošle oznámení [TVN_ENDLABELEDIT](/windows/win32/Controls/tvn-endlabeledit) . Parametr *lParam* je adresa struktury [NMTVDISPINFO](/windows/win32/api/commctrl/ns-commctrl-nmtvdispinfow) . Člen **položky** je struktura [TVITEM](/windows/win32/api/commctrl/ns-commctrl-tvitemw) , která identifikuje položku a obsahuje upravený text. Zodpovídáte za aktualizaci popisku položky, pokud je to vhodné, třeba po ověření upravovaného řetězce. Člen`TV_ITEM` *pszText* je 0, pokud probíhá zrušení úprav.

Během úprav popisku, obvykle v reakci na zprávu oznámení [TVN_BEGINLABELEDIT](/windows/win32/Controls/tvn-beginlabeledit) , můžete získat ukazatel na ovládací prvek pro úpravy, který se používá pro úpravu popisku pomocí členské funkce [GetEditControl](../mfc/reference/ctreectrl-class.md#geteditcontrol) . Můžete zavolat členskou funkci [SetLimitText](../mfc/reference/cedit-class.md#setlimittext) ovládacího prvku pro omezení množství textu, který může uživatel zadat nebo podtřídit ovládacímu prvku pro úpravy k zachycení a zrušení neplatných znaků. Všimněte si však, že se ovládací prvek Edit zobrazuje až *po* odeslání **TVN_BEGINLABELEDIT** .

## <a name="see-also"></a>Viz také:

[Používání atributu CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
