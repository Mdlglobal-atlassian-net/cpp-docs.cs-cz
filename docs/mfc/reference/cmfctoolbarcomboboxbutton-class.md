---
title: CMFCToolBarComboBoxButton – třída
ms.date: 11/04/2016
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
ms.openlocfilehash: 639a5f98ff4780bd26388796039e85b812621b36
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2019
ms.locfileid: "68915971"
---
# <a name="cmfctoolbarcomboboxbutton-class"></a>CMFCToolBarComboBoxButton – třída

Tlačítko panelu nástrojů, které obsahuje ovládací prvek pole se seznamem ( [Třída CComboBox –](../../mfc/reference/ccombobox-class.md)).

## <a name="syntax"></a>Syntaxe

```
class CMFCToolBarComboBoxButton : public CMFCToolBarButton
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CMFCToolBarComboBoxButton::CMFCToolBarComboBoxButton](#cmfctoolbarcomboboxbutton)|`CMFCToolBarComboBoxButton`Vytvoří.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CMFCToolBarComboBoxButton::AddItem](#additem)|Přidá položku na konec seznamu pole se seznamem.|
|[CMFCToolBarComboBoxButton::AddSortedItem](#addsorteditem)|Přidá položku do seznamu pole se seznamem. Pořadí položek v seznamu je určeno `Compare`.|
|[CMFCToolBarComboBoxButton::Compare](#compare)|Porovná dvě položky. Volá se, aby se `AddSortedItems` seřadily položky, které se přidají do seznamu polí se seznamem.|
|[CMFCToolBarComboBoxButton::CreateEdit](#createedit)|Vytvoří nový ovládací prvek pro úpravy pro tlačítko pole se seznamem.|
|[CMFCToolBarComboBoxButton::DeleteItem](#deleteitem)|Odstraní položku ze seznamu pole se seznamem.|
|[CMFCToolBarComboBoxButton::FindItem](#finditem)|Vrátí index položky, která obsahuje zadaný řetězec.|
|[CMFCToolBarComboBoxButton::GetByCmd](#getbycmd)|Vrátí ukazatel na tlačítko pole se seznamem se zadaným ID příkazu.|
|[CMFCToolBarComboBoxButton:: getcombobox](#getcombobox)|Vrátí ukazatel na ovládací prvek pole se seznamem, který je vložený na tlačítko pole se seznamem.|
|[CMFCToolBarComboBoxButton::GetCount](#getcount)|Vrátí počet položek v seznamu pole se seznamem.|
|[CMFCToolBarComboBoxButton::GetCountAll](#getcountall)|Najde tlačítko pole se seznamem, které má zadané ID příkazu. Vrátí počet položek v seznamu pole se seznamem daného tlačítka.|
|[CMFCToolBarComboBoxButton::GetCurSel](#getcursel)|Vrátí index vybrané položky v seznamu pole se seznamem.|
|[CMFCToolBarComboBoxButton::GetCurSelAll](#getcurselall)|Najde tlačítko pole se seznamem, které má zadané ID příkazu, a vrátí index vybrané položky v seznamu pole se seznamem daného tlačítka.|
|[CMFCToolBarComboBoxButton::GetEditCtrl](#geteditctrl)|Vrátí ukazatel na ovládací prvek pro úpravy, který je vložený na tlačítko pole se seznamem.|
|[CMFCToolBarComboBoxButton::GetItem](#getitem)|Vrátí řetězec, který je přidružen k zadanému indexu v seznamu pole se seznamem.|
|[CMFCToolBarComboBoxButton::GetItemAll](#getitemall)|Najde tlačítko pole se seznamem, které má zadané ID příkazu, a vrátí řetězec, který je přidružen k indexu v seznamu pole se seznamem daného tlačítka.|
|[CMFCToolBarComboBoxButton::GetItemData](#getitemdata)|Vrátí hodnotu 32, která je přidružená k zadanému indexu v seznamu pole se seznamem.|
|[CMFCToolBarComboBoxButton::GetItemDataAll](#getitemdataall)|Vyhledá tlačítko pole se seznamem, které má zadané ID příkazu, a vrátí hodnotu 32, která je přidružena k indexu v seznamu pole se seznamem daného tlačítka.|
|[CMFCToolBarComboBoxButton::GetItemDataPtrAll](#getitemdataptrall)|Najde tlačítko pole se seznamem, které má zadané ID příkazu. Načte hodnotu 32, která je přidružena k indexu v seznamu pole se seznamem daného tlačítka a vrátí hodnotu 32 jako ukazatel.|
|[CMFCToolBarComboBoxButton::GetText](#gettext)|Vrátí text z ovládacího prvku pro úpravy pole se seznamem.|
|[CMFCToolBarComboBoxButton::GetTextAll](#gettextall)|Najde tlačítko pole se seznamem, které má zadané ID příkazu, a vrátí text z ovládacího prvku pro úpravy tohoto tlačítka.|
|[CMFCToolBarComboBoxButton::IsCenterVert](#iscentervert)|Určuje, zda jsou tlačítka pole se seznamem v aplikaci zarovnána na střed nebo v horní části panelu nástrojů.|
|[CMFCToolBarComboBoxButton::IsFlatMode](#isflatmode)|Určuje, zda tlačítka pole se seznamem v aplikaci mají plochý vzhled.|
|[CMFCToolBarComboBoxButton::RemoveAllItems](#removeallitems)|Odebere všechny položky ze seznamu a textového ovládacího prvku pole se seznamem.|
|[CMFCToolBarComboBoxButton::SelectItem](#selectitem)|Vybere položku v poli se seznamem podle jejího indexu, 32 hodnoty nebo řetězce a upozorní ovládací prvek pole se seznamem na výběr.|
|[CMFCToolBarComboBoxButton::SelectItemAll](#selectitemall)|Najde tlačítko pole se seznamem, které má zadané ID příkazu. Volá `SelectItem` pro výběr položky v poli se seznamem podle jejího řetězce, indexu nebo 32 hodnoty.|
|[CMFCToolBarComboBoxButton::SetCenterVert](#setcentervert)|Určuje, zda jsou tlačítka pole se seznamem v aplikaci zarovnána svisle nebo v horní části panelu nástrojů.|
|[CMFCToolBarComboBoxButton::SetDropDownHeight](#setdropdownheight)|Nastaví výšku rozevíracího seznamu.|
|[CMFCToolBarComboBoxButton::SetFlatMode](#setflatmode)|Určuje, zda jsou tlačítka pole se seznamem v aplikaci plochým vzhledem.|

## <a name="remarks"></a>Poznámky

Chcete-li přidat tlačítko pole se seznamem na panel nástrojů, postupujte podle následujících kroků:

1. Zarezervujte si pro tlačítko zástupný identifikátor ID prostředku v nadřazeném prostředku panelu nástrojů.

2. Sestavte `CMFCToolBarComboBoxButton` objekt.

3. V obslužné rutině zprávy, která zpracovává zprávu AFX_WM_RESETTOOLBAR, nahraďte tlačítko zástupný text novým polem se seznamem pomocí [CMFCToolBar:: ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton).

Další informace najdete v tématu [Návod: Vložení ovládacích prvků na](../../mfc/walkthrough-putting-controls-on-toolbars.md)panely nástrojů. Příklad tlačítka panelu nástrojů pole se seznamem naleznete v příkladu projektu VisualStudioDemo.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak použít různé metody ve `CMFCToolBarComboBoxButton` třídě. V tomto příkladu se dozvíte, jak povolit pole pro úpravy a kombinování, nastavit svislé umístění tlačítek se seznamem v aplikaci, nastavit výšku pole se seznamem, když se má vyřadit, nastavit v aplikaci plochý vzhled tlačítek se seznamem. a nastavte text v textovém poli na tlačítko pole se seznamem. Tento fragment kódu je součástí ukázkového [vzorku sady Visual Studio](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_VisualStudioDemo#36](../../mfc/codesnippet/cpp/cmfctoolbarcomboboxbutton-class_1.cpp)]
[!code-cpp[NVC_MFC_VisualStudioDemo#37](../../mfc/codesnippet/cpp/cmfctoolbarcomboboxbutton-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

[CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxtoolbarcomboboxbutton. h

##  <a name="additem"></a>CMFCToolBarComboBoxButton:: AddItem

Připojí k poli se seznamem jedinečnou položku.

```
virtual INT_PTR AddItem(
    LPCTSTR lpszItem,
    DWORD_PTR dwData=0);
