---
title: Cmfctoolbarcomboboxbutton – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ffb17f8f38e83399ec32b792338f818cc06215dc
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45703758"
---
# <a name="cmfctoolbarcomboboxbutton-class"></a>Cmfctoolbarcomboboxbutton – třída
Tlačítka panelu nástrojů obsahující ovládací prvek pole se seznamem ( [CComboBox – třída](../../mfc/reference/ccombobox-class.md)).  
  
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
|[CMFCToolBarComboBoxButton::AddItem](#additem)|Přidá položku do konce seznamu pole se seznamem.|  
|[CMFCToolBarComboBoxButton::AddSortedItem](#addsorteditem)|Přidá položku do seznamu pole se seznamem. Pořadí položek v seznamu je určená `Compare`.|  
|[CMFCToolBarComboBoxButton::Compare](#compare)|Porovná dvě položky. Volána k řazení položek, které `AddSortedItems` přidá do seznamu pole se seznamem.|  
|[CMFCToolBarComboBoxButton::CreateEdit](#createedit)|Vytvoří nový ovládací prvek úprav pro tlačítko pole se seznamem.|  
|[CMFCToolBarComboBoxButton::DeleteItem](#deleteitem)|Odstraní položku ze seznamu pole se seznamem.|  
|[CMFCToolBarComboBoxButton::FindItem](#finditem)|Vrátí index položky, která obsahuje zadaný řetězec.|  
|[CMFCToolBarComboBoxButton::GetByCmd](#getbycmd)|Vrací ukazatel na tlačítka pole se seznamem s ID zadaného příkazu.|  
|[CMFCToolBarComboBoxButton::GetComboBox](#getcombobox)|Vrací ukazatel na prvek pole se seznamem, který je součástí tlačítko pole se seznamem.|  
|[CMFCToolBarComboBoxButton::GetCount](#getcount)|Vrátí počet položek, které pole se seznamem seznamu pole.|  
|[CMFCToolBarComboBoxButton::GetCountAll](#getcountall)|Vyhledá pole se seznamem, tlačítka pole, která má ID zadaného příkazu. Vrátí počet položek, které pole se seznamem pole seznamu toto tlačítko.|  
|[CMFCToolBarComboBoxButton::GetCurSel](#getcursel)|Vrátí index vybrané položky pole se seznamem seznamu pole.|  
|[CMFCToolBarComboBoxButton::GetCurSelAll](#getcurselall)|Vyhledá pole se seznamem, tlačítka pole, která má ID zadaného příkazu a vrátí index vybrané položky pole se seznamem pole seznamu toto tlačítko.|  
|[CMFCToolBarComboBoxButton::GetEditCtrl](#geteditctrl)|Vrací ukazatel na ovládací prvek pro úpravy, které jsou součástí tlačítko pole se seznamem.|  
|[CMFCToolBarComboBoxButton::GetItem](#getitem)|Vrátí řetězec, který je přidružený k zadanému indexu pole se seznamem seznamu pole.|  
|[CMFCToolBarComboBoxButton::GetItemAll](#getitemall)|Vyhledá pole se seznamem, tlačítka pole, která má ID zadaného příkazu a vrátí řetězec, který je přidružený k indexu v seznamu pole se seznamem toto tlačítko.|  
|[CMFCToolBarComboBoxButton::GetItemData](#getitemdata)|Vrátí hodnotu 32-bit, který je přidružený k zadanému indexu pole se seznamem seznamu pole.|  
|[CMFCToolBarComboBoxButton::GetItemDataAll](#getitemdataall)|Vyhledá pole se seznamem, tlačítka pole, která má ID zadaného příkazu a vrátí hodnotu 32-bit, který je spojen s indexem v seznamu pole se seznamem toto tlačítko.|  
|[CMFCToolBarComboBoxButton::GetItemDataPtrAll](#getitemdataptrall)|Vyhledá pole se seznamem, tlačítka pole, která má ID zadaného příkazu. Načte 32bitovou hodnotu, která je spojená indexu v seznamu pole se seznamem tohoto tlačítka a vrátí hodnotu 32-bit jako ukazatel.|  
|[CMFCToolBarComboBoxButton::GetText](#gettext)|Vrátí text z ovládacího prvku pro úpravy pole se seznamem.|  
|[CMFCToolBarComboBoxButton::GetTextAll](#gettextall)|Vyhledá pole se seznamem, tlačítka pole, která má ID zadaného příkazu a vrátí text z ovládací prvek pro úpravy tohoto tlačítka.|  
|[CMFCToolBarComboBoxButton::IsCenterVert](#iscentervert)|Určuje, jestli jsou tlačítka pole se seznamem v aplikaci na střed nebo v souladu s horním panelu nástrojů.|  
|[CMFCToolBarComboBoxButton::IsFlatMode](#isflatmode)|Určuje, zda mají tlačítka pole se seznamem v aplikaci jako plochá.|  
|[CMFCToolBarComboBoxButton::RemoveAllItems](#removeallitems)|Odebere všechny položky v seznamu pole a upravit ovládací prvek pole se seznamem.|  
|[CMFCToolBarComboBoxButton::SelectItem](#selectitem)|Vybere položku v poli se seznamem podle jeho index, 32bitová hodnota nebo řetězec a upozorní ovládací prvek pole se seznamem o výběru.|  
|[CMFCToolBarComboBoxButton::SelectItemAll](#selectitemall)|Vyhledá pole se seznamem, tlačítka pole, která má ID zadaného příkazu. Volání `SelectItem` vybrat položku v poli se seznamem tohoto tlačítka podle jeho string, index a 32bitová hodnota.|  
|[CMFCToolBarComboBoxButton::SetCenterVert](#setcentervert)|Určuje, zda jsou tlačítka pole se seznamem v aplikaci svisle na střed nebo v souladu s horním panelu nástrojů.|  
|[CMFCToolBarComboBoxButton::SetDropDownHeight](#setdropdownheight)|Nastaví výšku pole rozevíracího seznamu.|  
|[CMFCToolBarComboBoxButton::SetFlatMode](#setflatmode)|Určuje, zda tlačítka pole se seznamem v aplikaci jako plochá.|  
  
## <a name="remarks"></a>Poznámky  
 Chcete-li přidat tlačítko pole se seznamem na panel nástrojů, postupujte takto:  
  
 1. Zarezervujte si pro tlačítko zástupný identifikátor ID prostředku v nadřazeném prostředku panelu nástrojů.  
  
 2. Vytvoření `CMFCToolBarComboBoxButton` objektu.  
  
 3. V popisovači zpráv, která zpracovává zprávu AFX_WM_RESETTOOLBAR, nahraďte zástupné tlačítko Nová tlačítka pole se seznamem pomocí [CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton).  
  
 Další informace najdete v tématu [návod: vložení ovládacích prvků na panely nástrojů](../../mfc/walkthrough-putting-controls-on-toolbars.md). Příklad tlačítka pole se seznamem viz příklad projektu VisualStudioDemo.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak použít různé metody v `CMFCToolBarComboBoxButton` třídy. Tento příklad ukazuje, jak povolit úpravy a pole se seznamem polí, nastaví svislou pozici polí se seznamem, tlačítka pole v aplikaci, nastavení výšky pole se seznamem, když se rozbalil, nastavte plochý vzhled tlačítka pole se seznamem v aplikaci a nastavit text podle pole pro úpravy pole se seznamem tlačítko pole. Tento fragment kódu je součástí [Visual Studio demonstrační ukázka](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo#36](../../mfc/codesnippet/cpp/cmfctoolbarcomboboxbutton-class_1.cpp)]  
[!code-cpp[NVC_MFC_VisualStudioDemo#37](../../mfc/codesnippet/cpp/cmfctoolbarcomboboxbutton-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [Třídy CObject](../../mfc/reference/cobject-class.md)  
  
 [Cmfctoolbarbutton –](../../mfc/reference/cmfctoolbarbutton-class.md)  
  
 [Cmfctoolbarcomboboxbutton –](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxtoolbarcomboboxbutton.h  
  
##  <a name="additem"></a>  CMFCToolBarComboBoxButton::AddItem  
 Připojí jedinečný položky pole se seznamem.  
  
```  
virtual INT_PTR AddItem(
    LPCTSTR lpszItem,  
    DWORD_PTR dwData=0);
```  
  
### <a name="parameters"></a>Parametry  
*lpszItem*<br/>
[in] Text položky pro přidání do seznamu.  
  
*dwData*<br/>
[in] Data přidružená k položky pro přidání do seznamu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Index poslední položky v seznamu.  
  
### <a name="remarks"></a>Poznámky  
 Nepoužívejte tuto metodu při řazení seznamu na styl box.  
  
 Pokud text položky je už v seznamu, nová data se ukládají s existující položku. Vyhledejte položku je velká a malá písmena.  
  
##  <a name="addsorteditem"></a>  CMFCToolBarComboBoxButton::AddSortedItem  
 Přidá položku do seznamu v pořadí, ve kterém je definována [porovnání](#compare) metody.  
  
```  
virtual INT_PTR AddSortedItem(
    LPCTSTR lpszItem,  
    DWORD_PTR dwData=0);
```  
  
### <a name="parameters"></a>Parametry  
*lpszItem*<br/>
[in] Text položky pro přidání do seznamu.  
  
*dwData*<br/>
[in] Data přidružená k položky pro přidání do seznamu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Index položky, která byla přidána do seznamu.  
  
### <a name="remarks"></a>Poznámky  
 Tuto funkci použijte k přidání položek do seznamu v určitém pořadí.  
  
##  <a name="canbestretched"></a>  CMFCToolBarComboBoxButton::CanBeStretched  
 Určuje, zda můžete změnit velikost tlačítka pole se seznamem.  
  
```  
virtual BOOL CanBeStretched() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu TRUE.  
  
##  <a name="cmfctoolbarcomboboxbutton"></a>  CMFCToolBarComboBoxButton::CMFCToolBarComboBoxButton  
 Vytvoří [cmfctoolbarcomboboxbutton –](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md) objektu.  
  
```  
CMFCToolBarComboBoxButton(
    UINT uiID,  
    int iImage,  
    DWORD dwStyle=CBS_DROPDOWNLIST,  
    int iWidth=0);
```  
  
### <a name="parameters"></a>Parametry  
*uiID*<br/>
[in] Identifikátor příkazu tlačítka Nový.  
  
*iImage*<br/>
[in] Index obrázku přidružený k tlačítku nové bitové kopie.  
  
*dwStyle*<br/>
[in] Styl tlačítka Nový.  
  
*iWidth*<br/>
[in] Šířka v pixelech, o nové tlačítko.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí šířka je 150 pixelů.  
  
 Seznam styly tlačítek panelu nástrojů najdete v části [– styly ovládacího prvku panel nástrojů](../../mfc/reference/toolbar-control-styles.md)  
  
##  <a name="cleardata"></a>  CMFCToolBarComboBoxButton::ClearData  
 Uživatelem definované datové odstraní.  
  
```  
virtual void ClearData();
```  
  
### <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení tato metoda nemá žádný účinek. Pokud chcete odstranit všechna data definovaný uživatelem, přepište tuto metodu v odvozené třídě.  
  
##  <a name="compare"></a>  CMFCToolBarComboBoxButton::Compare  
 Porovná dva řetězce.  
  
```  
virtual int Compare(
    LPCTSTR lpszItem1,  
    LPCTSTR lpszItem2);
```  
  
### <a name="parameters"></a>Parametry  
*lpszItem1*<br/>
[in] První řetězec určený k porovnání.  
  
*lpszItem2*<br/>
[in] Druhý řetězec určený k porovnání.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota, která označuje malá a velká písmena lexikografickým vztah mezi řetězce. V následující tabulce jsou uvedeny možné hodnoty:  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|\<0|První řetězec, který je menší než druhý.|  
|0|První řetězec, který se rovná druhé.|  
|>0|První řetězec, který je větší než druhý.|  
  
### <a name="remarks"></a>Poznámky  
 Přepsáním této metody můžete změnit způsob řazení položek v seznamu.  
  
 Porovnávání rozlišuje velká a malá písmena.  
  
 Tato metoda je volána pouze z [AddSortedItem](#addsorteditem) metody.  
  
##  <a name="copyfrom"></a>  CMFCToolBarComboBoxButton::CopyFrom  
 Zkopíruje stav zadaného `CMFCToolBarComboBoxButton` aktuálnímu objektu.  
  
```  
virtual void CopyFrom(const CMFCToolBarButton& src);
```  
  
### <a name="parameters"></a>Parametry  
*src*<br/>
[in] Zdroj `CMFCToolBarComboBoxButton` objektu.  
  
##  <a name="createcombo"></a>  CMFCToolBarComboBoxButton::CreateCombo  
 Vytvoří nové pole se seznamem pro tlačítko pole se seznamem.  
  
```  
virtual CComboBox* CreateCombo(
    CWnd* pWndParent,  
    const CRect& rect);
```  
  
### <a name="parameters"></a>Parametry  
*pWndParent*<br/>
[in] Ukazatel do nadřazeného okna tlačítka.  
  
*Rect*<br/>
[in] Ohraničující obdélník pole se seznamem.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na nové pole se seznamem, pokud metoda byla úspěšná. v opačném případě hodnota NULL.  
  
##  <a name="createedit"></a>  CMFCToolBarComboBoxButton::CreateEdit  
 Vytvoří nové textové pole pro tlačítko pole se seznamem.  
  
```  
virtual CMFCToolBarComboBoxEdit* CreateEdit(
    CWnd* pWndParent,  
    const CRect& rect,  
    DWORD dwEditStyle);
```  
  
### <a name="parameters"></a>Parametry  
*pWndParent*<br/>
[in] Ukazatel do nadřazeného okna tlačítka.  
  
*Rect*<br/>
[in] Ohraničující obdélník nové pole pro úpravy.  
  
*dwEditStyle*<br/>
[in] Styl ovládacího prvku nové pole pro úpravy.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na nové textové pole, pokud metoda byla úspěšná. v opačném případě hodnota NULL.  
  
### <a name="remarks"></a>Poznámky  
 Rozhraní volá tuto metodu při vytváření nové textové pole pro tlačítko pole se seznamem. Přepsáním této metody můžete změnit způsob [cmfctoolbarcomboboxedit –](../../mfc/reference/cmfctoolbarcomboboxedit-class.md) se vytvoří.  
  
##  <a name="deleteitem"></a>  CMFCToolBarComboBoxButton::DeleteItem  
 Odstraní zadanou položku ze seznamu.  
  
```  
BOOL DeleteItem(int iIndex);  
BOOL DeleteItem(DWORD_PTR dwData);  
  BOOL DeleteItem(LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>Parametry  
*iIndex*<br/>
[in] Index založený na nule položka, která má být odstraněna.  
  
*dwData*<br/>
[in] Data přidružená k položka, která má být odstraněna.  
  
*lpszText*<br/>
[in] Text položky, která má být odstraněna. Pokud existuje více položek se stejným textem, odstraní se první položka.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud byla položka nachází a byla úspěšně odstraněna; v opačném případě hodnota FALSE.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="duplicatedata"></a>  CMFCToolBarComboBoxButton::DuplicateData  
 Uživatelem definované datové duplicitní položky.  
  
```  
virtual void DuplicateData();
```  
  
### <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení tato metoda nemá žádný účinek. Potlačí tuto metodu v odvozené třídě, pokud chcete zkopírovat všechny uživatelem definované datové.  
  
##  <a name="enablewindow"></a>  CMFCToolBarComboBoxButton::EnableWindow  
 Povolí nebo zakáže úpravy a pole se seznamem polí.  
  
```  
virtual void EnableWindow(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
*bEnable*<br/>
[in] TRUE, pokud chcete povolit úpravy a pole se seznamem polí; FALSE, pokud chcete zakázat úpravy a pole se seznamem polí.  
  
### <a name="remarks"></a>Poznámky  
 Pokud je zakázán, ovládací prvky se nemůže stát aktivní a nemůže přijímat uživatelský vstup.  
  
##  <a name="exporttomenubutton"></a>  CMFCToolBarComboBoxButton::ExportToMenuButton  
 Kopie řetězce z tabulky řetězců aplikaci do nabídky zadané pomocí příkazu tlačítka pole se seznamem ID.  
  
```  
virtual BOOL ExportToMenuButton(CMFCToolBarMenuButton& menuButton) const;  
```  
  
### <a name="parameters"></a>Parametry  
*Tlačítko nabídky*<br/>
[out] Odkaz na tlačítko nabídky.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vždy TRUE.  
  
##  <a name="finditem"></a>  CMFCToolBarComboBoxButton::FindItem  
 Vrátí index první položky v seznamu, který obsahuje zadaný řetězec.  
  
```  
int FindItem(LPCTSTR lpszText) const;  
```  
  
### <a name="parameters"></a>Parametry  
*lpszText*<br/>
[in] Text, který chcete vyhledat v seznamu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Index položky; nebo CB_ERR, pokud položka není nalezena.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getbycmd"></a>  CMFCToolBarComboBoxButton::GetByCmd  
 Získá ukazatel na tlačítka pole se seznamem, který má ID zadaného příkazu.  
  
```  
static CMFCToolBarComboBoxButton* GetByCmd(
    UINT uiCmd,  
    BOOL bIsFocus=FALSE);
```  
  
### <a name="parameters"></a>Parametry  
*uiCmd*<br/>
[in] Identifikátor příkazu tlačítka pole se seznamem.  
  
*bIsFocus*<br/>
[in] True pro pouze vyhledávání, zaměřuje tlačítka; FALSE, pokud chcete hledat všechna tlačítka.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na tlačítka pole se seznamem; nebo hodnota NULL, pokud se nenajde na tlačítko.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getcombobox"></a>  CMFCToolBarComboBoxButton::GetComboBox  
 Vrací ukazatel na pole se seznamem pole se seznamem tlačítko pole.  
  
```  
CComboBox* GetComboBox() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel [CComboBox – třída](../../mfc/reference/ccombobox-class.md) objektu, pokud metoda byla úspěšná; jinak hodnota NULL.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getcontextmenuid"></a>  CMFCToolBarComboBoxButton::GetContextMenuID  
 Získá ID prostředku místní nabídky pro tlačítka pole se seznamem.  
  
```  
UINT GetContextMenuID();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 ID místní nabídce prostředku.  
  
##  <a name="getcount"></a>  CMFCToolBarComboBoxButton::GetCount  
 Vrátí počet položek v seznamu.  
  
```  
INT_PTR GetCount() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet položek v seznamu.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getcountall"></a>  CMFCToolBarComboBoxButton::GetCountAll  
 Získá počet položek v seznamu tlačítko pole se seznamem, který má ID zadaného příkazu.  
  
```  
static int GetCountAll(UINT uiCmd);
```  
  
### <a name="parameters"></a>Parametry  
*uiCmd*<br/>
[in] Identifikátor příkazu tlačítka pole se seznamem.  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet položek v seznamu pole. v opačném případě CB_ERR Pokud tlačítko pole se seznamem se nenašel.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getcursel"></a>  CMFCToolBarComboBoxButton::GetCurSel  
 Získá index aktuálně vybrané položky v seznamu.  
  
```  
int GetCurSel() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Index aktuálně vybrané položky v seznamu pole. nebo CB_ERR, pokud není vybrána žádná položka.  
  
### <a name="remarks"></a>Poznámky  
 Indexu pole se seznamem je založený na nule.  
  
##  <a name="getcurselall"></a>  CMFCToolBarComboBoxButton::GetCurSelAll  
 Vrátí index aktuálně vybrané položky v seznamu pole se seznamem, tlačítka pole, která má ID zadaného příkazu.  
  
```  
static int GetCurSelAll(UINT uiCmd);
```  
  
### <a name="parameters"></a>Parametry  
*uiCmd*<br/>
[in] Identifikátor příkazu tlačítka pole se seznamem.  
  
### <a name="return-value"></a>Návratová hodnota  
 Index aktuálně vybrané položky v seznamu pole. v opačném případě se nenašel CB_ERR, pokud není vybrána žádná položka nebo tlačítko pole se seznamem.  
  
### <a name="remarks"></a>Poznámky  
 Indexu pole se seznamem je založený na nule.  
  
##  <a name="geteditctrl"></a>  CMFCToolBarComboBoxButton::GetEditCtrl  
 Vrací ukazatel na pole pro úpravy pole se seznamem tlačítko pole.  
  
```  
virtual CEdit* GetEditCtrl();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na textové pole, pokud metoda byla úspěšná. v opačném případě hodnota NULL.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="gethwnd"></a>  CMFCToolBarComboBoxButton::GetHwnd  
 Vrátí popisovač okna pro pole se seznamem.  
  
```  
virtual HWND GetHwnd();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Popisovač okna, nebo hodnota NULL, pokud není spojen s objektem okna v poli se seznamem.  
  
##  <a name="getitem"></a>  CMFCToolBarComboBoxButton::GetItem  
 Vrací řetězec přidružený k položce na zadaném indexu v seznamu.  
  
```  
LPCTSTR GetItem(int iIndex=-1) const;  
```  
  
### <a name="parameters"></a>Parametry  
*iIndex*<br/>
[in] Z nuly vycházející index položky v seznamu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na řetězec, který je přidružený k položce; v opačném případě hodnotu NULL, pokud parametr indexu je neplatný, nebo pokud je parametr indexu -1 a v poli se seznamem není vybrána žádná položka.  
  
### <a name="remarks"></a>Poznámky  
 Parametr indexu-1 vrátí řetězec, který je aktuálně vybrané položky.  
  
##  <a name="getitemall"></a>  CMFCToolBarComboBoxButton::GetItemAll  
 Vrací řetězec přidružený k položce na zadaný index v poli seznamu tlačítko pole se seznamem, který má ID zadaného příkazu.  
  
```  
static LPCTSTR GetItemAll(
    UINT uiCmd,  
    int iIndex=-1);
```  
  
### <a name="parameters"></a>Parametry  
*uiCmd*<br/>
[in] Identifikátor příkazu tlačítka pole se seznamem.  
  
*iIndex*<br/>
[in] Index založený na nule položku v seznamu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na řetězec položky, pokud metoda byla úspěšná. v opačném případě hodnotu NULL, pokud je index není platný, tlačítka pole se seznamem není nalezen, nebo pokud je index -1 a v poli se seznamem není vybrána žádná položka.  
  
### <a name="remarks"></a>Poznámky  
 Hodnota indexu-1 vrátí řetězec, který je aktuálně vybrané položky.  
  
##  <a name="getitemdata"></a>  CMFCToolBarComboBoxButton::GetItemData  
 Vrátí data související s položkou v konkrétní indexu v seznamu.  
  
```  
DWORD_PTR GetItemData(int iIndex=-1) const;  
```  
  
### <a name="parameters"></a>Parametry  
*iIndex*<br/>
[in] Index založený na nule položku v seznamu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Data přidružená k položce; nebo 0, pokud položka neexistuje.  
  
### <a name="remarks"></a>Poznámky  
 Parametr indexu-1 vrátí data přidružená k aktuálně vybrané položky.  
  
##  <a name="getitemdataall"></a>  CMFCToolBarComboBoxButton::GetItemDataAll  
 Vrátí data související s položkou v konkrétní indexu v seznamu tlačítka pole se seznamem, který má ID konkrétní příkazu.  
  
```  
static DWORD_PTR GetItemDataAll(
    UINT uiCmd,  
    int iIndex=-1);
```  
  
### <a name="parameters"></a>Parametry  
*uiCmd*<br/>
[in] Identifikátor příkazu tlačítka pole se seznamem.  
  
*iIndex*<br/>
[in] Index založený na nule položku v seznamu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Data související s položkou, byla-li metoda úspěšná; v opačném případě 0, pokud zadaný index je neplatný nebo CB_ERR Pokud tlačítko pole se seznamem se nenašel.  
  
### <a name="remarks"></a>Poznámky  
 Parametr indexu-1 vrátí data přidružená k aktuálně vybrané položky.  
  
##  <a name="getitemdataptrall"></a>  CMFCToolBarComboBoxButton::GetItemDataPtrAll  
 Vrátí data související s položkou v konkrétní indexu v seznamu tlačítka pole se seznamem, který má ID konkrétní příkazu. Tato data se vrátí jako ukazatel.  
  
```  
static void* GetItemDataPtrAll(
    UINT uiCmd,  
    int iIndex=-1);
```  
  
### <a name="parameters"></a>Parametry  
*uiCmd*<br/>
[in] Identifikátor příkazu tlačítka pole se seznamem.  
  
*iIndex*<br/>
[in] Index založený na nule položku v seznamu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel přidružené k položce byla-li metoda úspěšná; v opačném případě dojde k-1, pokud chybu nebo hodnota NULL, pokud tlačítko pole se seznamem se nenašel.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getprompt"></a>  CMFCToolBarComboBoxButton::GetPrompt  
 Vrátí řetězec, který se pro pole se seznamem, tlačítka pole.  
  
```  
virtual CString GetPrompt() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Řetězec, který se.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda není aktuálně implementována.  
  
##  <a name="gettext"></a>  CMFCToolBarComboBoxButton::GetText  
 Načte text do textového pole.  
  
```  
LPCTSTR GetText() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Text do textového pole.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="gettextall"></a>  CMFCToolBarComboBoxButton::GetTextAll  
 Načte text do textového pole tlačítko pole se seznamem, který má ID zadaného příkazu.  
  
```  
static LPCTSTR GetTextAll(UINT uiCmd);
```  
  
### <a name="parameters"></a>Parametry  
*uiCmd*<br/>
[in] Identifikátor příkazu tlačítka pole se seznamem konkrétní.  
  
### <a name="return-value"></a>Návratová hodnota  
 Text v textové pole, pokud metoda byla úspěšná. v opačném případě hodnota NULL.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="hasfocus"></a>  CMFCToolBarComboBoxButton::HasFocus  
 Označuje, zda pole se seznamem má aktuálně fokus.  
  
```  
virtual BOOL HasFocus() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud pole se seznamem má právě fokus; v opačném případě hodnota FALSE.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda také vrátí hodnotu TRUE, pokud všechny podřízené okno pole se seznamem má aktuálně fokus.  
  
##  <a name="iscentervert"></a>  CMFCToolBarComboBoxButton::IsCenterVert  
 Vrátí svislá pozice tlačítka pole se seznamem v aplikaci.  
  
```  
static BOOL IsCenterVert();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud se na tlačítka; FALSE, pokud jsou zarovnané tlačítka v horní části.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="isflatmode"></a>  CMFCToolBarComboBoxButton::IsFlatMode  
 Vrací plochý vzhled tlačítka pole se seznamem v aplikaci.  
  
```  
static BOOL IsFlatMode();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud tlačítka mají plochý; v opačném případě hodnota FALSE.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí styl ploché tlačítka pole se seznamem je FALSE.  
  
##  <a name="isownerof"></a>  CMFCToolBarComboBoxButton::IsOwnerOf  
 Označuje, zda je zadaný popisovač spojené s tlačítko pole se seznamem nebo jedna z jejích podřízených.  
  
```  
virtual BOOL IsOwnerOf(HWND hwnd);
```  
  
### <a name="parameters"></a>Parametry  
*hWnd*<br/>
[in] Popisovač okna.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud je popisovač je přidružený pomocí tlačítka pole se seznamem nebo jedna z jejích podřízených; v opačném případě hodnota FALSE.  
  
##  <a name="isribbonbutton"></a>  CMFCToolBarComboBoxButton::IsRibbonButton  
 Určuje, zda se nachází tlačítko pole se seznamem na panel pásu karet.  
  
```  
BOOL IsRibbonButton() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vždy hodnotu FALSE.  
  
### <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení tato metoda vždy vrátí hodnotu FALSE, což znamená, že tlačítko pole se seznamem se nikdy zobrazí na panelu pásu karet.  
  
##  <a name="iswindowvisible"></a>  CMFCToolBarComboBoxButton::IsWindowVisible  
 Vrátí pole se seznamem stav viditelnosti tlačítka pole.  
  
```  
virtual BOOL IsWindowVisible();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Stav viditelnosti tlačítka pole se seznamem.  
  
##  <a name="notifycommand"></a>  CMFCToolBarComboBoxButton::NotifyCommand  
 Určuje, zda tlačítko pole se seznamem zpracovávat zprávu.  
  
```  
virtual BOOL NotifyCommand(int iNotifyCode);
```  
  
### <a name="parameters"></a>Parametry  
*iNotifyCode*<br/>
[in] Zprávy oznámení, který je přidružený příkaz.  
  
### <a name="return-value"></a>Návratová hodnota  
 Určuje, zda tlačítko pole se seznamem zpracovává zprávy.  
  
##  <a name="onaddtocustomizepage"></a>  CMFCToolBarComboBoxButton::OnAddToCustomizePage  
 Volá se rozhraním, když se přidá tlačítko do **vlastní** dialogové okno.  
  
```  
virtual void OnAddToCustomizePage();
```  
  
##  <a name="oncalculatesize"></a>  CMFCToolBarComboBoxButton::OnCalculateSize  
 Volá se rozhraním vypočítat velikost tlačítka.  
  
```  
virtual SIZE OnCalculateSize(
    CDC* pDC,  
    const CSize& sizeDefault,  
    BOOL bHorz);
```  
  
### <a name="parameters"></a>Parametry  
*primární řadič domény*<br/>
[in] Kontext zařízení, která zobrazuje tlačítko pole se seznamem.  
  
*sizeDefault*<br/>
[in] Výchozí velikost tlačítka pole se seznamem.  
  
*bHorz*<br/>
[in] Ukotvit stav nadřazeného panelu nástrojů. Hodnota TRUE, když se ukotví vodorovně a FALSE. když se ukotví svisle.  
  
### <a name="return-value"></a>Návratová hodnota  
 A `SIZE` strukturu, která obsahuje dimenze tlačítko pole se seznamem v pixelech.  
  
##  <a name="onchangeparentwnd"></a>  CMFCToolBarComboBoxButton::OnChangeParentWnd  
 Volá se rozhraním, když tlačítko pole se seznamem se vloží do nového panelu nástrojů.  
  
```  
virtual void OnChangeParentWnd(CWnd* pWndParent);
```  
  
### <a name="parameters"></a>Parametry  
*pWndParent*<br/>
[in] Ukazatel do nového nadřazeného panelu nástrojů.  
  
##  <a name="onclick"></a>  CMFCToolBarComboBoxButton::OnClick  
 Volá se rozhraním, když uživatel klikne na tlačítko pole se seznamem.  
  
```  
virtual BOOL OnClick(
    CWnd* pWnd,  
    BOOL bDelay = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
*pWnd*<br/>
[in] Ukazatel na nadřazené okno tlačítko pole se seznamem.  
  
*bDelay*<br/>
[in] Vyhrazené pro použití v odvozené třídě.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud metoda zpracovává události. v opačném případě hodnota FALSE.  
  
##  <a name="onctlcolor"></a>  CMFCToolBarComboBoxButton::OnCtlColor  
 Volá se rozhraním, když uživatel změní barvu nadřazené nástrojů nastavit barvu tlačítka pole se seznamem.  
  
```  
virtual HBRUSH OnCtlColor(
    CDC* pDC,  
    UINT nCtlColor);
```  
  
### <a name="parameters"></a>Parametry  
*primární řadič domény*<br/>
[in] Kontext zařízení, která zobrazuje tlačítko pole se seznamem.  
  
*nCtlColor*<br/>
[in] Nevyužité.  
  
### <a name="return-value"></a>Návratová hodnota  
 Popisovač štětec, který systém použije k vykreslení na pozadí tlačítka pole se seznamem.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda také nastaví barvu textu tlačítka pole se seznamem.  
  
##  <a name="ondraw"></a>  CMFCToolBarComboBoxButton::OnDraw  
 Volá se rozhraním, chcete-li nakreslit tlačítko pole se seznamem na základě zadaného styly a možnosti.  
  
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
*Primární řadič domény*<br/>
[in] Kontext zařízení, která se zobrazí tlačítko.  
  
*Rect*<br/>
[in] Ohraničující obdélník na tlačítko.  
  
*pImages*<br/>
[in] Kolekci imagí, který je přidružený k tlačítku.  
  
*bHorz*<br/>
[in] Ukotvit stav nadřazeného panelu nástrojů. Hodnota TRUE, když se ukotví vodorovně a FALSE. když se ukotví svisle.  
  
*bCustomizeMode*<br/>
[in] Určuje, zda je aplikace v režimu úprav.  
  
*bHighlight*<br/>
[in] Určuje, zda chcete-li nakreslit zvýrazněným tlačítkem pole se seznamem.  
  
*bDrawBorder*<br/>
[in] Určuje, zda chcete-li nakreslit tlačítko pole se seznamem s ohraničením.  
  
*bGrayDisabledButtons*<br/>
[in] True pro vykreslení stín tlačítka Zakázané; FALSE, pokud chcete použít kolekci zakázané imagí.  
  
##  <a name="ondrawoncustomizelist"></a>  CMFCToolBarComboBoxButton::OnDrawOnCustomizeList  
 Volá se rozhraním, chcete-li nakreslit tlačítko pole se seznamem **příkazy** podokně **vlastní** dialogové okno.  
  
```  
virtual int OnDrawOnCustomizeList(
    CDC* pDC,  
    const CRect& rect,  
    BOOL bSelected);
```  
  
### <a name="parameters"></a>Parametry  
*primární řadič domény*<br/>
[in] Kontext zařízení, která zobrazuje tlačítko pole se seznamem.  
  
*Rect*<br/>
[in] Ohraničující obdélník tlačítko pole se seznamem.  
  
*bSelected*<br/>
[in] Hodnota TRUE, pokud je zaškrtnuto tlačítko pole se seznamem. v opačném případě hodnota FALSE.  
  
### <a name="return-value"></a>Návratová hodnota  
 Šířka v pixelech, tlačítka pole se seznamem.  
  
##  <a name="onglobalfontschanged"></a>  CMFCToolBarComboBoxButton::OnGlobalFontsChanged  
 Volá se rozhraním, nastavit pole se seznamem písma tlačítko pole při změně písmo aplikace.  
  
```  
virtual void OnGlobalFontsChanged();
```  
  
##  <a name="onmove"></a>  CMFCToolBarComboBoxButton::OnMove  
 Volá se rozhraním, chcete-li změnit umístění tlačítka pole se seznamem přesun nadřazeného panelu nástrojů.  
  
```  
virtual void OnMove();
```  
  
##  <a name="onshow"></a>  CMFCToolBarComboBoxButton::OnShow  
 Volá se rozhraním, když je skryta nebo zobrazena tlačítka pole se seznamem.  
  
```  
virtual void OnShow(BOOL bShow);
```  
  
### <a name="parameters"></a>Parametry  
*bShow*<br/>
[in] Určuje, zda skrýt nebo zobrazit tlačítko pole se seznamem.  
  
##  <a name="onsize"></a>  CMFCToolBarComboBoxButton::OnSize  
 Volá se rozhraním, chcete-li změnit velikost tlačítka pole se seznamem při změně velikosti nadřazeného panelu nástrojů.  
  
```  
virtual void OnSize(int iSize);
```  
  
### <a name="parameters"></a>Parametry  
*iSize*<br/>
[in] Novou šířku tlačítka pole se seznamem.  
  
##  <a name="onupdatetooltip"></a>  CMFCToolBarComboBoxButton::OnUpdateToolTip  
 Volá se rozhraním, když uživatel změní popis tlačítka pro tlačítko pole se seznamem.  
  
```  
virtual BOOL OnUpdateToolTip(
    CWnd* pWndParent,  
    int iButtonIndex,  
    CToolTipCtrl& wndToolTip,  
    CString& str);
```  
  
### <a name="parameters"></a>Parametry  
*pWndParent*<br/>
[in] Ukazatel do nadřazeného okna pro tlačítko pole se seznamem.  
  
*iButtonIndex*<br/>
[in] ID tlačítko pole se seznamem.  
  
*wndToolTip*<br/>
[in] Popis tlačítka pro přidružení k tlačítko pole se seznamem.  
  
*str*<br/>
[in] Text tipu nástroj.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud metoda zpracovává události. v opačném případě hodnota FALSE.  
  
##  <a name="removeallitems"></a>  CMFCToolBarComboBoxButton::RemoveAllItems  
 Odstraní všechny položky ze seznamu a úpravy polí.  
  
```  
void RemoveAllItems();
```  
  
### <a name="remarks"></a>Poznámky  
 Odebere všechny položky v seznamu pole a upravit ovládací prvek pole se seznamem.  
  
##  <a name="selectitem"></a>  CMFCToolBarComboBoxButton::SelectItem  
 Vybere položku v seznamu.  
  
```  
BOOL SelectItem(
    int iIndex,  
    BOOL bNotify=TRUE);  
  
BOOL SelectItem(DWORD_PTR dwData);  
BOOL SelectItem(LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>Parametry  
*iIndex*<br/>
[in] Index založený na nule položku v seznamu.  
  
*bNotify*<br/>
[in] TRUE, pokud chcete informovat tlačítko pole se seznamem výběru; v opačném případě FALSE.  
  
*dwData*<br/>
[in] Data související s položkou v seznamu.  
  
*lpszText*<br/>
[in] Text položky v seznamu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud metoda byla úspěšná. v opačném případě FALSE.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="selectitemall"></a>  CMFCToolBarComboBoxButton::SelectItemAll  
 Vybere položku v seznamu tlačítko pole se seznamem, který má ID zadaného příkazu.  
  
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
*uiCmd*<br/>
[in] Identifikátor příkazu tlačítka pole se seznamem, který obsahuje pole se seznamem.  
  
*iIndex*<br/>
[in] Index založený na nule položky v seznamu. Hodnota -1 se odeberou všechny aktuální výběr v seznamu a vymaže pole pro úpravy.  
  
*dwData*<br/>
[in] Data, která položky v seznamu.  
  
*lpszText*<br/>
[in] Text položky v seznamu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud metoda byla úspěšná. v opačném případě FALSE.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="serialize"></a>  CMFCToolBarComboBoxButton::Serialize  
 Čte tento objekt z archivu nebo zapíše do archivu.  
  
```  
virtual void Serialize(CArchive& ar);
```  
  
### <a name="parameters"></a>Parametry  
*ar*<br/>
[out v] `CArchive` Objektu určeného k serializaci.  
  
### <a name="remarks"></a>Poznámky  
 V nastavení `CArchive` objektu určit, jestli tato metoda čte nebo zapisuje do archivu.  
  
##  <a name="setaccdata"></a>  CMFCToolBarComboBoxButton::SetACCData  
 Naplní zadaný `CAccessibilityData` objekt usnadnění daty z tlačítka pole se seznamem.  
  
```  
virtual BOOL SetACCData(
    CWnd* pParent,  
    CAccessibilityData& data);
```  
  
### <a name="parameters"></a>Parametry  
*pParent*<br/>
[in] Nadřazené okno tlačítko pole se seznamem.  
  
*data*<br/>
[out] A `CAccessibilityData` objekt, který přijímá data přístupnost z tlačítka pole se seznamem.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud metoda byla úspěšná. v opačném případě FALSE.  
  
##  <a name="setcentervert"></a>  CMFCToolBarComboBoxButton::SetCenterVert  
 Nastaví svislou pozici tlačítka pole se seznamem v aplikaci.  
  
```  
static void SetCenterVert(BOOL bCenterVert=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
*bCenterVert*<br/>
[in] TRUE, pokud chcete prostřední tlačítko pole se seznamem na panelu nástrojů; FALSE pro zarovnání tlačítko pole se seznamem na horním panelu nástrojů.  
  
### <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení jsou tlačítka pole se seznamem zarovnaným k hornímu.  
  
##  <a name="setcontextmenuid"></a>  CMFCToolBarComboBoxButton::SetContextMenuID  
 Nastaví ID prostředku místní nabídky pro pole se seznamem, tlačítka pole.  
  
```  
void SetContextMenuID(UINT uiResID);
```  
  
### <a name="parameters"></a>Parametry  
*uiResID*<br/>
[in] ID místní nabídce prostředku.  
  
##  <a name="setdropdownheight"></a>  CMFCToolBarComboBoxButton::SetDropDownHeight  
 Výška pole se seznamem nastaví, když se rozbalil.  
  
```  
void SetDropDownHeight(int nHeight);
```  
  
### <a name="parameters"></a>Parametry  
*nHeight*<br/>
[in] Výška v pixelech, pole se seznamem.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí výška je 150 pixelů.  
  
##  <a name="setflatmode"></a>  CMFCToolBarComboBoxButton::SetFlatMode  
 Plochý vzhled tlačítka pole se seznamem nastaví v aplikaci.  
  
```  
static void SetFlatMode(BOOL bFlat=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
*bFlat*<br/>
[in] Hodnota TRUE pro plochý vzhled; v opačném případě FALSE.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí styl ploché tlačítka pole se seznamem je FALSE.  
  
##  <a name="setstyle"></a>  CMFCToolBarComboBoxButton::SetStyle  
 Nastaví zadaný styl pro pole se seznamem, tlačítka pole a překreslí ovládacího prvku, pokud to není zakázáno.  
  
```  
virtual void SetStyle(UINT nStyle);
```  
  
### <a name="parameters"></a>Parametry  
*nStyle*<br/>
[in] Bitová kombinace (nebo) panel nástrojů stylů.  
  
### <a name="remarks"></a>Poznámky  
 Seznam styly tlačítek panelu nástrojů najdete v části [– styly ovládacího prvku panel nástrojů](../../mfc/reference/toolbar-control-styles.md)  
  
##  <a name="settext"></a>  CMFCToolBarComboBoxButton::SetText  
 Nastaví text do textového pole se seznamem pro tlačítko pole.  
  
```  
void SetText(LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>Parametry  
*lpszText*<br/>
[in] Ukazatel na řetězec, který obsahuje text pro textové pole.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [Cmfctoolbarbutton – třída](../../mfc/reference/cmfctoolbarbutton-class.md)   
 [CComboBox – třída](../../mfc/reference/ccombobox-class.md)   
 [CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)   
 [Návod: Umístění ovládacích prvků na panely nástrojů](../../mfc/walkthrough-putting-controls-on-toolbars.md)



