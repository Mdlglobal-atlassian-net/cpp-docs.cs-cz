---
title: "Drawitemstruct – struktura | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: DRAWITEMSTRUCT
dev_langs: C++
helpviewer_keywords: DRAWITEMSTRUCT structure [MFC]
ms.assetid: ba9ef1d4-aebb-45e9-b956-4b81a02e50f7
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c63183cf721523b2f6b776dfad3bb9490816c703
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="drawitemstruct-structure"></a>DRAWITEMSTRUCT – struktura
`DRAWITEMSTRUCT` Struktura poskytuje informace okno vlastníka musí mít určit, jak k vyplnění vykreslovaných vlastníkem nebo nabídky ovládací prvek položku.  
  
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
 `CtlType`  
 Typ ovládacího prvku. Typy ovládacích prvků hodnoty jsou následující:  
  
- **ODT_BUTTON** tlačítko vykreslované uživatelem  
  
- **ODT_COMBOBOX** vykreslovaných vlastníkem pole se seznamem  
  
- **ODT_LISTBOX** pole se seznamem vykreslované uživatelem  
  
- **ODT_MENU** vykreslovaných vlastníkem nabídky  
  
- **ODT_LISTVIEW** ovládacího prvku zobrazení seznamu  
  
- **ODT_STATIC** vykreslovaných vlastníkem statického ovládacího prvku  
  
- **ODT_TAB** kartě ovládací prvek  
  
 `CtlID`  
 ID ovládacího prvku pole se seznamem, pole se seznamem nebo tlačítko. Tento člen není použit nabídky.  
  
 `itemID`  
 ID položky nabídky pro nabídky nebo index položky v seznamu nebo pole se seznamem. Prázdný seznam nebo pole se seznamem, je tento člen zápornou hodnotu, která umožní aplikaci k vykreslení pouze rámečku fokusu v souřadnice určeného **rcItem** člen, i když neexistují žádné položky v ovládacím prvku. Uživatel může zobrazit proto zda pole se seznamem nebo pole se seznamem má zaměření pro vstup. Nastavení bity **itemAction** člen Určuje, zda rámeček je k tomu, jako kdyby pole se seznamem nebo pole se seznamem má vstupu fokus.  
  
 `itemAction`  
 Definuje kreslení vyžadována akce. Bude jím nejméně jeden z následujících bits:  
  
- **ODA_DRAWENTIRE** tento bit nastaven při celý ovládací prvek, je nutné vykreslit.  
  
- **ODA_FOCUS** tento bit nastaven při získá ovládací prvek nebo ztratí zaměření pro vstup. **ItemState** člen kontroly k určení, zda má právě fokus, ovládacího prvku.  
  
- **ODA_SELECT** tento bit nastaven při pouze stav výběru se změnil. **ItemState** člen zkontrolovat určit nový stav výběru.  
  
 *itemState*  
 Určuje visual stav položky po aktuální kreslení akce se provede. To znamená, pokud položku nabídky je jako neaktivní, stav příznak **ODS_GRAYED** bude nastavena. Příznaky stavu jsou následující:  
  
- **ODS_CHECKED** tento bit nastaven, pokud má být zkontrolován položku nabídky. Tato verze se používá pouze v nabídce.  
  
- **ODS_DISABLED** tento bit nastaven, pokud je položka, které se mají vykreslovat jako zakázané.  
  
- **ODS_FOCUS** tento bit nastaven, pokud má položka vstupních fokus.  
  
- **ODS_GRAYED** tento bit nastaven, pokud položka má být neaktivní. Tato verze se používá pouze v nabídce.  
  
- **ODS_SELECTED** tento bit nastaven, pokud je vybraný stav položky.  
  
- **ODS_COMBOBOXEDIT** kreslení probíhá v poli Výběr (ovládací prvek pro úpravy) – pole se seznamem ownerdrawn.  
  
- **ODS_DEFAULT** položka je výchozí položku.  
  
 `hwndItem`  
 Určuje popisovač okna ovládacího prvku pole se seznamem, seznamy a tlačítka. Určuje popisovač v nabídce (`HMENU`) obsahující položku pro nabídky.  
  
 `hDC`  
 Identifikuje kontextu zařízení. Tento kontext zařízení musí být použita při provádění operací kreslení na ovládací prvek.  
  
 *rcItem*  
 Obdélníku v kontextu zařízení určeného `hDC` člena, který definuje hranice řízení, které se mají vykreslovat. Windows automaticky klipy nic, co vlastník nevykresluje v kontextu zařízení pro pole se seznamem, seznamy a tlačítka, ale jeho není oříznutí položky nabídky. Při kreslení položky nabídky, vlastník nesmí kreslení mimo hranice rámeček definované **rcItem** člen.  
  
 `itemData`  
 Pole se seznamem nebo pole se seznamem tento člen obsahuje hodnotu, která byla předána do pole se seznamem pomocí jedné z následujících akcí:  
  
- [CComboBox::AddString](../../mfc/reference/ccombobox-class.md#addstring)  
  
- [CComboBox::InsertString](../../mfc/reference/ccombobox-class.md#insertstring)  
  
- [CListBox::AddString](../../mfc/reference/clistbox-class.md#addstring)  
  
- [CListBox::InsertString](../../mfc/reference/clistbox-class.md#insertstring)  
  
 Tento člen nabídky, obsahuje hodnotu, která byla předána do nabídky pomocí jedné z následujících akcí:  
  
- [CMenu::AppendMenu](../../mfc/reference/cmenu-class.md#appendmenu)  
  
- [CMenu::InsertMenu](../../mfc/reference/cmenu-class.md#insertmenu)  
  
- [CMenu::ModifyMenu](../../mfc/reference/cmenu-class.md#modifymenu)  
  
## <a name="remarks"></a>Poznámky  
 Okno vlastník nabídky nebo ovládací prvek položky vykreslovaných vlastníkem obdrží ukazatel na tato struktura jako `lParam` parametr `WM_DRAWITEM` zprávy.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** winuser  
  
## <a name="see-also"></a>Viz také  
 [Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CWnd::OnDrawItem](../../mfc/reference/cwnd-class.md#ondrawitem)

