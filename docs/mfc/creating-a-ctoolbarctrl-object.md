---
title: Vytvoření objektu CToolBarCtrl | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CToolBarCtrl
dev_langs:
- C++
helpviewer_keywords:
- toolbar controls [MFC], creating
- CToolBarCtrl class [MFC], creating toolbars
ms.assetid: a4f6bf0c-0195-4dbf-a09e-aee503e19dc3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c98f99ef7ff26fed7d7df89881d2148af6bc993a
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46421645"
---
# <a name="creating-a-ctoolbarctrl-object"></a>Vytvoření objektu CToolBarCtrl

[Ctoolbarctrl –](../mfc/reference/ctoolbarctrl-class.md) objekty obsahují několik interních datových struktur – seznam rastrové obrázky tlačítka bitové kopie, seznam řetězců, popisku tlačítka a seznam `TBBUTTON` struktury –, který přidružit obrázek a/nebo řetězec s pozici, styl, stavu, a Identifikátor příkazu tlačítka. Každý prvek tyto datové struktury odkazuje na index založený na nule. Než budete moct použít `CToolBarCtrl` objektu, musíte nastavit tyto datové struktury. Seznam datových strukturách naleznete v tématu [ovládací prvky panelu nástrojů](controls-mfc.md) v sadě Windows SDK. Seznam řetězců, které jde použít jenom pro popisy tlačítek; řetězce nelze načíst z panelu nástrojů.

Použití `CToolBarCtrl` objektu, obvykle postupujte podle těchto kroků:

### <a name="to-use-a-ctoolbarctrl-object"></a>Použití objektu CToolBarCtrl

1. Vytvořit [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) objektu.

1. Volání [vytvořit](../mfc/reference/ctoolbarctrl-class.md#create) Windows běžné ovládací prvek panelu nástrojů a vytvořte tak `CToolBarCtrl` objektu. Pokud chcete rastrové obrázky tlačítka, přidejte rastrové obrázky tlačítka panelu nástrojů voláním [AddBitmap](../mfc/reference/ctoolbarctrl-class.md#addbitmap). Pokud chcete řetězec popisky tlačítek, přidejte řetězce na panelu nástrojů voláním [addstring –](../mfc/reference/ctoolbarctrl-class.md#addstring) a/nebo [AddStrings](../mfc/reference/ctoolbarctrl-class.md#addstrings). Po volání `AddString` a/nebo `AddStrings`, měli byste zavolat [AutoSize](../mfc/reference/ctoolbarctrl-class.md#autosize) zajistí řetězec nebo řetězce se zobrazí.

1. Panel nástrojů přidat tlačítko struktury voláním [AddButtons](../mfc/reference/ctoolbarctrl-class.md#addbuttons).

1. Pokud chcete popisy tlačítek, zpracovat **TTN_NEEDTEXT** zprávy v panelu nástrojů nadřazenému oknu, jak je popsáno v [zpracování oznámení popisů Tip](../mfc/handling-tool-tip-notifications.md).

1. Pokud chcete, aby vaši uživatelé nepotřebují k přizpůsobení panelu nástrojů, zpracování zpráv s oznámením přizpůsobení v nadřazenému oknu, jak je popsáno v [zpracování oznámení o přizpůsobení](../mfc/handling-customization-notifications.md).

## <a name="see-also"></a>Viz také

[Používání atributu CToolBarCtrl](../mfc/using-ctoolbarctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)

