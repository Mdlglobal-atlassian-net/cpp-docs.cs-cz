---
title: "Třída CMFCToolBarComboBoxButton | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCToolBarComboBoxButton
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::CMFCToolBarComboBoxButton
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::AddItem
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::AddSortedItem
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::Compare
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::CreateEdit
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::DeleteItem
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::FindItem
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetByCmd
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetComboBox
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetCount
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetCountAll
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetCurSel
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetCurSelAll
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetEditCtrl
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetItem
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetItemAll
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetItemData
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetItemDataAll
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetItemDataPtrAll
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetText
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetTextAll
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::IsCenterVert
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::IsFlatMode
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::RemoveAllItems
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::SelectItem
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::SelectItemAll
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::SetCenterVert
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::SetDropDownHeight
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::SetFlatMode
dev_langs:
- C++
helpviewer_keywords:
- CMFCToolBarComboBoxButton [MFC], CMFCToolBarComboBoxButton
- CMFCToolBarComboBoxButton [MFC], AddItem
- CMFCToolBarComboBoxButton [MFC], AddSortedItem
- CMFCToolBarComboBoxButton [MFC], Compare
- CMFCToolBarComboBoxButton [MFC], CreateEdit
- CMFCToolBarComboBoxButton [MFC], DeleteItem
- CMFCToolBarComboBoxButton [MFC], FindItem
- CMFCToolBarComboBoxButton [MFC], GetByCmd
- CMFCToolBarComboBoxButton [MFC], GetComboBox
- CMFCToolBarComboBoxButton [MFC], GetCount
- CMFCToolBarComboBoxButton [MFC], GetCountAll
- CMFCToolBarComboBoxButton [MFC], GetCurSel
- CMFCToolBarComboBoxButton [MFC], GetCurSelAll
- CMFCToolBarComboBoxButton [MFC], GetEditCtrl
- CMFCToolBarComboBoxButton [MFC], GetItem
- CMFCToolBarComboBoxButton [MFC], GetItemAll
- CMFCToolBarComboBoxButton [MFC], GetItemData
- CMFCToolBarComboBoxButton [MFC], GetItemDataAll
- CMFCToolBarComboBoxButton [MFC], GetItemDataPtrAll
- CMFCToolBarComboBoxButton [MFC], GetText
- CMFCToolBarComboBoxButton [MFC], GetTextAll
- CMFCToolBarComboBoxButton [MFC], IsCenterVert
- CMFCToolBarComboBoxButton [MFC], IsFlatMode
- CMFCToolBarComboBoxButton [MFC], RemoveAllItems
- CMFCToolBarComboBoxButton [MFC], SelectItem
- CMFCToolBarComboBoxButton [MFC], SelectItemAll
- CMFCToolBarComboBoxButton [MFC], SetCenterVert
- CMFCToolBarComboBoxButton [MFC], SetDropDownHeight
- CMFCToolBarComboBoxButton [MFC], SetFlatMode
ms.assetid: 32fa39f7-8e4e-4f0a-a31d-7b540d969a6c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c7732d58c8e37683f670f6f13bb4df5f49e4ef24
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cmfctoolbarcomboboxbutton-class"></a>CMFCToolBarComboBoxButton – třída
Tlačítka panelu nástrojů, který obsahuje prvek pole se seznamem ( [CComboBox – třída](../../mfc/reference/ccombobox-class.md)).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCToolBarComboBoxButton : public CMFCToolBarButton  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCToolBarComboBoxButton::CMFCToolBarComboBoxButton](#cmfctoolbarcomboboxbutton)|Vytvoří `CMFCToolBarComboBoxButton`.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCToolBarComboBoxButton::AddItem](#additem)|Přidá položku na konec seznamu.|  
|[CMFCToolBarComboBoxButton::AddSortedItem](#addsorteditem)|Přidá položku do seznamu. Pořadí položek v seznamu je zadána `Compare`.|  
|[CMFCToolBarComboBoxButton::Compare](#compare)|Porovná dvě položky. Voláno k seřazení položek, které `AddSortedItems` přidá do seznamu.|  
|[CMFCToolBarComboBoxButton::CreateEdit](#createedit)|Vytvoří nový ovládací prvek úprav pro tlačítko pole se seznamem.|  
|[CMFCToolBarComboBoxButton::DeleteItem](#deleteitem)|Vymaže položku ze seznamu.|  
|[CMFCToolBarComboBoxButton::FindItem](#finditem)|Vrátí index položky, která obsahuje zadaný řetězec.|  
|[CMFCToolBarComboBoxButton::GetByCmd](#getbycmd)|Vrací ukazatel na tlačítko pole se seznamem s ID zadaný příkaz.|  
|[CMFCToolBarComboBoxButton::GetComboBox](#getcombobox)|Vrací ukazatel na prvek pole se seznamem, který je vložen do tlačítko pole se seznamem.|  
|[CMFCToolBarComboBoxButton::GetCount](#getcount)|Vrátí počet položek, které se seznamem se pole seznamu.|  
|[CMFCToolBarComboBoxButton::GetCountAll](#getcountall)|Vyhledá se seznamem se tlačítko pole, které má zadaný příkaz ID. Vrátí počet položek, které se seznamem se pole seznamu tohoto tlačítka.|  
|[CMFCToolBarComboBoxButton::GetCurSel](#getcursel)|Vrátí index vybrané položky se seznamem se pole seznamu.|  
|[CMFCToolBarComboBoxButton::GetCurSelAll](#getcurselall)|Vyhledá se seznamem se tlačítko pole, které má zadaný příkaz ID a vrátí index vybrané položky se seznamem se pole seznamu tohoto tlačítka.|  
|[CMFCToolBarComboBoxButton::GetEditCtrl](#geteditctrl)|Vrátí ovládací prvek úprav, který je součástí tlačítko pole se seznamem ukazatel.|  
|[CMFCToolBarComboBoxButton::GetItem](#getitem)|Vrátí řetězec, který je přidružen zadanému indexu v se seznamem se seznam pole.|  
|[CMFCToolBarComboBoxButton::GetItemAll](#getitemall)|Vyhledá se seznamem se tlačítko pole, které má zadaný příkaz ID a vrátí řetězec, který je přidružený index v seznamu pole se seznamem tohoto tlačítka.|  
|[CMFCToolBarComboBoxButton::GetItemData](#getitemdata)|Vrátí hodnotu 32-bit, která souvisí s zadaného indexu v se seznamem se pole seznamu.|  
|[CMFCToolBarComboBoxButton::GetItemDataAll](#getitemdataall)|Vyhledá se seznamem se pole tlačítka, který má zadaný příkaz ID a vrátí hodnotu 32-bit, který je přidružený index v seznamu pole se seznamem tohoto tlačítka.|  
|[CMFCToolBarComboBoxButton::GetItemDataPtrAll](#getitemdataptrall)|Vyhledá se seznamem se tlačítko pole, které má zadaný příkaz ID. Načte hodnotu 32-bit, která je spojená indexu v seznamu pole se seznamem tohoto tlačítka a vrátí hodnotu 32-bit jako ukazatel.|  
|[CMFCToolBarComboBoxButton::GetText](#gettext)|Vrátí text z ovládacího prvku pole se seznamem pro úpravy.|  
|[CMFCToolBarComboBoxButton::GetTextAll](#gettextall)|Vyhledá se seznamem se pole tlačítka, který má zadaný příkaz ID a vrátí text z ovládací prvek pro úpravy tohoto tlačítka.|  
|[CMFCToolBarComboBoxButton::IsCenterVert](#iscentervert)|Určuje, zda jsou tlačítka pole se seznamem v aplikaci na střed nebo v souladu s horní části panelu nástrojů.|  
|[CMFCToolBarComboBoxButton::IsFlatMode](#isflatmode)|Určuje, zda mají tlačítka pole se seznamem v aplikaci s plochým vzhledem.|  
|[CMFCToolBarComboBoxButton::RemoveAllItems](#removeallitems)|Odebere všechny položky ze seznamu, pole a ovládacích prvků pole se seznamem pro úpravy.|  
|[CMFCToolBarComboBoxButton::SelectItem](#selectitem)|Vybere v pole se seznamem podle jeho indexu, 32bitovou hodnotu nebo řetězec a upozorní ovládacího prvku pole se seznamem o výběr.|  
|[CMFCToolBarComboBoxButton::SelectItemAll](#selectitemall)|Vyhledá se seznamem se tlačítko pole, které má zadaný příkaz ID. Volání `SelectItem` vybrat položku do pole se seznamem tohoto tlačítka podle jeho řetězec, indexu nebo 32bitovou hodnotu.|  
|[CMFCToolBarComboBoxButton::SetCenterVert](#setcentervert)|Určuje, zda jsou tlačítka pole se seznamem v aplikaci svisle na střed nebo v souladu s horní části panelu nástrojů.|  
|[CMFCToolBarComboBoxButton::SetDropDownHeight](#setdropdownheight)|Nastaví výšku rozevíracího seznamu.|  
|[CMFCToolBarComboBoxButton::SetFlatMode](#setflatmode)|Určuje, jestli mají tlačítka pole se seznamem v aplikaci s plochým vzhledem.|  
  
## <a name="remarks"></a>Poznámky  
 Chcete-li přidat tlačítko pole se seznamem na panel nástrojů, postupujte takto:  
  
 1. Zarezervujte si pro tlačítko zástupný identifikátor ID prostředku v nadřazeném prostředku panelu nástrojů.  
  
 2. Vytvořit `CMFCToolBarComboBoxButton` objektu.  
  
 3. V popisovač zpráv, který zpracovává `AFX_WM_RESETTOOLBAR` zprávy, nahraďte zástupný tlačítko tlačítka Nová pole se seznamem pomocí [CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton).  
  
 Další informace najdete v tématu [návod: vložení ovládacích prvků na panely nástrojů](../../mfc/walkthrough-putting-controls-on-toolbars.md). Příklad tlačítka panelu nástrojů pole se seznamem najdete příklad projektu VisualStudioDemo.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak pomocí různých metod v nástroji `CMFCToolBarComboBoxButton` třídy. Tento příklad ukazuje, jak povolit polích upravit a pole se seznamem, nastaví svislou pozici polí se seznamem tlačítka pole v aplikaci, nastavit výška pole se seznamem při umístění, nastavte plochý vzhled tlačítek pole se seznamem v aplikaci a nastavit text do textového pole se seznamem se pro tlačítko pole. Tento fragment kódu je součástí [Visual Studio Demo-ukázka](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo#36](../../mfc/codesnippet/cpp/cmfctoolbarcomboboxbutton-class_1.cpp)]  
[!code-cpp[NVC_MFC_VisualStudioDemo#37](../../mfc/codesnippet/cpp/cmfctoolbarcomboboxbutton-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)  
  
 [CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxtoolbarcomboboxbutton.h  
  
##  <a name="additem"></a>CMFCToolBarComboBoxButton::AddItem  
 Připojí položku jedinečný pro pole se seznamem.  
  
```  
virtual INT_PTR AddItem(
    LPCTSTR lpszItem,  
    DWORD_PTR dwData=0);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`lpszItem`  
 Text položky pro přidání do seznamu.  
  
 [v]`dwData`  
 Data přidružená k položce přidat do seznamu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Index poslední položky v seznamu.  
  
### <a name="remarks"></a>Poznámky  
 Nepoužívejte tuto metodu, když je seřazen styl box seznamu.  
  
 Pokud text položky je již v seznamu, nová data se uloží spolu existující položku. Vyhledejte položku je malá a velká písmena.  
  
##  <a name="addsorteditem"></a>CMFCToolBarComboBoxButton::AddSortedItem  
 Přidá položku do pole se seznamem v pořadí, ve kterém je definována [porovnat](#compare) metoda.  
  
```  
virtual INT_PTR AddSortedItem(
    LPCTSTR lpszItem,  
    DWORD_PTR dwData=0);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`lpszItem`  
 Text položky pro přidání do seznamu.  
  
 [v]`dwData`  
 Data přidružená k položce přidat do seznamu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Index položky, která byla přidána do seznamu.  
  
### <a name="remarks"></a>Poznámky  
 Pomocí této funkce můžete přidat položky do seznamu v určitém pořadí.  
  
##  <a name="canbestretched"></a>CMFCToolBarComboBoxButton::CanBeStretched  
 Určuje, zda lze změnit velikost tlačítko pole se seznamem.  
  
```  
virtual BOOL CanBeStretched() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `TRUE`.  
  
##  <a name="cmfctoolbarcomboboxbutton"></a>CMFCToolBarComboBoxButton::CMFCToolBarComboBoxButton  
 Vytvoří [CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md) objektu.  
  
```  
CMFCToolBarComboBoxButton(
    UINT uiID,  
    int iImage,  
    DWORD dwStyle=CBS_DROPDOWNLIST,  
    int iWidth=0);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`uiID`  
 ID příkazu tlačítko Nový.  
  
 [v]`iImage`  
 Index obrázku přidružený tlačítko nové bitové kopie.  
  
 [v]`dwStyle`  
 Styl tlačítko Nový.  
  
 [v]`iWidth`  
 Šířka v pixelech tlačítko Nový.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí šířku je 150 pixelů.  
  
 Seznam styly tlačítek panelu nástrojů najdete v části [styly ovládacího prvku panel nástrojů](../../mfc/reference/toolbar-control-styles.md)  
  
##  <a name="cleardata"></a>CMFCToolBarComboBoxButton::ClearData  
 Uživatelem definované datové odstranění.  
  
```  
virtual void ClearData();
```  
  
### <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení tato metoda neprovede žádnou akci. Potlačí tuto metodu v odvozené třídě, pokud chcete odstranit všechna uživatelská data.  
  
##  <a name="compare"></a>CMFCToolBarComboBoxButton::Compare  
 Porovnává dva řetězce.  
  
```  
virtual int Compare(
    LPCTSTR lpszItem1,  
    LPCTSTR lpszItem2);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`lpszItem1`  
 První řetězec určený k porovnání  
  
 [v]`lpszItem2`  
 Druhý řetězec určený k porovnání  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota, která označuje malá a velká písmena lexicographic vztah mezi řetězce. Následující tabulka uvádí možné hodnoty:  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|\<0|První řetězec je menší než druhý.|  
|0|První řetězec rovná druhé.|  
|>0|První řetězec je větší než druhý.|  
  
### <a name="remarks"></a>Poznámky  
 Potlačí tuto metodu, chcete-li změnit řazení položky v seznamu.  
  
 Porovnání rozlišuje velká a malá písmena.  
  
 Tato metoda je volána pouze z [AddSortedItem](#addsorteditem) metoda.  
  
##  <a name="copyfrom"></a>CMFCToolBarComboBoxButton::CopyFrom  
 Zkopíruje stav zadaného `CMFCToolBarComboBoxButton` jako aktuální objekt.  
  
```  
virtual void CopyFrom(const CMFCToolBarButton& src);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`src`  
 Zdroj `CMFCToolBarComboBoxButton` objektu.  
  
##  <a name="createcombo"></a>CMFCToolBarComboBoxButton::CreateCombo  
 Vytvoří nové pole se seznamem pro tlačítko pole se seznamem.  
  
```  
virtual CComboBox* CreateCombo(
    CWnd* pWndParent,  
    const CRect& rect);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pWndParent`  
 Ukazatel do nadřazeného okna tlačítka.  
  
 [v]`rect`  
 Ohraničující obdélník pole se seznamem.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na nové pole se seznamem, pokud metoda byla úspěšná. v opačném `NULL`.  
  
##  <a name="createedit"></a>CMFCToolBarComboBoxButton::CreateEdit  
 Vytvoří nové textové pole pro tlačítko pole se seznamem.  
  
```  
virtual CMFCToolBarComboBoxEdit* CreateEdit(
    CWnd* pWndParent,  
    const CRect& rect,  
    DWORD dwEditStyle);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pWndParent`  
 Ukazatel do nadřazeného okna tlačítka.  
  
 [v]`rect`  
 Ohraničující obdélník nové textové pole.  
  
 [v]`dwEditStyle`  
 Ovládací prvek styl nové textové pole.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na nové textové pole, pokud metoda byla úspěšná. v opačném `NULL`.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda volá framework při vytváření nové textové pole pro tlačítko pole se seznamem. Potlačí tuto metodu, chcete-li změnit jak [CMFCToolBarComboBoxEdit](../../mfc/reference/cmfctoolbarcomboboxedit-class.md) je vytvořena.  
  
##  <a name="deleteitem"></a>CMFCToolBarComboBoxButton::DeleteItem  
 Odstraní určenou položku z pole se seznamem.  
  
```  
BOOL DeleteItem(int iIndex);  
BOOL DeleteItem(DWORD_PTR dwData);  
  BOOL DeleteItem(LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`iIndex`  
 Index založený na nule položky pro odstranění.  
  
 [v]`dwData`  
 Data související s položka, která má být odstraněna.  
  
 [v]`lpszText`  
 Text položky pro odstranění. Pokud je vybráno více položek se stejný text, první položku, je odstranit.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud byla položka nachází a byla úspěšně odstraněna; v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="duplicatedata"></a>CMFCToolBarComboBoxButton::DuplicateData  
 Uživatelem definované datové duplicitní položky.  
  
```  
virtual void DuplicateData();
```  
  
### <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení tato metoda neprovede žádnou akci. Potlačí tuto metodu v odvozené třídě, pokud chcete zkopírovat všechna uživatelská data.  
  
##  <a name="enablewindow"></a>CMFCToolBarComboBoxButton::EnableWindow  
 Povolí nebo zakáže úpravy a pole se seznamem polí.  
  
```  
virtual void EnableWindow(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`bEnable`  
 `TRUE`Povolit úpravy a pole se seznamem polí; `FALSE` zakázat polích upravit a pole se seznamem.  
  
### <a name="remarks"></a>Poznámky  
 Pokud je zakázáno, ovládací prvky se nemůže stát aktivní a nemůže přijímat vstup uživatele.  
  
##  <a name="exporttomenubutton"></a>CMFCToolBarComboBoxButton::ExportToMenuButton  
 ID kopie řetězec z tabulky řetězec aplikace tak, aby zadaný nabídky pomocí příkazu tlačítko pole se seznamem.  
  
```  
virtual BOOL ExportToMenuButton(CMFCToolBarMenuButton& menuButton) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [out]`menuButton`  
 Odkaz na tlačítka s nabídkou.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vždy `TRUE`.  
  
##  <a name="finditem"></a>CMFCToolBarComboBoxButton::FindItem  
 Vrátí index první položky v seznamu, který obsahuje zadaný řetězec.  
  
```  
int FindItem(LPCTSTR lpszText) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [v]`lpszText`  
 Text, který chcete vyhledat v rozevíracím seznamu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Index položky; nebo `CB_ERR` Pokud položka není nalezena.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getbycmd"></a>CMFCToolBarComboBoxButton::GetByCmd  
 Získá ukazatel na tlačítko pole se seznamem, který má zadaný příkaz ID.  
  
```  
static CMFCToolBarComboBoxButton* GetByCmd(
    UINT uiCmd,  
    BOOL bIsFocus=FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`uiCmd`  
 ID příkazu tlačítka pole se seznamem.  
  
 [v]`bIsFocus`  
 `TRUE`Chcete-li hledat pouze zaměřuje tlačítka; `FALSE` k vyhledání všech tlačítek.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na tlačítko pole se seznamem; nebo `NULL` Pokud tlačítko nebyl nalezen.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getcombobox"></a>CMFCToolBarComboBoxButton::GetComboBox  
 Vrací ukazatel na pole se seznamem se seznamem se tlačítko pole.  
  
```  
CComboBox* GetComboBox() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel [CComboBox – třída](../../mfc/reference/ccombobox-class.md) objektu, pokud metoda byla úspěšná, jinak hodnota `NULL`.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getcontextmenuid"></a>CMFCToolBarComboBoxButton::GetContextMenuID  
 Získá ID prostředku místní nabídky pro tlačítka pole se seznamem.  
  
```  
UINT GetContextMenuID();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 ID místní nabídky prostředku.  
  
##  <a name="getcount"></a>CMFCToolBarComboBoxButton::GetCount  
 Vrátí počet položek v seznamu.  
  
```  
INT_PTR GetCount() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet položek v seznamu.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getcountall"></a>CMFCToolBarComboBoxButton::GetCountAll  
 Získá počet položek v seznamu tlačítka pole se seznamem, který má zadaný příkaz ID.  
  
```  
static int GetCountAll(UINT uiCmd);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`uiCmd`  
 ID příkazu tlačítka pole se seznamem.  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet položek v seznamu; v opačném `CB_ERR` Pokud tlačítko pole se seznamem nebylo nalezeno.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getcursel"></a>CMFCToolBarComboBoxButton::GetCurSel  
 Získá index aktuálně vybrané položky v seznamu.  
  
```  
int GetCurSel() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Index aktuálně vybrané položky v seznamu; nebo `CB_ERR` Pokud není vybrána žádná položka.  
  
### <a name="remarks"></a>Poznámky  
 Indexu pole se seznamem je počítáno od nuly.  
  
##  <a name="getcurselall"></a>CMFCToolBarComboBoxButton::GetCurSelAll  
 Vrátí index aktuálně vybrané položky v seznamu pole se seznamem tlačítko pole, které má zadaný příkaz ID.  
  
```  
static int GetCurSelAll(UINT uiCmd);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`uiCmd`  
 ID příkazu tlačítka pole se seznamem.  
  
### <a name="return-value"></a>Návratová hodnota  
 Index aktuálně vybrané položky v seznamu; v opačném `CB_ERR` Pokud není vybrána žádná položka nebo tlačítko pole se seznamem nebyl nalezen.  
  
### <a name="remarks"></a>Poznámky  
 Indexu pole se seznamem je počítáno od nuly.  
  
##  <a name="geteditctrl"></a>CMFCToolBarComboBoxButton::GetEditCtrl  
 Vrací ukazatel na textové pole se seznamem se tlačítko pole.  
  
```  
virtual CEdit* GetEditCtrl();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na textové pole, pokud metoda byla úspěšná. v opačném `NULL`.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="gethwnd"></a>CMFCToolBarComboBoxButton::GetHwnd  
 Vrátí popisovač okna pro pole se seznamem.  
  
```  
virtual HWND GetHwnd();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Popisovač okna, nebo `NULL` Pokud pole se seznamem není spojen s objektem okna.  
  
##  <a name="getitem"></a>CMFCToolBarComboBoxButton::GetItem  
 Vrátí řetězec přidružený k položku na zadaný index v poli seznamu.  
  
```  
LPCTSTR GetItem(int iIndex=-1) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [v]`iIndex`  
 Index položky v seznamu nule.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na řetězec, který je přidružená k položce; v opačném `NULL` Pokud parametr indexu je neplatná, nebo pokud parametr indexu -1 a v seznamu je vybrána žádná položka.  
  
### <a name="remarks"></a>Poznámky  
 Index parametru-1 vrátí řetězec aktuálně vybrané položky.  
  
##  <a name="getitemall"></a>CMFCToolBarComboBoxButton::GetItemAll  
 Vrátí řetězec přidružený k položku na zadaný index v poli seznamu tlačítka pole se seznamem, který má zadaný příkaz ID.  
  
```  
static LPCTSTR GetItemAll(
    UINT uiCmd,  
    int iIndex=-1);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`uiCmd`  
 ID příkazu tlačítka pole se seznamem.  
  
 [v]`iIndex`  
 Index založený na nule položky v seznamu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na položky řetězec, pokud metoda byla úspěšná. jinak `NULL` Pokud index není platný, tlačítko pole se seznamem není nalezen, nebo pokud index, je -1 a není vybrána žádná položka v seznamu.  
  
### <a name="remarks"></a>Poznámky  
 Hodnota indexu -1 vrátí řetězec aktuálně vybrané položky.  
  
##  <a name="getitemdata"></a>CMFCToolBarComboBoxButton::GetItemData  
 Vrací data související s položky na konkrétní indexu v seznamu.  
  
```  
DWORD_PTR GetItemData(int iIndex=-1) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [v]`iIndex`  
 Index založený na nule položky v seznamu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Data přidružená k položce; nebo 0, pokud položka neexistuje.  
  
### <a name="remarks"></a>Poznámky  
 Index parametru-1 vrací data související s aktuálně vybrané položky.  
  
##  <a name="getitemdataall"></a>CMFCToolBarComboBoxButton::GetItemDataAll  
 Vrátí data související s položky na konkrétní indexu v seznamu tlačítka pole se seznamem, které má konkrétní příkaz ID.  
  
```  
static DWORD_PTR GetItemDataAll(
    UINT uiCmd,  
    int iIndex=-1);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`uiCmd`  
 ID příkazu tlačítka pole se seznamem.  
  
 [v]`iIndex`  
 Index založený na nule položky v seznamu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Data související s položkou, pokud metoda byla úspěšná. jinak hodnota 0, pokud zadaný index není platný nebo CB_ERR Pokud tlačítko pole se seznamem se nenašla.  
  
### <a name="remarks"></a>Poznámky  
 Index parametru-1 vrací data související s aktuálně vybrané položky.  
  
##  <a name="getitemdataptrall"></a>CMFCToolBarComboBoxButton::GetItemDataPtrAll  
 Vrátí data související s položky na konkrétní indexu v seznamu tlačítka pole se seznamem, které má konkrétní příkaz ID. Tato data jsou vrácena jako ukazatel.  
  
```  
static void* GetItemDataPtrAll(
    UINT uiCmd,  
    int iIndex=-1);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`uiCmd`  
 ID příkazu, který se zobrazí tlačítko pro pole se seznamem.  
  
 [v]`iIndex`  
 Index založený na nule položky v seznamu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel přidružené k položce, pokud metoda byla úspěšná. jinak hodnota -1, pokud dojde k chybě, nebo `NULL` Pokud tlačítko pole se seznamem nebylo nalezeno.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getprompt"></a>CMFCToolBarComboBoxButton::GetPrompt  
 Vrátí text výzvy pro se seznamem se tlačítko pole.  
  
```  
virtual CString GetPrompt() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Výzva řetězec.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda není aktuálně implementována.  
  
##  <a name="gettext"></a>CMFCToolBarComboBoxButton::GetText  
 Načte text do textového pole.  
  
```  
LPCTSTR GetText() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Text do textového pole.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="gettextall"></a>CMFCToolBarComboBoxButton::GetTextAll  
 Načte text do textového pole pro tlačítko pole se seznamem, který má zadaný příkaz ID.  
  
```  
static LPCTSTR GetTextAll(UINT uiCmd);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`uiCmd`  
 ID příkazu tlačítka pole s konkrétní pole se seznamem.  
  
### <a name="return-value"></a>Návratová hodnota  
 Text do textového pole, pokud metoda byla úspěšná. v opačném `NULL`.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="hasfocus"></a>CMFCToolBarComboBoxButton::HasFocus  
 Určuje, zda pole se seznamem právě aktivní.  
  
```  
virtual BOOL HasFocus() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud pole se seznamem má právě fokus; v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda také vrátí hodnotu `TRUE` žádné podřízeného okna pole se seznamem má právě fokus.  
  
##  <a name="iscentervert"></a>CMFCToolBarComboBoxButton::IsCenterVert  
 Vrátí pozice ve svislém směru tlačítek pole se seznamem v aplikaci.  
  
```  
static BOOL IsCenterVert();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud se na tlačítka; `FALSE` Pokud jsou v souladu tlačítek v horní části.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="isflatmode"></a>CMFCToolBarComboBoxButton::IsFlatMode  
 Vrátí plochý vzhled tlačítek pole se seznamem v aplikaci.  
  
```  
static BOOL IsFlatMode();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud máte tlačítka plochý; v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Je výchozí styl ploché pro tlačítka pole se seznamem`FALSE.`  
  
##  <a name="isownerof"></a>CMFCToolBarComboBoxButton::IsOwnerOf  
 Určuje, zda je zadaný popisovač přidružený tlačítko pole se seznamem nebo jednu z jejích podřízených.  
  
```  
virtual BOOL IsOwnerOf(HWND hwnd);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`hwnd`  
 Popisovač okna.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud popisovač assocated s tlačítko pole se seznamem nebo jednu z jejích podřízených; v opačném `FALSE`.  
  
##  <a name="isribbonbutton"></a>CMFCToolBarComboBoxButton::IsRibbonButton  
 Určuje, zda tlačítko pole se seznamem se nachází na panelu pásu karet.  
  
```  
BOOL IsRibbonButton() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vždy `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení, tato metoda vždy vrátí `FALSE`, což znamená, že se seznamem se tlačítko pole se nikdy zobrazí na panelu pásu karet.  
  
##  <a name="iswindowvisible"></a>CMFCToolBarComboBoxButton::IsWindowVisible  
 Vrátí stav viditelnosti se seznamem se tlačítko pole.  
  
```  
virtual BOOL IsWindowVisible();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Stav viditelnosti tlačítka pole se seznamem.  
  
##  <a name="notifycommand"></a>CMFCToolBarComboBoxButton::NotifyCommand  
 Určuje, zda zprávu zpracuje tlačítko pole se seznamem.  
  
```  
virtual BOOL NotifyCommand(int iNotifyCode);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`iNotifyCode`  
 Oznámení, které souvisí s příkaz.  
  
### <a name="return-value"></a>Návratová hodnota  
 Jestli zprávu zpracuje tlačítko pole se seznamem.  
  
##  <a name="onaddtocustomizepage"></a>CMFCToolBarComboBoxButton::OnAddToCustomizePage  
 Voláno rámcem, když je tlačítko přidán do **přizpůsobit** dialogové okno.  
  
```  
virtual void OnAddToCustomizePage();
```  
  
##  <a name="oncalculatesize"></a>CMFCToolBarComboBoxButton::OnCalculateSize  
 Voláno rámcem vypočítat velikost tlačítka.  
  
```  
virtual SIZE OnCalculateSize(
    CDC* pDC,  
    const CSize& sizeDefault,  
    BOOL bHorz);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pDC`  
 Kontext zařízení, který se zobrazí tlačítko pole se seznamem.  
  
 [v]`sizeDefault`  
 Výchozí velikost tlačítko pole se seznamem.  
  
 [v]`bHorz`  
 Stav ukotvení panelu nástrojů nadřazené. `TRUE`Když se panelu nástrojů ukotveno vodorovně a `FALSE` když panelu nástrojů ukotveno svisle.  
  
### <a name="return-value"></a>Návratová hodnota  
 A `SIZE` struktura, která obsahuje dimenze tlačítko pole se seznamem v pixelech.  
  
##  <a name="onchangeparentwnd"></a>CMFCToolBarComboBoxButton::OnChangeParentWnd  
 Voláno rámcem při tlačítko pole se seznamem se vloží do nového panelu nástrojů.  
  
```  
virtual void OnChangeParentWnd(CWnd* pWndParent);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pWndParent`  
 Ukazatel na panelu nástrojů nové nadřazené.  
  
##  <a name="onclick"></a>CMFCToolBarComboBoxButton::OnClick  
 Voláno rámcem, když uživatel klikne na tlačítko pole se seznamem.  
  
```  
virtual BOOL OnClick(
    CWnd* pWnd,  
    BOOL bDelay = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pWnd`  
 Ukazatel do nadřazeného okna tlačítka pole se seznamem.  
  
 [v]`bDelay`  
 Vyhrazené pro použití v odvozené třídě.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud metoda zpracovává událost. v opačném `FALSE`.  
  
##  <a name="onctlcolor"></a>CMFCToolBarComboBoxButton::OnCtlColor  
 Voláno rámcem, když uživatel změní barvu nadřazené nástrojů nastavit barvu tlačítko pole se seznamem se.  
  
```  
virtual HBRUSH OnCtlColor(
    CDC* pDC,  
    UINT nCtlColor);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pDC`  
 Kontext zařízení, který se zobrazí tlačítko pole se seznamem.  
  
 [v]`nCtlColor`  
 Nepoužívá se.  
  
### <a name="return-value"></a>Návratová hodnota  
 Popisovač štětce, který používá rozhraní k vyplnění pozadí tlačítko pole se seznamem.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda také nastaví barvu textu tlačítka pole se seznamem.  
  
##  <a name="ondraw"></a>CMFCToolBarComboBoxButton::OnDraw  
 Voláno rámcem k vykreslení tlačítko pole se seznamem pomocí zadané styly a možnosti.  
  
```  
virtual void OnDraw(
    CDC* pDC,  
    const CRect& rect,  
    CMFCToolBarImages* pImages,  
    BOOL bHorz = TRUE,  
    BOOL bCustomizeMode = FALSE,  
    BOOL bHighlight = FALSE,  
    BOOL bDrawBorder = TRUE,  
    BOOL bGrayDisabledButtons = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`Pdc`  
 Kontext zařízení, který se zobrazí tlačítko.  
  
 [v]`rect`  
 Ohraničující obdélník tlačítko.  
  
 [v]`pImages`  
 Kolekce bitové kopie, který je přidružen tlačítko.  
  
 [v]`bHorz`  
 Stav ukotvení panelu nástrojů nadřazené. `TRUE`Když se panelu nástrojů ukotveno vodorovně a `FALSE` když panelu nástrojů ukotveno svisle.  
  
 [v]`bCustomizeMode`  
 Zda je aplikace v režimu vlastní nastavení.  
  
 [v]`bHighlight`  
 Určuje, zda se k vykreslení tlačítko pole se seznamem zvýrazněná.  
  
 [v]`bDrawBorder`  
 Určuje, zda se k vykreslení tlačítka pole se seznamem s ohraničení.  
  
 [v]`bGrayDisabledButtons`  
 `TRUE`Kreslení šedou barvou zakázané tlačítka; `FALSE` používat zakázáno Image kolekce.  
  
##  <a name="ondrawoncustomizelist"></a>CMFCToolBarComboBoxButton::OnDrawOnCustomizeList  
 Voláno rámcem kreslení tlačítko pole se seznamem **příkazy** podokně **přizpůsobit** dialogové okno.  
  
```  
virtual int OnDrawOnCustomizeList(
    CDC* pDC,  
    const CRect& rect,  
    BOOL bSelected);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pDC`  
 Kontext zařízení, který se zobrazí tlačítko pole se seznamem.  
  
 [v]`rect`  
 Ohraničující obdélník tlačítko pole se seznamem.  
  
 [v]`bSelected`  
 `TRUE`pole se seznamem se tlačítko bude vybrána. v opačném `FALSE`.  
  
### <a name="return-value"></a>Návratová hodnota  
 Šířka v pixelech tlačítko pole se seznamem.  
  
##  <a name="onglobalfontschanged"></a>CMFCToolBarComboBoxButton::OnGlobalFontsChanged  
 Voláno rámcem nastavit písma tlačítko pole se seznamem se při změně písma aplikace.  
  
```  
virtual void OnGlobalFontsChanged();
```  
  
##  <a name="onmove"></a>CMFCToolBarComboBoxButton::OnMove  
 Voláno rámcem a změňte umístění tlačítka pole se seznamem, pokud se přesune panel nástrojů nadřazené.  
  
```  
virtual void OnMove();
```  
  
##  <a name="onshow"></a>CMFCToolBarComboBoxButton::OnShow  
 Voláno rámcem při tlačítko pole se seznamem je skrytý nebo zobrazení.  
  
```  
virtual void OnShow(BOOL bShow);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`bShow`  
 Určuje, zda skrytí nebo zobrazení tlačítka pole se seznamem.  
  
##  <a name="onsize"></a>CMFCToolBarComboBoxButton::OnSize  
 Voláno rámcem ke změně velikosti tlačítka pole se seznamem, když se změní velikost panelu nástrojů nadřazené.  
  
```  
virtual void OnSize(int iSize);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`iSize`  
 Nové šířka tlačítko pole se seznamem.  
  
##  <a name="onupdatetooltip"></a>CMFCToolBarComboBoxButton::OnUpdateToolTip  
 Voláno rámcem, když uživatel změní popis tlačítka pro tlačítko pole se seznamem.  
  
```  
virtual BOOL OnUpdateToolTip(
    CWnd* pWndParent,  
    int iButtonIndex,  
    CToolTipCtrl& wndToolTip,  
    CString& str);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pWndParent`  
 Ukazatel do nadřazeného okna pro tlačítko pole se seznamem.  
  
 [v]`iButtonIndex`  
 ID tlačítko pole se seznamem.  
  
 [v]`wndToolTip`  
 Nástroj popisek, který chcete přidružit k tlačítko pole se seznamem.  
  
 [v]`str`  
 Text popisu nástroje.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud metoda zpracovává událost. v opačném `FALSE`.  
  
##  <a name="removeallitems"></a>CMFCToolBarComboBoxButton::RemoveAllItems  
 Odstraní všechny položky ze seznamu a úpravy polí.  
  
```  
void RemoveAllItems();
```  
  
### <a name="remarks"></a>Poznámky  
 Odebere všechny položky ze seznamu, pole a ovládacích prvků pole se seznamem pro úpravy.  
  
##  <a name="selectitem"></a>CMFCToolBarComboBoxButton::SelectItem  
 Vyberte položku v seznamu.  
  
```  
BOOL SelectItem(
    int iIndex,  
    BOOL bNotify=TRUE);  
  
BOOL SelectItem(DWORD_PTR dwData);  
BOOL SelectItem(LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`iIndex`  
 Index založený na nule položky v seznamu.  
  
 [v]`bNotify`  
 `TRUE`Upozornit na tlačítko pole se seznamem výběru; v opačném případě `FALSE`.  
  
 [v]`dwData`  
 Data přidružená k položce v seznamu.  
  
 [v]`lpszText`  
 Text položky v seznamu.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud metoda byla úspěšná. v opačném případě `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="selectitemall"></a>CMFCToolBarComboBoxButton::SelectItemAll  
 Vybere položku v seznamu tlačítka pole se seznamem, který má zadaný příkaz ID.  
  
```  
static BOOL SelectItemAll(
    UINT uiCmd,  
    int iIndex);

 
static BOOL SelectItemAll(
    UINT uiCmd,  
    DWORD_PTR dwData);

 
static BOOL SelectItemAll(
    UINT uiCmd,  
    LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`uiCmd`  
 ID příkazu tlačítka pole se seznamem, které obsahuje pole se seznamem.  
  
 [v]`iIndex`  
 Index založený na nule položky v seznamu. Hodnota -1 Odebere všechny aktuální výběr v seznamu a vymaže textové pole.  
  
 [v]`dwData`  
 Data, která položky v seznamu.  
  
 [v]`lpszText`  
 Text položky v seznamu.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud metoda byla úspěšná. v opačném případě `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="serialize"></a>CMFCToolBarComboBoxButton::Serialize  
 Čte tento objekt z archivu nebo zapíše ho do archivu.  
  
```  
virtual void Serialize(CArchive& ar);
```  
  
### <a name="parameters"></a>Parametry  
 [ve out]`ar`  
 `CArchive` Objektu k serializaci.  
  
### <a name="remarks"></a>Poznámky  
 Nastavení v `CArchive` objekt určit, zda tato metoda čte nebo zapisuje do archivu.  
  
##  <a name="setaccdata"></a>CMFCToolBarComboBoxButton::SetACCData  
 Naplní zadaný `CAccessibilityData` objekt pomocí usnadnění data z tlačítko pole se seznamem.  
  
```  
virtual BOOL SetACCData(
    CWnd* pParent,  
    CAccessibilityData& data);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pParent`  
 Nadřazené okno tlačítka pole se seznamem.  
  
 [out]`data`  
 A `CAccessibilityData` objekt, který přijímá data usnadnění z tlačítko pole se seznamem.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud metoda byla úspěšná. v opačném případě `FALSE`.  
  
##  <a name="setcentervert"></a>CMFCToolBarComboBoxButton::SetCenterVert  
 Nastaví pozice ve svislém směru tlačítek pole se seznamem v aplikaci.  
  
```  
static void SetCenterVert(BOOL bCenterVert=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`bCenterVert`  
 `TRUE`na střed tlačítko pole se seznamem na panelu nástrojů; `FALSE` Chcete-li zarovnat tlačítko pole se seznamem do horní části panelu nástrojů.  
  
### <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení je zarovnán tlačítka pole se seznamem na začátek.  
  
##  <a name="setcontextmenuid"></a>CMFCToolBarComboBoxButton::SetContextMenuID  
 Nastaví ID prostředku místní nabídky se seznamem se tlačítko pole.  
  
```  
void SetContextMenuID(UINT uiResID);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`uiResID`  
 ID místní nabídky prostředku.  
  
##  <a name="setdropdownheight"></a>CMFCToolBarComboBoxButton::SetDropDownHeight  
 Výška pole se seznamem nastaví při umístění.  
  
```  
void SetDropDownHeight(int nHeight);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`nHeight`  
 Výška v pixelech pole se seznamem.  
  
### <a name="remarks"></a>Poznámky  
 Výška výchozí je 150 pixelů.  
  
##  <a name="setflatmode"></a>CMFCToolBarComboBoxButton::SetFlatMode  
 Nastaví plochý vzhled tlačítek pole se seznamem v aplikaci.  
  
```  
static void SetFlatMode(BOOL bFlat=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`bFlat`  
 `TRUE`pro plochý vzhled; v opačném případě `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí styl ploché pro tlačítka pole se seznamem je `FALSE`.  
  
##  <a name="setstyle"></a>CMFCToolBarComboBoxButton::SetStyle  
 Nastaví zadaný styl pro se seznamem se tlačítko pole nebo ho překreslí ovládacího prvku, jestli není zakázaný.  
  
```  
virtual void SetStyle(UINT nStyle);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`nStyle`  
 Bitová kombinace (nebo) stylů panelu nástrojů.  
  
### <a name="remarks"></a>Poznámky  
 Seznam styly tlačítek panelu nástrojů najdete v části [styly ovládacího prvku panel nástrojů](../../mfc/reference/toolbar-control-styles.md)  
  
##  <a name="settext"></a>CMFCToolBarComboBoxButton::SetText  
 Nastaví text do textového pole se seznamem se pro tlačítko pole.  
  
```  
void SetText(LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`lpszText`  
 Ukazatel na řetězec, který obsahuje text pro textové pole.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBarButton – třída](../../mfc/reference/cmfctoolbarbutton-class.md)   
 [CComboBox – třída](../../mfc/reference/ccombobox-class.md)   
 [CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)   
 [Návod: Umístění ovládacích prvků na panely nástrojů](../../mfc/walkthrough-putting-controls-on-toolbars.md)



