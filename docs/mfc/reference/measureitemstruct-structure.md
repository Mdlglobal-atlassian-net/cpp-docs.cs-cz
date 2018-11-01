---
title: MEASUREITEMSTRUCT – struktura
ms.date: 11/04/2016
f1_keywords:
- MEASUREITEMSTRUCT
helpviewer_keywords:
- MEASUREITEMSTRUCT structure [MFC]
ms.assetid: d141ace4-47cb-46b5-a81c-ad2c5e5a8501
ms.openlocfilehash: 3f541c30c484041d855807f220345d6863a780d6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50575038"
---
# <a name="measureitemstruct-structure"></a>MEASUREITEMSTRUCT – struktura

`MEASUREITEMSTRUCT` Struktura informuje Windows dimenzí ovládací prvek nebo nabídka položku vykreslovaných vlastníkem.

## <a name="syntax"></a>Syntaxe

```
typedef struct tagMEASUREITEMSTRUCT {
    UINT CtlType;
    UINT CtlID;
    UINT itemID;
    UINT itemWidth;
    UINT itemHeight;
    DWORD itemData
} MEASUREITEMSTRUCT;
```

#### <a name="parameters"></a>Parametry

*CtlType*<br/>
Obsahuje typ ovládacího prvku. Hodnoty pro typy ovládacích prvků jsou následující:

- Pole se seznamem ODT_COMBOBOX vykreslené vlastníkem.

- Pole se seznamem ODT_LISTBOX vykreslené vlastníkem.

- ODT_MENU nabídce vykreslené vlastníkem.

*CtlID*<br/>
Obsahuje ID ovládacího prvku pro pole se seznamem, pole se seznamem nebo tlačítka. Tento člen se nepoužívá pro nabídky.

*ID položky*<br/>
Obsahuje ID položky nabídky nabídky nebo ID položky seznamu pole proměnné výšky pole se seznamem nebo seznamu. Tento člen se nepoužívá pro pevné výšky pole se seznamem nebo seznamu pole nebo tlačítka.

*itemWidth*<br/>
Určuje šířku položky nabídky. Vlastníkem vykreslené vlastníkem. položka nabídky vyplnit tento člen ještě před jeho vrácením ze zprávy.

*itemHeight*<br/>
Určuje výšku jednotlivých položek v seznamu nebo nabídky. Před vrácením z zprávy, vlastník pole se seznamem vykreslené vlastníkem, seznamu nebo položky nabídky vyplňte tento člen. Maximální výška položky v seznamu je 255.

*itemData*<br/>
Pro pole se seznamem nebo seznamu tento člen obsahuje hodnotu, která byla předána do seznamu o jednu z následujících akcí:

- [CComboBox::AddString](../../mfc/reference/ccombobox-class.md#addstring)

- [CComboBox::InsertString](../../mfc/reference/ccombobox-class.md#insertstring)

- [CListBox::AddString](../../mfc/reference/clistbox-class.md#addstring)

- [CListBox::InsertString](../../mfc/reference/clistbox-class.md#insertstring)

Tento člen nabídky, obsahuje hodnotu, která byla předána do nabídky pomocí jedné z následujících akcí:

- [CMenu::AppendMenu](../../mfc/reference/cmenu-class.md#appendmenu)

- [CMenu::InsertMenu](../../mfc/reference/cmenu-class.md#insertmenu)

- [CMenu::ModifyMenu](../../mfc/reference/cmenu-class.md#modifymenu)

To umožňuje Windows správně zpracovat interakce uživatele s ovládacím prvkem. Selhání k vyplnění správné členů `MEASUREITEMSTRUCT` způsobí, že struktura nesprávnou operaci ovládacího prvku.

## <a name="requirements"></a>Požadavky

**Záhlaví:** winuser

## <a name="see-also"></a>Viz také

[Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CWnd::OnMeasureItem](../../mfc/reference/cwnd-class.md#onmeasureitem)