```

### <a name="parameters"></a>Parametry

*lpszItem*<br/>
pro Text položky, která se má přidat do pole se seznamem

*dwData*<br/>
pro Data spojená s položkou, která se mají přidat do pole se seznamem.

### <a name="return-value"></a>Návratová hodnota

Index poslední položky v poli se seznamem.

### <a name="remarks"></a>Poznámky

Tuto metodu nepoužívejte při řazení stylu seznamu.

Pokud je text položky již v seznamu, jsou nová data uložena spolu s existující položkou. Hledání položky rozlišuje velká a malá písmena.

##  <a name="addsorteditem"></a>CMFCToolBarComboBoxButton::AddSortedItem

Přidá položku do pole seznamu v pořadí, které je definováno metodou [Compare](#compare) .

```
virtual INT_PTR AddSortedItem(
    LPCTSTR lpszItem,
    DWORD_PTR dwData=0);
```

### <a name="parameters"></a>Parametry

*lpszItem*<br/>
pro Text položky, která se má přidat do pole se seznamem

*dwData*<br/>
pro Data spojená s položkou, která se mají přidat do pole se seznamem.

### <a name="return-value"></a>Návratová hodnota

Index položky přidané do pole se seznamem

### <a name="remarks"></a>Poznámky

Pomocí této funkce lze přidat položky do pole seznamu v určitém pořadí.

##  <a name="canbestretched"></a>CMFCToolBarComboBoxButton::CanBeStretched

Určuje, zda se může změnit velikost tlačítka pole se seznamem.

```
virtual BOOL CanBeStretched() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE.

##  <a name="cmfctoolbarcomboboxbutton"></a>CMFCToolBarComboBoxButton::CMFCToolBarComboBoxButton

Vytvoří objekt [CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md) .

```
CMFCToolBarComboBoxButton(
    UINT uiID,
    int iImage,
    DWORD dwStyle=CBS_DROPDOWNLIST,
    int iWidth=0);
```

### <a name="parameters"></a>Parametry

