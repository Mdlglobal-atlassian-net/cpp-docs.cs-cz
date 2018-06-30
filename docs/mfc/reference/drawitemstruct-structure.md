---
title: Drawitemstruct – struktura | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- DRAWITEMSTRUCT
dev_langs:
- C++
helpviewer_keywords:
- DRAWITEMSTRUCT structure [MFC]
ms.assetid: ba9ef1d4-aebb-45e9-b956-4b81a02e50f7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ff4596a52170d0c6d197a0bda431963b5f0e9344
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2018
ms.locfileid: "37120931"
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
 *CtlType*  
 Typ ovládacího prvku. Typy ovládacích prvků hodnoty jsou následující:  
  
- Tlačítko ODT_BUTTON vykreslované uživatelem  
  
- ODT_COMBOBOX vykreslovaných vlastníkem pole se seznamem  
  
- Pole se seznamem vykreslovaných vlastníkem ODT_LISTBOX  
  
- Vlastní vykreslené nabídky ODT_MENU  
  
- Ovládací prvek seznamu ODT_LISTVIEW  
  
- ODT_STATIC vykreslovaných vlastníkem statického ovládacího prvku  
  
- Ovládací prvek karty ODT_TAB  
  
 *CtlID*  
 ID ovládacího prvku pole se seznamem, pole se seznamem nebo tlačítko. Tento člen není použit nabídky.  
  
 *itemID*  
 ID položky nabídky pro nabídky nebo index položky v seznamu nebo pole se seznamem. Prázdný seznam nebo pole se seznamem, je tento člen zápornou hodnotu, která umožní aplikaci k vykreslení pouze rámečku fokusu v souřadnice určeného `rcItem` člen, i když neexistují žádné položky v ovládacím prvku. Uživatel může zobrazit proto zda pole se seznamem nebo pole se seznamem má zaměření pro vstup. Nastavení bity `itemAction` člen Určuje, zda rámeček je k tomu, jako kdyby pole se seznamem nebo pole se seznamem má vstupu fokus.  
  
 *itemAction*  
 Definuje kreslení vyžadována akce. Bude jím nejméně jeden z následujících bits:  
  
- ODA_DRAWENTIRE tato verze se nastaví, pokud je nutné vykreslit celý ovládací prvek.  
  
- ODA_FOCUS tento bit nastaven při získá ovládací prvek nebo ztratí zaměření pro vstup. `itemState` Člen kontroly k určení, zda má právě fokus, ovládacího prvku.  
  
- ODA_SELECT tato verze se nastaví, pokud došlo ke změně pouze stav výběru. `itemState` Člen zkontrolovat určit nový stav výběru.  
  
 *itemState*  
 Určuje visual stav položky po aktuální kreslení akce se provede. To znamená pokud položku nabídky má být neaktivní, stav příznak ODS_GRAYED se nastaví. Příznaky stavu jsou následující:  
  
- ODS_CHECKED tento bit nastaven, pokud má být zkontrolován položku nabídky. Tato verze se používá pouze v nabídce.  
  
- ODS_DISABLED tento bit nastaven, pokud je položka, které se mají vykreslovat jako zakázané.  
  
- ODS_FOCUS tento bit bude nastavena, pokud má položka vstupních fokus.  
  
- ODS_GRAYED tento bit nastaven, pokud položka má být neaktivní. Tato verze se používá pouze v nabídce.  
  
- ODS_SELECTED tento bit nastaven, pokud je vybraný stav položky.  
  
- ODS_COMBOBOXEDIT kreslení probíhá v poli Výběr (ovládací prvek pro úpravy) – pole se seznamem ownerdrawn.  
  
- ODS_DEFAULT položka je výchozí položku.  
  
 *hwndItem*  
 Určuje popisovač okna ovládacího prvku pole se seznamem, seznamy a tlačítka. Určuje popisovač v nabídce (HMENU), který obsahuje položky pro nabídky.  
  
 *hDC*  
 Identifikuje kontextu zařízení. Tento kontext zařízení musí být použita při provádění operací kreslení na ovládací prvek.  
  
 *rcItem*  
 Obdélníku v kontextu zařízení určeného *hDC* člena, který definuje hranice řízení, které se mají vykreslovat. Windows automaticky klipy nic, co vlastník nevykresluje v kontextu zařízení pro pole se seznamem, seznamy a tlačítka, ale jeho není oříznutí položky nabídky. Při kreslení položky nabídky, vlastník nesmí kreslení mimo hranice rámeček definované `rcItem` člen.  
  
 *itemData*  
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
 Okno vlastník nabídky nebo ovládací prvek položky vykreslovaných vlastníkem obdrží ukazatel na tato struktura jako *lParam* parametr WM_DRAWITEM zprávy.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** winuser  
  
## <a name="see-also"></a>Viz také  
 [Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CWnd::OnDrawItem](../../mfc/reference/cwnd-class.md#ondrawitem)

