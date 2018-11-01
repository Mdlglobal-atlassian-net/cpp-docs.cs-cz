---
title: DRAWITEMSTRUCT – struktura
ms.date: 11/04/2016
f1_keywords:
- DRAWITEMSTRUCT
helpviewer_keywords:
- DRAWITEMSTRUCT structure [MFC]
ms.assetid: ba9ef1d4-aebb-45e9-b956-4b81a02e50f7
ms.openlocfilehash: 9c5bfc12bd371761682102dad6d7bcb75ef44151
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50624429"
---
# <a name="drawitemstruct-structure"></a>DRAWITEMSTRUCT – struktura

`DRAWITEMSTRUCT` Struktury poskytuje informace o nadřazenému oknu, musí mít k určení způsobu vykreslení ovládací prvek nebo nabídka položku vykreslovaných vlastníkem.

## <a name="syntax"></a>Syntaxe

```
typedef struct tagDRAWITEMSTRUCT {
    UINT CtlType;
    UINT CtlID;
    UINT itemID;
    UINT itemAction;
    UINT itemState;
    HWND hwndItem;
    HDC hDC;
    RECT rcItem;
    DWORD itemData;
} DRAWITEMSTRUCT;
```

#### <a name="parameters"></a>Parametry

*CtlType*<br/>
Typ ovládacího prvku. Hodnoty pro typy ovládacích prvků jsou následující:

- Tlačítka nakresleného vlastníkem ODT_BUTTON

- ODT_COMBOBOX vykreslovaných vlastníkem pole se seznamem

- Pole se seznamem vykreslovaných vlastníkem ODT_LISTBOX

- Nabídka ODT_MENU vykreslovaných vlastníkem

- Ovládací prvek zobrazení seznamu ODT_LISTVIEW

- ODT_STATIC vykreslovaných vlastníkem statický ovládací prvek

- Ovládací prvek karty ODT_TAB

*CtlID*<br/>
ID ovládacího prvku pro pole se seznamem, pole se seznamem nebo tlačítka. Tento člen se nepoužívá pro nabídky.

*ID položky*<br/>
ID položky nabídky pro nabídky nebo index položky v seznamu nebo pole se seznamem. Tento člen pro prázdný seznam nebo pole se seznamem, je záporná hodnota, která umožňuje, aby aplikace k vykreslení pouze obdélník na souřadnicích určené `rcItem` člen, i když neexistují žádné položky v ovládacím prvku. Uživatele mohou být zobrazeny tak, zda pole se seznamem nebo pole se seznamem má vstupní fokus. Nastavení bity `itemAction` člen Určuje, zda obdélníku je potřeba vykreslit jakoby seznamu nebo pole se seznamem má vstupní fokus.

*itemAction*<br/>
Definuje výkresu dělat. Bude jím nejméně jeden z následujících bits:

- ODA_DRAWENTIRE tento bit nastaven při celý ovládací prvek je nutné vykreslit.

- ODA_FOCUS tento bit nastaven, když ovládací prvek získá nebo ztratí vstupní fokus. `itemState` Člen zkontrolovat slouží k určení, zda ovládací prvek má fokus.

- ODA_SELECT tento bit nastaven pouze stav výběru se při změně. `itemState` Člen by měl být zkontrolována k určení nový stav výběru.

*itemState*<br/>
Určuje vizuální stav položky po provedení aktuální výkresu akce. To znamená pokud položka nabídky je nepřístupný, příznak stavu ODS_GRAYED se nastaví. Příznaky stavu jsou následující:

- ODS_CHECKED tento bit nastaven, pokud má být zkontrolován položky nabídky. Tato verze se používá jenom v nabídce.

- ODS_DISABLED tento bit nastaven, pokud položka je potřeba vykreslit jako zakázané.

- ODS_FOCUS tento bit nastaven, pokud položka má vstupní fokus.

- ODS_GRAYED tento bit nastaven, pokud položka je nepřístupný. Tato verze se používá jenom v nabídce.

- ODS_SELECTED tento bit nastaven, pokud je vybraný stav položky.

- ODS_COMBOBOXEDIT výkresu probíhá v oblasti výběru (textové pole) do pole se seznamem ownerdrawn.

- ODS_DEFAULT položky je výchozí položku.

*hwndItem*<br/>
Určuje popisovač okna ovládacího prvku pro pole se seznamem, seznamy a tlačítka. Určuje popisovač nabídky (HMENU), který obsahuje položku nabídky.

*hDC*<br/>
Určuje kontext zařízení. Kontext zařízení musí být použita při provádění operace kreslení. na ovládacím prvku.

*rcItem*<br/>
Obdélník v kontextu zařízení určeného *hDC* člena, který definuje hranice ovládacího prvku chcete kreslit. Windows automaticky klipy všechno, co v kontextu zařízení pro pole se seznamem, seznamy a tlačítka nakreslí vlastníka, ale není to galerie položek nabídky. Při vykreslování položky nabídky, nesmí kreslení vlastníka mimo hranice obdélníku definovaném `rcItem` člena.

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

## <a name="remarks"></a>Poznámky

Okno vlastníka ovládací prvek nebo nabídka položky vykreslovaných vlastníkem přijímá ukazatel na tuto strukturu jako *lParam* parametr WM_DRAWITEM zprávy.

## <a name="requirements"></a>Požadavky

**Záhlaví:** winuser

## <a name="see-also"></a>Viz také

[Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CWnd::OnDrawItem](../../mfc/reference/cwnd-class.md#ondrawitem)