*uiID*<br/>
pro ID příkazu nového tlačítka

*iImage*<br/>
pro Index obrázku obrázku přidruženého k novému tlačítku

*dwStyle*<br/>
pro Styl tlačítka nový

*iWidth*<br/>
pro Šířka nového tlačítka v pixelech

### <a name="remarks"></a>Poznámky

Výchozí šířka je 150 pixelů.

Seznam stylů tlačítek panelu nástrojů viz [styly ovládacích prvků panelu nástrojů](../../mfc/reference/toolbar-control-styles.md)

##  <a name="cleardata"></a>  CMFCToolBarComboBoxButton::ClearData

Odstraní data definovaná uživatelem.

```
virtual void ClearData();
```

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení tato metoda neprovádí žádnou akci. Tuto metodu přepište v odvozené třídě, pokud chcete odstranit jakákoli data definovaná uživatelem.

##  <a name="compare"></a>CMFCToolBarComboBoxButton:: Compare

Porovná dva řetězce.

```
virtual int Compare(
    LPCTSTR lpszItem1,
    LPCTSTR lpszItem2);
```

### <a name="parameters"></a>Parametry

*lpszItem1*<br/>
pro První řetězec, který se má porovnat.

*lpszItem2*<br/>
pro Druhý řetězec, který se má porovnat.

### <a name="return-value"></a>Návratová hodnota

Hodnota, která označuje lexikografickým pořadím vztah mezi řetězci a rozlišující velká a malá písmena. Následující tabulka uvádí možné hodnoty:

|Value|Popis|
|-----------|-----------------|
|\<0|První řetězec je menší než druhý.|
|0|První řetězec se rovná druhému.|
|>0|První řetězec je větší než druhý.|

### <a name="remarks"></a>Poznámky

Tuto metodu přepište, pokud chcete změnit způsob řazení položek v poli se seznamem.

Porovnávání rozlišuje velká a malá písmena.

