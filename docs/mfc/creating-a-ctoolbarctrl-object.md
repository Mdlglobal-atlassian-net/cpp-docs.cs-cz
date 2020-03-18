---
title: Vytvoření objektu CToolBarCtrl
ms.date: 11/04/2016
helpviewer_keywords:
- toolbar controls [MFC], creating
- CToolBarCtrl class [MFC], creating toolbars
ms.assetid: a4f6bf0c-0195-4dbf-a09e-aee503e19dc3
ms.openlocfilehash: cf1d2eeb9efd2f8a1e7b433c0e18dd868a8b9aca
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79445891"
---
# <a name="creating-a-ctoolbarctrl-object"></a>Vytvoření objektu CToolBarCtrl

Objekty [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) obsahují několik vnitřních datových struktur – seznam rastrových obrázků tlačítek, seznam řetězců popisků tlačítek a seznam `TBBUTTON`ch struktur – které přiřadí obrázek nebo řetězec k pozici, stylu, stavu a ID příkazu tlačítka. Na každý z prvků těchto datových struktur se odkazuje index založený na nule. Než budete moci použít objekt `CToolBarCtrl`, je nutné nastavit tyto datové struktury. Seznam datových struktur najdete v tématu [ovládací prvky panelu nástrojů](controls-mfc.md) v Windows SDK. Seznam řetězců lze použít pouze pro popisky tlačítek; z panelu nástrojů nelze načíst řetězce.

Chcete-li použít objekt `CToolBarCtrl`, obvykle se řiďte těmito kroky:

### <a name="to-use-a-ctoolbarctrl-object"></a>Použití objektu CToolBarCtrl

1. Sestavte objekt [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) .

1. Voláním [Create](../mfc/reference/ctoolbarctrl-class.md#create) Vytvořte běžný ovládací prvek panelu nástrojů systému Windows a připojte jej k objektu `CToolBarCtrl`. Pokud chcete rastrové obrázky pro tlačítka, přidejte rastrové obrázky tlačítka na panel nástrojů voláním [AddBitmap](../mfc/reference/ctoolbarctrl-class.md#addbitmap). Pokud chcete jmenovky řetězce pro tlačítka, přidejte řetězce na panel nástrojů voláním [AddString](../mfc/reference/ctoolbarctrl-class.md#addstring) a/nebo [AddStrings](../mfc/reference/ctoolbarctrl-class.md#addstrings). Po volání `AddString` a/nebo `AddStrings`byste měli zavolat funkci [AutoSize](../mfc/reference/ctoolbarctrl-class.md#autosize) , aby se zobrazil řetězec nebo řetězce, které se mají zobrazit.

1. Přidejte do panelu nástrojů struktury tlačítek voláním [AddButtons](../mfc/reference/ctoolbarctrl-class.md#addbuttons).

1. Pokud potřebujete popisy tlačítek, zpracujte zprávy **TTN_NEEDTEXT** v okně vlastníka panelu nástrojů, jak je popsáno v tématu [zpracování oznámení s popisem nástrojů](../mfc/handling-tool-tip-notifications.md).

1. Pokud chcete, aby uživatel mohl přizpůsobit panel nástrojů, zpracujte zprávy s oznámením o přizpůsobení v okně vlastník, jak je popsáno v [tématu zpracování oznámení přizpůsobení](../mfc/handling-customization-notifications.md).

## <a name="see-also"></a>Viz také

[Používání atributu CToolBarCtrl](../mfc/using-ctoolbarctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