Tato metoda je volána pouze v metodě [AddSortedItem](#addsorteditem) .

##  <a name="copyfrom"></a>CMFCToolBarComboBoxButton::CopyFrom

Zkopíruje stav zadaného `CMFCToolBarComboBoxButton` objektu do aktuálního objektu.

```
virtual void CopyFrom(const CMFCToolBarButton& src);
```

### <a name="parameters"></a>Parametry

*src*<br/>
pro Zdrojový `CMFCToolBarComboBoxButton` objekt.

##  <a name="createcombo"></a>CMFCToolBarComboBoxButton::CreateCombo

Vytvoří nové pole se seznamem pro tlačítko pole se seznamem.

```
virtual CComboBox* CreateCombo(
    CWnd* pWndParent,
    const CRect& rect);
```

### <a name="parameters"></a>Parametry

*pWndParent*<br/>
pro Ukazatel na nadřazené okno tlačítka.

*OBD*<br/>
pro Ohraničující obdélník pole se seznamem.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na nové pole se seznamem, pokud byla metoda úspěšná; v opačném případě hodnota NULL.

##  <a name="createedit"></a>CMFCToolBarComboBoxButton::CreateEdit

Vytvoří nové textové pole pro tlačítko pole se seznamem.

```
virtual CMFCToolBarComboBoxEdit* CreateEdit(
    CWnd* pWndParent,
    const CRect& rect,
    DWORD dwEditStyle);
```

### <a name="parameters"></a>Parametry

*pWndParent*<br/>
pro Ukazatel na nadřazené okno tlačítka.

*OBD*<br/>
pro Ohraničující obdélník nového pole pro úpravy.

*dwEditStyle*<br/>
pro Styl ovládacího prvku pro nové pole pro úpravy

### <a name="return-value"></a>Návratová hodnota

Ukazatel na nové pole pro úpravy, pokud byla metoda úspěšná; v opačném případě hodnota NULL.

### <a name="remarks"></a>Poznámky

Rozhraní volá tuto metodu, když vytvoří nové textové pole pro tlačítko pole se seznamem. Tuto metodu přepište, pokud chcete změnit způsob vytvoření [CMFCToolBarComboBoxEdit](../../mfc/reference/cmfctoolbarcomboboxedit-class.md) .

##  <a name="deleteitem"></a>CMFCToolBarComboBoxButton::D eleteItem

Odstraní zadanou položku z pole se seznamem.

```
BOOL DeleteItem(int iIndex);
BOOL DeleteItem(DWORD_PTR dwData);
BOOL DeleteItem(LPCTSTR lpszText);
```

### <a name="parameters"></a>Parametry

*iIndex*<br/>
pro Index položky vycházející z nuly, který má být odstraněn.

*dwData*<br/>
pro Data přidružená k položce, která se má odstranit

*lpszText*<br/>
pro Text položky, která se má odstranit Pokud existuje více položek se stejným textem, je první položka odstraněna.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud se položka vyhledala a úspěšně odstranila; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

##  <a name="duplicatedata"></a>  CMFCToolBarComboBoxButton::DuplicateData

Duplikuje data definovaná uživatelem.

```
virtual void DuplicateData();
```

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení tato metoda neprovádí žádnou akci. Tuto metodu přepište v odvozené třídě, pokud chcete zkopírovat data definovaná uživatelem.

##  <a name="enablewindow"></a>CMFCToolBarComboBoxButton::EnableWindow

Povolí nebo zakáže pole pro úpravy a pole se seznamem.

```
virtual void EnableWindow(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parametry

*bEnable*<br/>
pro TRUE, pokud chcete povolit pole pro úpravy a pole se seznamem; FALSE, pokud chcete zakázat pole pro úpravy a pole se seznamem.

### <a name="remarks"></a>Poznámky

Pokud je toto pole zakázané, ovládací prvky se nedají aktivovat a nemohou přijímat vstupy uživatele.

##  <a name="exporttomenubutton"></a>CMFCToolBarComboBoxButton::ExportToMenuButton

Zkopíruje řetězec z tabulky řetězců aplikace do zadané nabídky pomocí ID příkazu pole se seznamem.

```
virtual BOOL ExportToMenuButton(CMFCToolBarMenuButton& menuButton) const;
```

### <a name="parameters"></a>Parametry

*menuButton*<br/>
mimo Odkaz na tlačítko nabídky

### <a name="return-value"></a>Návratová hodnota

Vždycky TRUE.

##  <a name="finditem"></a>CMFCToolBarComboBoxButton::FindItem

Vrátí index první položky v seznamu, která obsahuje zadaný řetězec.

```
int FindItem(LPCTSTR lpszText) const;
```

### <a name="parameters"></a>Parametry

*lpszText*<br/>
pro Text, který má být hledán v seznamu.

### <a name="return-value"></a>Návratová hodnota

Index položky; nebo CB_ERR, pokud položka nebyla nalezena.

### <a name="remarks"></a>Poznámky

##  <a name="getbycmd"></a>CMFCToolBarComboBoxButton::GetByCmd

Získá ukazatel na tlačítko pole se seznamem, které má zadané ID příkazu.

```
static CMFCToolBarComboBoxButton* GetByCmd(
    UINT uiCmd,
    BOOL bIsFocus=FALSE);
```

### <a name="parameters"></a>Parametry

*uiCmd*<br/>
pro ID příkazu pro tlačítko pole se seznamem

*bIsFocus*<br/>
pro TRUE, pokud chcete hledat pouze tlačítka s fokusem; FALSE pro hledání všech tlačítek.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na tlačítko pole se seznamem; nebo hodnotu NULL, pokud tlačítko není nalezeno.

### <a name="remarks"></a>Poznámky

##  <a name="getcombobox"></a>CMFCToolBarComboBoxButton:: getcombobox

Vrátí ukazatel na pole se seznamem na tlačítko pole se seznamem.

```
CComboBox* GetComboBox() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na objekt [třídy CComboBox –](../../mfc/reference/ccombobox-class.md) , pokud byla metoda úspěšná; jinak NULL.

### <a name="remarks"></a>Poznámky

##  <a name="getcontextmenuid"></a>CMFCToolBarComboBoxButton::GetContextMenuID

Získá ID prostředku místní nabídky pro tlačítko pole se seznamem.

```
UINT GetContextMenuID();
```

### <a name="return-value"></a>Návratová hodnota

ID prostředku místní nabídky

##  <a name="getcount"></a>CMFCToolBarComboBoxButton:: GetCount

Vrátí počet položek v poli se seznamem.

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet položek v poli se seznamem.

### <a name="remarks"></a>Poznámky

##  <a name="getcountall"></a>CMFCToolBarComboBoxButton::GetCountAll

Vrátí počet položek v seznamu tlačítka pole se seznamem, které má zadané ID příkazu.

```
static int GetCountAll(UINT uiCmd);
```

### <a name="parameters"></a>Parametry

*uiCmd*<br/>
pro ID příkazu pro tlačítko pole se seznamem

### <a name="return-value"></a>Návratová hodnota

Počet položek v seznamu; v opačném případě CB_ERR, pokud není nalezeno tlačítko pole se seznamem.

### <a name="remarks"></a>Poznámky

##  <a name="getcursel"></a>CMFCToolBarComboBoxButton::

Načte index aktuálně vybrané položky v seznamu.

```
int GetCurSel() const;
```

### <a name="return-value"></a>Návratová hodnota

Index aktuálně vybrané položky v seznamu; nebo CB_ERR, pokud není vybrána žádná položka.

### <a name="remarks"></a>Poznámky

Index pole seznamu je založený na nule.

##  <a name="getcurselall"></a>CMFCToolBarComboBoxButton::GetCurSelAll

Vrátí index aktuálně vybrané položky v seznamu tlačítka pole se seznamem, které má zadané ID příkazu.

```
static int GetCurSelAll(UINT uiCmd);
```

### <a name="parameters"></a>Parametry

*uiCmd*<br/>
pro ID příkazu pro tlačítko pole se seznamem

### <a name="return-value"></a>Návratová hodnota

Index aktuálně vybrané položky v seznamu; v opačném případě CB_ERR, pokud není vybrána žádná položka nebo nebylo nalezeno tlačítko pole se seznamem.

### <a name="remarks"></a>Poznámky

Index pole seznamu je založený na nule.

##  <a name="geteditctrl"></a>  CMFCToolBarComboBoxButton::GetEditCtrl

Vrátí ukazatel na pole pro úpravy na tlačítku pole se seznamem.

```
virtual CEdit* GetEditCtrl();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na pole pro úpravy, pokud byla metoda úspěšná; v opačném případě hodnota NULL.

### <a name="remarks"></a>Poznámky

##  <a name="gethwnd"></a>CMFCToolBarComboBoxButton:: GetHwnd

Vrátí popisovač okna pro pole se seznamem.

```
virtual HWND GetHwnd();
```

### <a name="return-value"></a>Návratová hodnota

Popisovač okna nebo hodnota NULL, pokud pole se seznamem není přidruženo k objektu window.

##  <a name="getitem"></a>CMFCToolBarComboBoxButton:: GetItem

Vrátí řetězec přidružený k položce v zadaném indexu v poli se seznamem.

```
LPCTSTR GetItem(int iIndex=-1) const;
```

### <a name="parameters"></a>Parametry

*iIndex*<br/>
pro Index položky založený na nule položky v seznamu.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na řetězec, který je přidružen k položce; v opačném případě hodnota NULL, pokud je parametr indexu neplatný, nebo pokud je parametr indexu-1 a v poli se seznamem není žádná vybraná položka.

### <a name="remarks"></a>Poznámky

Parametr indexu-1 vrátí řetězec aktuálně vybrané položky.

##  <a name="getitemall"></a>CMFCToolBarComboBoxButton::GetItemAll

Vrátí řetězec přidružený k položce v zadaném indexu v rozevíracím seznamu tlačítka pole se seznamem, které má zadané ID příkazu.

```
static LPCTSTR GetItemAll(
    UINT uiCmd,
    int iIndex=-1);
```

### <a name="parameters"></a>Parametry

*uiCmd*<br/>
pro ID příkazu pro tlačítko pole se seznamem

*iIndex*<br/>
pro Index položky vycházející z nuly položky v poli se seznamem.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na řetězec položky, pokud byla metoda úspěšná; v opačném případě hodnota NULL, pokud je index neplatný, není nalezeno tlačítko pole se seznamem, nebo pokud je index-1 a v poli se seznamem není žádná vybraná položka.

### <a name="remarks"></a>Poznámky

Hodnota indexu-1 vrátí řetězec aktuálně vybrané položky.

##  <a name="getitemdata"></a>CMFCToolBarComboBoxButton::GetItemData

Vrátí data přidružená k položce v zadaném indexu v seznamu.

```
DWORD_PTR GetItemData(int iIndex=-1) const;
```

### <a name="parameters"></a>Parametry

*iIndex*<br/>
pro Index položky vycházející z nuly položky v poli se seznamem.

### <a name="return-value"></a>Návratová hodnota

Data přidružená k položce; nebo 0, pokud položka neexistuje.

### <a name="remarks"></a>Poznámky

Parametr indexu-1 vrátí data přidružená k aktuálně vybrané položce.

##  <a name="getitemdataall"></a>CMFCToolBarComboBoxButton::GetItemDataAll

Vrátí data přidružená k položce na konkrétním indexu v seznamu tlačítka pole se seznamem, které má konkrétní ID příkazu.

```
static DWORD_PTR GetItemDataAll(
    UINT uiCmd,
    int iIndex=-1);
```

### <a name="parameters"></a>Parametry

*uiCmd*<br/>
pro ID příkazu pro tlačítko pole se seznamem

*iIndex*<br/>
pro Index položky vycházející z nuly položky v poli se seznamem.

### <a name="return-value"></a>Návratová hodnota

Data přidružená k položce, pokud byla metoda úspěšná; v opačném případě 0, pokud je zadaný index neplatný, nebo CB_ERR, pokud není nalezeno tlačítko pole se seznamem.

### <a name="remarks"></a>Poznámky

Parametr indexu-1 vrátí data přidružená k aktuálně vybrané položce.

##  <a name="getitemdataptrall"></a>CMFCToolBarComboBoxButton::GetItemDataPtrAll

Vrátí data přidružená k položce na konkrétním indexu v seznamu tlačítka pole se seznamem, které má konkrétní ID příkazu. Tato data se vrátí jako ukazatel.

```
static void* GetItemDataPtrAll(
    UINT uiCmd,
    int iIndex=-1);
```

### <a name="parameters"></a>Parametry

*uiCmd*<br/>
pro ID příkazu pro tlačítko pole se seznamem

*iIndex*<br/>
pro Index položky vycházející z nuly položky v poli se seznamem.

### <a name="return-value"></a>Návratová hodnota

Ukazatel přidružený k položce, pokud byla metoda úspěšná; v opačném případě-1 dojde k chybě nebo hodnotu NULL, pokud není nalezeno tlačítko pole se seznamem.

### <a name="remarks"></a>Poznámky

##  <a name="getprompt"></a>CMFCToolBarComboBoxButton:: GetPrompt

Vrátí řetězec výzvy pro tlačítko pole se seznamem.

```
virtual CString GetPrompt() const;
```

### <a name="return-value"></a>Návratová hodnota

Řetězec výzvy

### <a name="remarks"></a>Poznámky

Tato metoda není momentálně implementována.

##  <a name="gettext"></a>CMFCToolBarComboBoxButton:: GetText

Získá text v poli pro úpravy.

```
LPCTSTR GetText() const;
```

### <a name="return-value"></a>Návratová hodnota

Text v poli pro úpravy

### <a name="remarks"></a>Poznámky

##  <a name="gettextall"></a>CMFCToolBarComboBoxButton::GetTextAll

Získá text v poli pro úpravy tlačítka pole se seznamem, které má zadané ID příkazu.

```
static LPCTSTR GetTextAll(UINT uiCmd);
```

### <a name="parameters"></a>Parametry

*uiCmd*<br/>
pro ID příkazu konkrétního pole se seznamem.

### <a name="return-value"></a>Návratová hodnota

Text v poli pro úpravy, pokud byla metoda úspěšná; v opačném případě hodnota NULL.

### <a name="remarks"></a>Poznámky

##  <a name="hasfocus"></a>  CMFCToolBarComboBoxButton::HasFocus

Určuje, zda pole se seznamem aktuálně má fokus.

```
virtual BOOL HasFocus() const;
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud pole se seznamem aktuálně má fokus; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Tato metoda také vrátí hodnotu TRUE, pokud libovolné podřízené okno pole se seznamem aktuálně má fokus.

##  <a name="iscentervert"></a>CMFCToolBarComboBoxButton::IsCenterVert

Vrátí svislou pozici tlačítek pole se seznamem v aplikaci.

```
static BOOL IsCenterVert();
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud jsou tlačítka zarovnána na střed. FALSE, pokud jsou tlačítka zarovnána v horní části.

### <a name="remarks"></a>Poznámky

##  <a name="isflatmode"></a>CMFCToolBarComboBoxButton::IsFlatMode

Vrátí plochý vzhled tlačítek pole se seznamem v aplikaci.

```
static BOOL IsFlatMode();
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud mají tlačítka plochý styl; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Výchozí plochý styl pro tlačítka pole se seznamem je FALSE.

##  <a name="isownerof"></a>CMFCToolBarComboBoxButton::IsOwnerOf

Označuje, zda je zadaný popisovač spojen s tlačítkem pole se seznamem, nebo s některým z jeho podřízených objektů.

```
virtual BOOL IsOwnerOf(HWND hwnd);
```

### <a name="parameters"></a>Parametry

*HWND*<br/>
pro Popisovač okna.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je popisovač assocated s tlačítkem pole se seznamem nebo s některým z jeho podřízených objektů; v opačném případě FALSE.

##  <a name="isribbonbutton"></a>CMFCToolBarComboBoxButton::IsRibbonButton

Označuje, zda je tlačítko pole se seznamem umístěno na panelu pásu karet.

```
BOOL IsRibbonButton() const;
```

### <a name="return-value"></a>Návratová hodnota

Vždy NEPRAVDA.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení tato metoda vždycky vrátí hodnotu FALSE, což znamená, že se na pásu karet nikdy nezobrazuje tlačítko pole se seznamem.

##  <a name="iswindowvisible"></a>CMFCToolBarComboBoxButton::IsWindowVisible

Vrátí stav viditelnosti tlačítka pole se seznamem.

```
virtual BOOL IsWindowVisible();
```

### <a name="return-value"></a>Návratová hodnota

Stav viditelnosti tlačítka pole se seznamem

##  <a name="notifycommand"></a>CMFCToolBarComboBoxButton::NotifyCommand

Určuje, zda tlačítko pole se seznamem zpracovává zprávu.

```
virtual BOOL NotifyCommand(int iNotifyCode);
```

### <a name="parameters"></a>Parametry

*iNotifyCode*<br/>
pro Zpráva s oznámením, která je přidružena k příkazu.

### <a name="return-value"></a>Návratová hodnota

Určuje, zda tlačítko pole se seznamem zpracovává zprávu.

##  <a name="onaddtocustomizepage"></a>CMFCToolBarComboBoxButton::OnAddToCustomizePage

Volá se rozhraním, když se přidá tlačítko do dialogového okna **přizpůsobit** .

```
virtual void OnAddToCustomizePage();
```

##  <a name="oncalculatesize"></a>CMFCToolBarComboBoxButton::OnCalculateSize

Volá se rozhraním, aby se počítala velikost tlačítka.

```
virtual SIZE OnCalculateSize(
    CDC* pDC,
    const CSize& sizeDefault,
    BOOL bHorz);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
pro Kontext zařízení, který zobrazuje tlačítko pole se seznamem.

*sizeDefault*<br/>
pro Výchozí velikost tlačítka pole se seznamem

*bHorz*<br/>
pro Stav Dock ovládacího prvku ToolBar TRUE, pokud je panel nástrojů ukotvený vodorovně a FALSE, když je panel nástrojů ukotvený svisle.

### <a name="return-value"></a>Návratová hodnota

`SIZE` Struktura obsahující rozměry tlačítka pole se seznamem (v pixelech).

##  <a name="onchangeparentwnd"></a>CMFCToolBarComboBoxButton::OnChangeParentWnd

Volá se rozhraním, když se na nový panel nástrojů Vloží tlačítko pole se seznamem.

```
virtual void OnChangeParentWnd(CWnd* pWndParent);
```

### <a name="parameters"></a>Parametry

*pWndParent*<br/>
pro Ukazatel na nový nadřazený panel nástrojů.

##  <a name="onclick"></a>CMFCToolBarComboBoxButton:: Click

Volá se rozhraním, když uživatel klikne na tlačítko pole se seznamem.

```
virtual BOOL OnClick(
    CWnd* pWnd,
    BOOL bDelay = TRUE);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
pro Ukazatel na nadřazené okno tlačítka pole se seznamem.

*bDelay*<br/>
pro Vyhrazeno pro použití v odvozené třídě.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud metoda zpracovává událost; v opačném případě FALSE.

##  <a name="onctlcolor"></a>CMFCToolBarComboBoxButton::OnCtlColor

Volá se rozhraním, když uživatel změní barvu nadřazené panely nástrojů tak, aby se nastavila barva tlačítka pole se seznamem.

```
virtual HBRUSH OnCtlColor(
    CDC* pDC,
    UINT nCtlColor);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
pro Kontext zařízení, který zobrazuje tlačítko pole se seznamem.

*nCtlColor*<br/>
pro Nepoužívané.

### <a name="return-value"></a>Návratová hodnota

Zpracování štětce, který používá rozhraní k vykreslování pozadí tlačítka pole se seznamem.

### <a name="remarks"></a>Poznámky

Tato metoda také nastavuje barvu textu tlačítka pole se seznamem.

##  <a name="ondraw"></a>CMFCToolBarComboBoxButton:: Draw

Volá se rozhraním, aby se vykreslilo tlačítko pole se seznamem pomocí zadaných stylů a možností.

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

*Pdc*<br/>
pro Kontext zařízení, který zobrazí tlačítko.

*OBD*<br/>
pro Ohraničující obdélník tlačítka

*pImages*<br/>
pro Kolekce obrázků přidružených k tlačítku

*bHorz*<br/>
pro Stav Dock ovládacího prvku ToolBar TRUE, pokud je panel nástrojů ukotvený vodorovně a FALSE, když je panel nástrojů ukotvený svisle.

*bCustomizeMode*<br/>
pro Určuje, zda je aplikace v režimu přizpůsobení.

*bHighlight*<br/>
pro Určuje, zda má být zvýrazněno tlačítko pole se seznamem.

*bDrawBorder*<br/>
pro Určuje, zda se má vykreslit tlačítko pole se seznamem s ohraničením.

*bGrayDisabledButtons*<br/>
pro TRUE pro kreslení vybarvených zakázaných tlačítek; FALSE pro použití kolekce zakázaných imagí.

##  <a name="ondrawoncustomizelist"></a>CMFCToolBarComboBoxButton::OnDrawOnCustomizeList

Volá se rozhraním, aby se vykreslilo tlačítko pole se seznamem v podokně **příkazy** v dialogovém okně **přizpůsobit** .

```
virtual int OnDrawOnCustomizeList(
    CDC* pDC,
    const CRect& rect,
    BOOL bSelected);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
pro Kontext zařízení, který zobrazuje tlačítko pole se seznamem.

*OBD*<br/>
pro Ohraničující obdélník tlačítka pole se seznamem.

*bSelected*<br/>
pro TRUE, pokud je vybráno tlačítko pole se seznamem; v opačném případě FALSE.

### <a name="return-value"></a>Návratová hodnota

Šířka tlačítka pole se seznamem (v pixelech)

##  <a name="onglobalfontschanged"></a>  CMFCToolBarComboBoxButton::OnGlobalFontsChanged

Volá se rozhraním, aby se při změně písma aplikace nastavilo písmo tlačítka pole se seznamem.

```
virtual void OnGlobalFontsChanged();
```

##  <a name="onmove"></a>CMFCToolBarComboBoxButton::-Move

Volá se rozhraním, aby se změnilo umístění tlačítka pole se seznamem, když se přesune nadřazený panel nástrojů.

```
virtual void OnMove();
```

##  <a name="onshow"></a>CMFCToolBarComboBoxButton:: inshow

Volá se rozhraním, když je tlačítko pole se seznamem skryté nebo zobrazené.

```
virtual void OnShow(BOOL bShow);
```

### <a name="parameters"></a>Parametry

*bShow*<br/>
pro Určuje, zda se má skrýt nebo zobrazit tlačítko pole se seznamem.

##  <a name="onsize"></a>CMFCToolBarComboBoxButton::-size

Volá se rozhraním, aby se změnila velikost tlačítka pole se seznamem, když se změní velikost nadřazeného panelu nástrojů.

```
virtual void OnSize(int iSize);
```

### <a name="parameters"></a>Parametry

*iSize*<br/>
pro Nová šířka tlačítka pole se seznamem

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
pro Ukazatel na nadřazené okno pro tlačítko pole se seznamem.

*iButtonIndex*<br/>
pro ID tlačítka pole se seznamem

*wndToolTip*<br/>
pro Popisek, který má být spojen s tlačítkem pole se seznamem.

*str*<br/>
pro Text tipu nástroje

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud metoda zpracovává událost; v opačném případě FALSE.

##  <a name="removeallitems"></a>CMFCToolBarComboBoxButton::RemoveAllItems

Odstraní všechny položky ze seznamu a textových polí.

```
void RemoveAllItems();
```

### <a name="remarks"></a>Poznámky

Odebere všechny položky ze seznamu a textového ovládacího prvku pole se seznamem.

##  <a name="selectitem"></a>CMFCToolBarComboBoxButton::SelectItem

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
pro Index položky vycházející z nuly položky v poli se seznamem.

*bNotify*<br/>
pro TRUE pro upozorňování tlačítka pole se seznamem na výběr; v opačném případě FALSE.

*dwData*<br/>
pro Data přidružená k položce v seznamu.

*lpszText*<br/>
pro Text položky v poli se seznamem.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud byla metoda úspěšná; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

##  <a name="selectitemall"></a>CMFCToolBarComboBoxButton::SelectItemAll

Vybere položku v seznamu tlačítka pole se seznamem, které má zadané ID příkazu.

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
pro ID příkazu pole se seznamem, které obsahuje pole se seznamem

*iIndex*<br/>
pro Index položky vycházející z nuly položky v poli se seznamem. Hodnota-1 odstraní všechny aktuální výběry v seznamu a vymaže pole pro úpravy.

*dwData*<br/>
pro Data položky v poli se seznamem.

*lpszText*<br/>
pro Text položky v poli se seznamem.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud byla metoda úspěšná; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

##  <a name="serialize"></a>CMFCToolBarComboBoxButton:: serializovat

Přečte tento objekt z archivu nebo ho zapíše do archivu.

```
virtual void Serialize(CArchive& ar);
```

### <a name="parameters"></a>Parametry

*snížen*<br/>
[in, out] `CArchive` Objekt k serializaci.

### <a name="remarks"></a>Poznámky

Nastavení v `CArchive` objektu určují, zda tato metoda čte nebo zapisuje do archivu.

##  <a name="setaccdata"></a>CMFCToolBarComboBoxButton::SetACCData

Naplní zadaný `CAccessibilityData` objekt pomocí dat přístupnosti z tlačítka pole se seznamem.

```
virtual BOOL SetACCData(
    CWnd* pParent,
    CAccessibilityData& data);
```

### <a name="parameters"></a>Parametry

*pParent*<br/>
pro Nadřazené okno tlačítka pole se seznamem

*data*<br/>
mimo `CAccessibilityData` Objekt, který obdrží data přístupnosti z tlačítka pole se seznamem.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud byla metoda úspěšná; v opačném případě FALSE.

##  <a name="setcentervert"></a>CMFCToolBarComboBoxButton::SetCenterVert

Nastaví svislou polohu tlačítek pole se seznamem v aplikaci.

```
static void SetCenterVert(BOOL bCenterVert=TRUE);
```

### <a name="parameters"></a>Parametry

*bCenterVert*<br/>
pro TRUE pro vycentrovat tlačítko pole se seznamem na panelu nástrojů; Hodnota FALSE, pokud chcete zarovnat tlačítko pole se seznamem na horní okraj panelu nástrojů.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení jsou tlačítka pole se seznamem zarovnána nahoru.

##  <a name="setcontextmenuid"></a>CMFCToolBarComboBoxButton::SetContextMenuID

Nastaví ID prostředku místní nabídky pro tlačítko pole se seznamem.

```
void SetContextMenuID(UINT uiResID);
```

### <a name="parameters"></a>Parametry

*uiResID*<br/>
pro ID prostředku místní nabídky

##  <a name="setdropdownheight"></a>CMFCToolBarComboBoxButton::SetDropDownHeight

Nastaví výšku seznamu při jeho vyřazení.

```
void SetDropDownHeight(int nHeight);
```

### <a name="parameters"></a>Parametry

*nHeight*<br/>
pro Výška pole seznamu v pixelech

### <a name="remarks"></a>Poznámky

Výchozí výška je 150 pixelů.

##  <a name="setflatmode"></a>CMFCToolBarComboBoxButton::SetFlatMode

Nastaví plochý vzhled tlačítek pole se seznamem v aplikaci.

```
static void SetFlatMode(BOOL bFlat=TRUE);
```

### <a name="parameters"></a>Parametry

*bFlat*<br/>
pro TRUE pro zjednodušený vzhled stylu; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Výchozí plochý styl pro tlačítka pole se seznamem je FALSE.

##  <a name="setstyle"></a>CMFCToolBarComboBoxButton:: SetStyle

Nastaví zadaný styl pro tlačítko pole se seznamem a překreslí ovládací prvek, pokud není zakázán.

```
virtual void SetStyle(UINT nStyle);
```

### <a name="parameters"></a>Parametry

*nStyle*<br/>
pro Bitová kombinace stylů panelu nástrojů (nebo).

### <a name="remarks"></a>Poznámky

Seznam stylů tlačítek panelu nástrojů viz [styly ovládacích prvků panelu nástrojů](../../mfc/reference/toolbar-control-styles.md)

##  <a name="settext"></a>CMFCToolBarComboBoxButton::SetText

Nastaví text v poli pro úpravy na tlačítku pole se seznamem.

```
void SetText(LPCTSTR lpszText);
```

### <a name="parameters"></a>Parametry

*lpszText*<br/>
pro Ukazatel na řetězec obsahující text pro textové pole.

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBarButton – třída](../../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[CComboBox – třída](../../mfc/reference/ccombobox-class.md)<br/>
[CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)<br/>
[Návod: Umístění ovládacích prvků na panely nástrojů](../../mfc/walkthrough-putting-controls-on-toolbars.md)
