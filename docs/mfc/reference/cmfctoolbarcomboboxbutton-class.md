---
title: Třída CMFCToolBarComboBoxButton
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
ms.openlocfilehash: 0d003bdacf13403ad8dc4be4ec7e6f71ea57d156
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372193"
---
# <a name="cmfctoolbarcomboboxbutton-class"></a>Třída CMFCToolBarComboBoxButton

Tlačítko panelu nástrojů, které obsahuje ovládací prvek pole se seznamem [(Třída CComboBox).](../../mfc/reference/ccombobox-class.md)

## <a name="syntax"></a>Syntaxe

```
class CMFCToolBarComboBoxButton : public CMFCToolBarButton
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CMFCToolBarComboBoxButton::CMFCToolBarComboBoxButton](#cmfctoolbarcomboboxbutton)|Vytvoří `CMFCToolBarComboBoxButton`.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CMFCToolBarComboBoxButton::Přidatpoložku](#additem)|Přidá položku na konec seznamu polí se seznamem.|
|[CMFCToolBarComboBoxButton::Přidat položku Typu Třídění](#addsorteditem)|Přidá položku do seznamu polí se seznamem. Pořadí položek v seznamu je `Compare`určeno .|
|[CMFCToolBarComboBoxButton::Porovnat](#compare)|Porovná dvě položky. Nazývá se řazení `AddSortedItems` položek, které se přidá do seznamu polí se seznamem.|
|[CMFCToolBarComboBoxButton::CreateEdit](#createedit)|Vytvoří nový ovládací prvek pro úpravy tlačítka pole se seznamem.|
|[CMFCToolBarComboBoxButton::DeleteItem](#deleteitem)|Odstraní položku ze seznamu polí se seznamem.|
|[CMFCToolBarComboBoxButton::FindItem](#finditem)|Vrátí index položky, která obsahuje zadaný řetězec.|
|[CMFCToolBarComboBoxButton::GetByCmd](#getbycmd)|Vrátí ukazatel na tlačítko pole se seznamem se zadaným ID příkazu.|
|[CMFCToolBarComboBoxButton::GetComboBox](#getcombobox)|Vrátí ukazatel na ovládací prvek pole se seznamem, který je vložen do tlačítka pole se seznamem.|
|[CMFCToolBarComboBoxButton::GetCount](#getcount)|Vrátí počet položek v seznamu polí se seznamem.|
|[CMFCToolBarComboBoxButton::GetCountAll](#getcountall)|Vyhledá tlačítko pole se seznamem, které má zadané ID příkazu. Vrátí počet položek v seznamu polí se seznamem tohoto tlačítka.|
|[CMFCToolBarComboBoxButton::GetCurSel](#getcursel)|Vrátí index vybrané položky v seznamu polí se seznamem.|
|[CMFCToolBarComboBoxButton::GetCurSelAll](#getcurselall)|Vyhledá tlačítko pole se seznamem, které má zadané ID příkazu, a vrátí index vybrané položky v seznamu polí se seznamem tohoto tlačítka.|
|[CMFCToolBarComboBoxButton::GetEditCtrl](#geteditctrl)|Vrátí ukazatel na ovládací prvek pro úpravy, který je vložen do tlačítka pole se seznamem.|
|[CMFCToolBarComboBoxButton::GetItem](#getitem)|Vrátí řetězec, který je přidružen k zadanému indexu v seznamu polí se seznamem.|
|[CMFCToolBarComboBoxButton::GetItemAll](#getitemall)|Vyhledá tlačítko pole se seznamem, které má zadané ID příkazu, a vrátí řetězec přidružený k indexu v seznamu polí se seznamem tohoto tlačítka.|
|[CMFCToolBarComboBoxButton::GetItemData](#getitemdata)|Vrátí 32bitovou hodnotu přidruženou k zadanému indexu v seznamu polí se seznamem.|
|[CMFCToolBarComboBoxButton::GetItemDataAll](#getitemdataall)|Vyhledá tlačítko pole se seznamem, které má zadané ID příkazu, a vrátí 32bitovou hodnotu přidruženou k indexu v seznamu polí se seznamem tohoto tlačítka.|
|[CMFCToolBarComboBoxButton::GetItemDataPtrAll](#getitemdataptrall)|Vyhledá tlačítko pole se seznamem, které má zadané ID příkazu. Načte 32bitovou hodnotu, která je přidružena index v seznamu polí se seznamem tohoto tlačítka a vrátí 32bitovou hodnotu jako ukazatel.|
|[CMFCToolBarComboBoxButton::GetText](#gettext)|Vrátí text z ovládacího prvku upravit pole se seznamem.|
|[CMFCToolBarComboBoxButton::GetTextAll](#gettextall)|Vyhledá tlačítko pole se seznamem, které má zadané ID příkazu, a vrátí text z ovládacího prvku upravit toto tlačítko.|
|[CMFCToolBarComboBoxButton::IsCenterVert](#iscentervert)|Určuje, zda jsou tlačítka pole se seznamem v aplikaci vystředěna nebo zarovnána s horní částí panelu nástrojů.|
|[CMFCToolBarComboBoxButton::Režim IsFlatMode](#isflatmode)|Určuje, zda mají tlačítka pole se seznamem v aplikaci plochý vzhled.|
|[CMFCToolBarComboBoxButton::RemoveAllItems](#removeallitems)|Odebere všechny položky ze seznamu a upravit ovládací prvek pole se seznamem.|
|[CMFCToolBarComboBoxButton::SelectItem](#selectitem)|Vybere položku v poli se seznamem podle indexu, 32bitové hodnoty nebo řetězce a upozorní ovládací prvek pole se seznamem o výběru.|
|[CMFCToolBarComboBoxButton::SelectItemAll](#selectitemall)|Vyhledá tlačítko pole se seznamem, které má zadané ID příkazu. Volání `SelectItem` vybrat položku v poli se seznamem tohoto tlačítka podle jeho řetězec, index nebo 32bitovou hodnotu.|
|[CMFCToolBarComboBoxButton::SetCenterVert](#setcentervert)|Určuje, zda jsou tlačítka pole se seznamem v aplikaci vystředěna svisle nebo zarovnána s horní částí panelu nástrojů.|
|[CMFCToolBarComboBoxButton::SetDropDownHeight](#setdropdownheight)|Nastaví výšku rozevíracího seznamu.|
|[CMFCToolBarComboBoxButton::SetFlatMode](#setflatmode)|Určuje, zda mají tlačítka pole se seznamem v aplikaci plochý vzhled.|

## <a name="remarks"></a>Poznámky

Chcete-li na panel nástrojů přidat tlačítko pole se seznamem, postupujte takto:

1. Zarezervujte si pro tlačítko zástupný identifikátor ID prostředku v nadřazeném prostředku panelu nástrojů.

2. Vytvořte `CMFCToolBarComboBoxButton` objekt.

3. V obslužné rutině zprávy, která zpracovává zprávu AFX_WM_RESETTOOLBAR, nahraďte tlačítko fiktivní ho za nové pole se seznamem pomocí tlačítka [CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton).

Další informace naleznete [v tématu Návod: Uvedení ovládacích prvků na panely nástrojů](../../mfc/walkthrough-putting-controls-on-toolbars.md). Příklad tlačítka panelu nástrojů pole se seznamem naleznete v příkladu projektu VisualStudioDemo.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak používat různé `CMFCToolBarComboBoxButton` metody ve třídě. Příklad ukazuje, jak povolit pole pro úpravy a pole se seznamem, nastavit svislou polohu tlačítek pole se seznamem v aplikaci, nastavit výšku seznamu při jeho pádu dolů, nastavit plochý vzhled tlačítek pole se seznamem v aplikaci a nastavit text v textovém poli tlačítka pole se seznamem. Tento fragment kódu je součástí [ukázky ukázky aplikace Visual Studio](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_VisualStudioDemo#36](../../mfc/codesnippet/cpp/cmfctoolbarcomboboxbutton-class_1.cpp)]
[!code-cpp[NVC_MFC_VisualStudioDemo#37](../../mfc/codesnippet/cpp/cmfctoolbarcomboboxbutton-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CmFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

[CmFCToolBarComboBoxTlačítko](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxtoolbarcomboboxbutton.h

## <a name="cmfctoolbarcomboboxbuttonadditem"></a><a name="additem"></a>CMFCToolBarComboBoxButton::Přidatpoložku

Připojí jedinečnou položku do seznamu.

```
virtual INT_PTR AddItem(
    LPCTSTR lpszItem,
    DWORD_PTR dwData=0);
```

### <a name="parameters"></a>Parametry

*lpszPoložka*<br/>
[v] Text položky, kterou chcete přidat do seznamu.

*dwData*<br/>
[v] Data přidružená k položce, která chcete přidat do seznamu.

### <a name="return-value"></a>Návratová hodnota

Index poslední položky v seznamu.

### <a name="remarks"></a>Poznámky

Tuto metodu nepoužívejte při řazení stylu seznamu.

Pokud je text položky již v seznamu, nová data se uloží s existující položkou. Hledání položky rozlišuje malá a velká písmena.

## <a name="cmfctoolbarcomboboxbuttonaddsorteditem"></a><a name="addsorteditem"></a>CMFCToolBarComboBoxButton::Přidat položku Typu Třídění

Přidá položku do seznamu v pořadí, které je definováno [compare](#compare) metodou.

```
virtual INT_PTR AddSortedItem(
    LPCTSTR lpszItem,
    DWORD_PTR dwData=0);
```

### <a name="parameters"></a>Parametry

*lpszPoložka*<br/>
[v] Text položky, kterou chcete přidat do seznamu.

*dwData*<br/>
[v] Data přidružená k položce, která chcete přidat do seznamu.

### <a name="return-value"></a>Návratová hodnota

Index položky, která byla přidána do seznamu.

### <a name="remarks"></a>Poznámky

Tato funkce slouží k přidání položek do seznamu v určitém pořadí.

## <a name="cmfctoolbarcomboboxbuttoncanbestretched"></a><a name="canbestretched"></a>CMFCToolBarComboBoxButton::CanBeStretched

Označuje, zda se může změnit velikost tlačítka pole se seznamem.

```
virtual BOOL CanBeStretched() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA.

## <a name="cmfctoolbarcomboboxbuttoncmfctoolbarcomboboxbutton"></a><a name="cmfctoolbarcomboboxbutton"></a>CMFCToolBarComboBoxButton::CMFCToolBarComboBoxButton

Vytvoří objekt [CMFCToolBarComboBoxButton.](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)

```
CMFCToolBarComboBoxButton(
    UINT uiID,
    int iImage,
    DWORD dwStyle=CBS_DROPDOWNLIST,
    int iWidth=0);
```

### <a name="parameters"></a>Parametry

*uiID*<br/>
[v] ID příkazu nového tlačítka.

*iImage*<br/>
[v] Index obrázku obrázku přidruženého k novému tlačítku.

*dwStyl*<br/>
[v] Styl nového tlačítka.

*iŠířka*<br/>
[v] Šířka nového tlačítka v pixelech.

### <a name="remarks"></a>Poznámky

Výchozí šířka je 150 pixelů.

Seznam stylů tlačítek panelu nástrojů naleznete v tématu [Styly ovládacích prvků nástrojů](../../mfc/reference/toolbar-control-styles.md)

## <a name="cmfctoolbarcomboboxbuttoncleardata"></a><a name="cleardata"></a>CMFCToolBarComboBoxButton::ClearData

Odstraní uživatelem definovaná data.

```
virtual void ClearData();
```

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení tato metoda neprovede žádnou akci. Přepsat tuto metodu v odvozené třídě, pokud chcete odstranit všechna uživatelem definovaná data.

## <a name="cmfctoolbarcomboboxbuttoncompare"></a><a name="compare"></a>CMFCToolBarComboBoxButton::Porovnat

Porovná dva řetězce.

```
virtual int Compare(
    LPCTSTR lpszItem1,
    LPCTSTR lpszItem2);
```

### <a name="parameters"></a>Parametry

*lpszPoložka1*<br/>
[v] První řetězec porovnat.

*lpszPoložka2*<br/>
[v] Druhý řetězec porovnat.

### <a name="return-value"></a>Návratová hodnota

Hodnota, která označuje lexikografický vztah rozlišující malá a velká písmena mezi řetězci. V následující tabulce jsou uvedeny možné hodnoty:

|Hodnota|Popis|
|-----------|-----------------|
|\<0|První řetězec je menší než druhý.|
|0|První řetězec se rovná druhému.|
|> 0|První řetězec je větší než druhý.|

### <a name="remarks"></a>Poznámky

Přepište tuto metodu a změňte způsob řazení položek v seznamu.

Porovnání se rozlišuje malá a velká písmena.

Tato metoda je volána pouze z [AddSortedItem](#addsorteditem) metoda.

## <a name="cmfctoolbarcomboboxbuttoncopyfrom"></a><a name="copyfrom"></a>CMFCToolBarComboBoxButton::CopyFrom

Zkopíruje stav zadaného `CMFCToolBarComboBoxButton` na aktuální objekt.

```
virtual void CopyFrom(const CMFCToolBarButton& src);
```

### <a name="parameters"></a>Parametry

*src*<br/>
[v] Zdrojový `CMFCToolBarComboBoxButton` objekt.

## <a name="cmfctoolbarcomboboxbuttoncreatecombo"></a><a name="createcombo"></a>CMFCToolBarComboBoxButton::CreateCombo

Vytvoří nové pole se seznamem pro tlačítko pole se seznamem.

```
virtual CComboBox* CreateCombo(
    CWnd* pWndParent,
    const CRect& rect);
```

### <a name="parameters"></a>Parametry

*pWndParent*<br/>
[v] Ukazatel na nadřazené okno tlačítka.

*Rect*<br/>
[v] Ohraničující obdélník pole se seznamem.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na nové pole se seznamem, pokud byla metoda úspěšná; jinak NULL.

## <a name="cmfctoolbarcomboboxbuttoncreateedit"></a><a name="createedit"></a>CMFCToolBarComboBoxButton::CreateEdit

Vytvoří nové textové pole pro tlačítko pole se seznamem.

```
virtual CMFCToolBarComboBoxEdit* CreateEdit(
    CWnd* pWndParent,
    const CRect& rect,
    DWORD dwEditStyle);
```

### <a name="parameters"></a>Parametry

*pWndParent*<br/>
[v] Ukazatel na nadřazené okno tlačítka.

*Rect*<br/>
[v] Ohraničující obdélník nového textového pole.

*dwEditstyl*<br/>
[v] Styl ovládání nového textového pole

### <a name="return-value"></a>Návratová hodnota

Ukazatel na nové pole pro úpravy, pokud byla metoda úspěšná; jinak NULL.

### <a name="remarks"></a>Poznámky

Framework volá tuto metodu při vytvoření nového textového pole pro tlačítko pole se seznamem. Přepsat tuto metodu změnit způsob vytvoření [CMFCToolBarComboBoxEdit.](../../mfc/reference/cmfctoolbarcomboboxedit-class.md)

## <a name="cmfctoolbarcomboboxbuttondeleteitem"></a><a name="deleteitem"></a>CMFCToolBarComboBoxButton::DeleteItem

Odstraní zadanou položku ze seznamu.

```
BOOL DeleteItem(int iIndex);
BOOL DeleteItem(DWORD_PTR dwData);
BOOL DeleteItem(LPCTSTR lpszText);
```

### <a name="parameters"></a>Parametry

*iIndex*<br/>
[v] Index na základě nuly položky, která má být odstraněna.

*dwData*<br/>
[v] Data přidružená k položce, která má být odstraněna.

*lpszText*<br/>
[v] Text položky, která má být odstraněna. Pokud existuje více položek se stejným textem, první položka se odstraní.

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud byla položka lokalizována a úspěšně odstraněna; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

## <a name="cmfctoolbarcomboboxbuttonduplicatedata"></a><a name="duplicatedata"></a>CMFCToolBarComboBoxButton::DuplicateData

Duplikuje uživatelem definovaná data.

```
virtual void DuplicateData();
```

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení tato metoda neprovede žádnou akci. Přepsat tuto metodu v odvozené třídě, pokud chcete zkopírovat všechna uživatelem definovaná data.

## <a name="cmfctoolbarcomboboxbuttonenablewindow"></a><a name="enablewindow"></a>CMFCToolBarComboBoxButton::EnableWindow

Povolí nebo zakáže pole pro úpravy a seseznam.

```
virtual void EnableWindow(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parametry

*bEnable*<br/>
[v] TRUE povolit editační a sektonová pole; FALSE zakázat upravit a seseznampolí.

### <a name="remarks"></a>Poznámky

Pokud je zakázáno, ovládací prvky nelze aktivovat a nemůže přijmout vstup uživatele.

## <a name="cmfctoolbarcomboboxbuttonexporttomenubutton"></a><a name="exporttomenubutton"></a>CMFCToolBarComboBoxButton::ExportToMenuButton

Zkopíruje řetězec z tabulky aplikačních řetězců do zadané nabídky pomocí ID příkazu příkazu pole se seznamem.

```
virtual BOOL ExportToMenuButton(CMFCToolBarMenuButton& menuButton) const;
```

### <a name="parameters"></a>Parametry

*menuButton*<br/>
[out] Odkaz na tlačítko nabídky.

### <a name="return-value"></a>Návratová hodnota

Vždy TRUE

## <a name="cmfctoolbarcomboboxbuttonfinditem"></a><a name="finditem"></a>CMFCToolBarComboBoxButton::FindItem

Vrátí index první položky v seznamu, který obsahuje zadaný řetězec.

```
int FindItem(LPCTSTR lpszText) const;
```

### <a name="parameters"></a>Parametry

*lpszText*<br/>
[v] Text, pro který chcete hledat v seznamu.

### <a name="return-value"></a>Návratová hodnota

Index položky; nebo CB_ERR, pokud položka není nalezena.

### <a name="remarks"></a>Poznámky

## <a name="cmfctoolbarcomboboxbuttongetbycmd"></a><a name="getbycmd"></a>CMFCToolBarComboBoxButton::GetByCmd

Získá ukazatel na tlačítko pole se seznamem, který má zadané ID příkazu.

```
static CMFCToolBarComboBoxButton* GetByCmd(
    UINT uiCmd,
    BOOL bIsFocus=FALSE);
```

### <a name="parameters"></a>Parametry

*uiCmd*<br/>
[v] ID příkazu tlačítka pole se seznamem.

*bIsFocus*<br/>
[v] TRUE pro vyhledávání pouze zaostřených tlačítek; False pro vyhledávání všech tlačítek.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na tlačítko pole se seznamem; nebo NULL, pokud tlačítko není nalezeno.

### <a name="remarks"></a>Poznámky

## <a name="cmfctoolbarcomboboxbuttongetcombobox"></a><a name="getcombobox"></a>CMFCToolBarComboBoxButton::GetComboBox

Vrátí ukazatel na pole se seznamem v poli se seznamem.

```
CComboBox* GetComboBox() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na [ccombobox třídy](../../mfc/reference/ccombobox-class.md) objektu, pokud metoda byla úspěšná; jinak NULL.

### <a name="remarks"></a>Poznámky

## <a name="cmfctoolbarcomboboxbuttongetcontextmenuid"></a><a name="getcontextmenuid"></a>CMFCToolBarComboBoxButton::GetContextMenuID

Získá ID prostředku místní nabídky pro tlačítko pole se seznamem.

```
UINT GetContextMenuID();
```

### <a name="return-value"></a>Návratová hodnota

ID prostředku místní nabídky.

## <a name="cmfctoolbarcomboboxbuttongetcount"></a><a name="getcount"></a>CMFCToolBarComboBoxButton::GetCount

Vrátí počet položek v seznamu.

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet položek v seznamu.

### <a name="remarks"></a>Poznámky

## <a name="cmfctoolbarcomboboxbuttongetcountall"></a><a name="getcountall"></a>CMFCToolBarComboBoxButton::GetCountAll

Získá počet položek v seznamu tlačítka pole se seznamem, který má zadané ID příkazu.

```
static int GetCountAll(UINT uiCmd);
```

### <a name="parameters"></a>Parametry

*uiCmd*<br/>
[v] ID příkazu tlačítka pole se seznamem.

### <a name="return-value"></a>Návratová hodnota

Počet položek v seznamu; v opačném případě CB_ERR, pokud není nalezeno tlačítko pole se seznamem.

### <a name="remarks"></a>Poznámky

## <a name="cmfctoolbarcomboboxbuttongetcursel"></a><a name="getcursel"></a>CMFCToolBarComboBoxButton::GetCurSel

Získá index aktuálně vybrané položky v seznamu.

```
int GetCurSel() const;
```

### <a name="return-value"></a>Návratová hodnota

Index aktuálně vybrané položky v seznamu; nebo CB_ERR, pokud není vybrána žádná položka.

### <a name="remarks"></a>Poznámky

Index seznamu je založen na nule.

## <a name="cmfctoolbarcomboboxbuttongetcurselall"></a><a name="getcurselall"></a>CMFCToolBarComboBoxButton::GetCurSelAll

Vrátí index aktuálně vybrané položky v seznamu tlačítka pole se seznamem, které má zadané ID příkazu.

```
static int GetCurSelAll(UINT uiCmd);
```

### <a name="parameters"></a>Parametry

*uiCmd*<br/>
[v] ID příkazu tlačítka pole se seznamem.

### <a name="return-value"></a>Návratová hodnota

Index aktuálně vybrané položky v seznamu; v opačném případě CB_ERR, pokud není vybrána žádná položka nebo není nalezeno tlačítko pole se seznamem.

### <a name="remarks"></a>Poznámky

Index seznamu je založen na nule.

## <a name="cmfctoolbarcomboboxbuttongeteditctrl"></a><a name="geteditctrl"></a>CMFCToolBarComboBoxButton::GetEditCtrl

Vrátí ukazatel na editační pole v poli se seznamem.

```
virtual CEdit* GetEditCtrl();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na pole pro úpravy, pokud byla metoda úspěšná; jinak NULL.

### <a name="remarks"></a>Poznámky

## <a name="cmfctoolbarcomboboxbuttongethwnd"></a><a name="gethwnd"></a>CMFCToolBarComboBoxButton::GetHwnd

Vrátí popisovač okna pro pole se seznamem.

```
virtual HWND GetHwnd();
```

### <a name="return-value"></a>Návratová hodnota

Popisovač okna nebo NULL, pokud pole se seznamem není přidružen k objektu okna.

## <a name="cmfctoolbarcomboboxbuttongetitem"></a><a name="getitem"></a>CMFCToolBarComboBoxButton::GetItem

Vrátí řetězec přidružený k položce v zadaném indexu v seznamu.

```
LPCTSTR GetItem(int iIndex=-1) const;
```

### <a name="parameters"></a>Parametry

*iIndex*<br/>
[v] Nulový index položky v seznamu.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na řetězec, který je přidružen k položce; v opačném případě null, pokud je parametr indexu neplatný, nebo pokud je parametr indexu -1 a v poli se seznamem není žádná vybraná položka.

### <a name="remarks"></a>Poznámky

Parametr indexu -1 vrátí řetězec položky, která je aktuálně vybrána.

## <a name="cmfctoolbarcomboboxbuttongetitemall"></a><a name="getitemall"></a>CMFCToolBarComboBoxButton::GetItemAll

Vrátí řetězec přidružený k položce v zadaném indexu v seznamu tlačítka pole se seznamem, který má zadané ID příkazu.

```
static LPCTSTR GetItemAll(
    UINT uiCmd,
    int iIndex=-1);
```

### <a name="parameters"></a>Parametry

*uiCmd*<br/>
[v] ID příkazu tlačítka pole se seznamem.

*iIndex*<br/>
[v] Nulový index položky v seznamu.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na řetězec položky, pokud byla metoda úspěšná; v opačném případě null, pokud je index neplatný, není nalezeno tlačítko pole se seznamem nebo pokud index je -1 a není žádná vybraná položka v poli se seznamem.

### <a name="remarks"></a>Poznámky

Hodnota indexu -1 vrátí řetězec položky, která je aktuálně vybrána.

## <a name="cmfctoolbarcomboboxbuttongetitemdata"></a><a name="getitemdata"></a>CMFCToolBarComboBoxButton::GetItemData

Vrátí data přidružená k položce v určitém indexu v seznamu.

```
DWORD_PTR GetItemData(int iIndex=-1) const;
```

### <a name="parameters"></a>Parametry

*iIndex*<br/>
[v] Nulový index položky v seznamu.

### <a name="return-value"></a>Návratová hodnota

Data přidružená k položce; nebo 0, pokud položka neexistuje.

### <a name="remarks"></a>Poznámky

Parametr indexu -1 vrátí data přidružená k aktuálně vybrané položce.

## <a name="cmfctoolbarcomboboxbuttongetitemdataall"></a><a name="getitemdataall"></a>CMFCToolBarComboBoxButton::GetItemDataAll

Vrátí data přidružená k položce v určitém indexu v seznamu tlačítka pole se seznamem, které má konkrétní ID příkazu.

```
static DWORD_PTR GetItemDataAll(
    UINT uiCmd,
    int iIndex=-1);
```

### <a name="parameters"></a>Parametry

*uiCmd*<br/>
[v] ID příkazu tlačítka pole se seznamem.

*iIndex*<br/>
[v] Nulový index položky v seznamu.

### <a name="return-value"></a>Návratová hodnota

Data přidružená k položce, pokud byla metoda úspěšná; v opačném případě 0, pokud zadaný index není platný, nebo CB_ERR, pokud není nalezeno tlačítko pole se seznamem.

### <a name="remarks"></a>Poznámky

Parametr indexu -1 vrátí data přidružená k aktuálně vybrané položce.

## <a name="cmfctoolbarcomboboxbuttongetitemdataptrall"></a><a name="getitemdataptrall"></a>CMFCToolBarComboBoxButton::GetItemDataPtrAll

Vrátí data přidružená k položce v určitém indexu v seznamu tlačítka pole se seznamem, které má konkrétní ID příkazu. Tato data jsou vrácena jako ukazatel.

```
static void* GetItemDataPtrAll(
    UINT uiCmd,
    int iIndex=-1);
```

### <a name="parameters"></a>Parametry

*uiCmd*<br/>
[v] ID příkazu tlačítka pole se seznamem.

*iIndex*<br/>
[v] Nulový index položky v seznamu.

### <a name="return-value"></a>Návratová hodnota

Ukazatel přidružený k položce, pokud byla metoda úspěšná; jinak -1, pokud dojde k chybě, nebo NULL, pokud není nalezeno tlačítko pole se seznamem.

### <a name="remarks"></a>Poznámky

## <a name="cmfctoolbarcomboboxbuttongetprompt"></a><a name="getprompt"></a>CMFCToolBarComboBoxButton::Výzva k získání

Vrátí řetězec výzvy pro tlačítko pole se seznamem.

```
virtual CString GetPrompt() const;
```

### <a name="return-value"></a>Návratová hodnota

Řetězec výzvy.

### <a name="remarks"></a>Poznámky

Tato metoda není aktuálně implementována.

## <a name="cmfctoolbarcomboboxbuttongettext"></a><a name="gettext"></a>CMFCToolBarComboBoxButton::GetText

Získá text v textovém poli.

```
LPCTSTR GetText() const;
```

### <a name="return-value"></a>Návratová hodnota

Text v textovém poli.

### <a name="remarks"></a>Poznámky

## <a name="cmfctoolbarcomboboxbuttongettextall"></a><a name="gettextall"></a>CMFCToolBarComboBoxButton::GetTextAll

Získá text v textovém poli pole se seznamem tlačítko, které má zadané id příkazu.

```
static LPCTSTR GetTextAll(UINT uiCmd);
```

### <a name="parameters"></a>Parametry

*uiCmd*<br/>
[v] ID příkazu konkrétního tlačítka pole se seznamem.

### <a name="return-value"></a>Návratová hodnota

Text v textovém poli, pokud byla metoda úspěšná; jinak NULL.

### <a name="remarks"></a>Poznámky

## <a name="cmfctoolbarcomboboxbuttonhasfocus"></a><a name="hasfocus"></a>CMFCToolBarComboBoxButton::HasFocus

Označuje, zda pole se seznamem aktuálně má fokus.

```
virtual BOOL HasFocus() const;
```

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud pole se seznamem má aktuálně fokus; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

Tato metoda také vrátí hodnotu PRAVDA, pokud je aktuálně fokus fokusováno v libovolném podřízeném okně pole se seznamem.

## <a name="cmfctoolbarcomboboxbuttoniscentervert"></a><a name="iscentervert"></a>CMFCToolBarComboBoxButton::IsCenterVert

Vrátí svislou polohu tlačítek pole se seznamem v aplikaci.

```
static BOOL IsCenterVert();
```

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud jsou tlačítka vystředěna; FALSE, pokud jsou tlačítka zarovnána v horní části.

### <a name="remarks"></a>Poznámky

## <a name="cmfctoolbarcomboboxbuttonisflatmode"></a><a name="isflatmode"></a>CMFCToolBarComboBoxButton::Režim IsFlatMode

Vrátí plochý vzhled tlačítek pole se seznamem v aplikaci.

```
static BOOL IsFlatMode();
```

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud mají tlačítka plochý styl; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

Výchozí plochý styl pro tlačítka pole se seznamem je FALSE.

## <a name="cmfctoolbarcomboboxbuttonisownerof"></a><a name="isownerof"></a>CMFCToolBarComboBoxButton::JeOwnerOf

Označuje, zda je zadaný popisovač přidružen k tlačítku pole se seznamem nebo k jednomu z jeho podřízených.

```
virtual BOOL IsOwnerOf(HWND hwnd);
```

### <a name="parameters"></a>Parametry

*Hwnd*<br/>
[v] Klika okna.

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud je rukojeť přidružena k tlačítku pole se seznamem nebo k jednomu z jeho podřízených; jinak NEPRAVDA.

## <a name="cmfctoolbarcomboboxbuttonisribbonbutton"></a><a name="isribbonbutton"></a>CMFCToolBarComboBoxButton::IsRibbonButton

Označuje, zda se tlačítko pole se seznamem nachází na panelu pásu karet.

```
BOOL IsRibbonButton() const;
```

### <a name="return-value"></a>Návratová hodnota

Vždy FALSE

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení tato metoda vždy vrátí hodnotu FALSE, což znamená, že tlačítko pole se seznamem se nikdy nezobrazí na panelu pásu karet.

## <a name="cmfctoolbarcomboboxbuttoniswindowvisible"></a><a name="iswindowvisible"></a>CMFCToolBarComboBoxButton::IsWindowVisible

Vrátí stav viditelnosti tlačítka pole se seznamem.

```
virtual BOOL IsWindowVisible();
```

### <a name="return-value"></a>Návratová hodnota

Stav viditelnosti tlačítka pole se seznamem.

## <a name="cmfctoolbarcomboboxbuttonnotifycommand"></a><a name="notifycommand"></a>CMFCToolBarComboBoxButton::Příkaz NotifyCommand

Označuje, zda tlačítko pole se seznamem zprávu zpracuje.

```
virtual BOOL NotifyCommand(int iNotifyCode);
```

### <a name="parameters"></a>Parametry

*iNotifyCode*<br/>
[v] Zpráva s oznámením, která je přidružena k příkazu.

### <a name="return-value"></a>Návratová hodnota

Zda tlačítko pole se seznamem zpracovává zprávu.

## <a name="cmfctoolbarcomboboxbuttononaddtocustomizepage"></a><a name="onaddtocustomizepage"></a>CMFCToolBarComboBoxButton::OnAddToCustomizePage

Volat rámci při přidání tlačítka do dialogového okna **Přizpůsobit.**

```
virtual void OnAddToCustomizePage();
```

## <a name="cmfctoolbarcomboboxbuttononcalculatesize"></a><a name="oncalculatesize"></a>CMFCToolBarComboBoxButton::OnCalculateSize

Volat rámci pro výpočet velikosti tlačítka.

```
virtual SIZE OnCalculateSize(
    CDC* pDC,
    const CSize& sizeDefault,
    BOOL bHorz);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[v] Kontext zařízení, který zobrazuje tlačítko pole se seznamem.

*sizeDefault*<br/>
[v] Výchozí velikost tlačítka pole se seznamem.

*bHorz*<br/>
[v] Stav ukotvení nadřazeného panelu nástrojů. Pravda, pokud je panel nástrojů ukotven vodorovně a nepravda, když je panel nástrojů ukotven svisle.

### <a name="return-value"></a>Návratová hodnota

Struktura, `SIZE` která obsahuje rozměry tlačítka pole se seznamem v obrazových bodech.

## <a name="cmfctoolbarcomboboxbuttononchangeparentwnd"></a><a name="onchangeparentwnd"></a>CMFCToolBarComboBoxButton::OnChangeParentWnd

Volat rámci při pole se seznamem tlačítko je vložen do nového panelu nástrojů.

```
virtual void OnChangeParentWnd(CWnd* pWndParent);
```

### <a name="parameters"></a>Parametry

*pWndParent*<br/>
[v] Ukazatel na nový nadřazený panel nástrojů.

## <a name="cmfctoolbarcomboboxbuttononclick"></a><a name="onclick"></a>CMFCToolBarComboBoxButton::Při klepnutí

Volat rámci, když uživatel klikne na tlačítko pole se seznamem.

```
virtual BOOL OnClick(
    CWnd* pWnd,
    BOOL bDelay = TRUE);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
[v] Ukazatel na nadřazené okno tlačítka pole se seznamem.

*bZpoždění*<br/>
[v] Vyhrazeno pro použití v odvozené třídě.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud metoda zpracovává událost; jinak NEPRAVDA.

## <a name="cmfctoolbarcomboboxbuttononctlcolor"></a><a name="onctlcolor"></a>CMFCToolBarComboBoxButton::OnCtlColor

Volat rámci při uživatel změní barvu nadřazeného panelu nástrojů nastavit barvu tlačítka pole se seznamem.

```
virtual HBRUSH OnCtlColor(
    CDC* pDC,
    UINT nCtlColor);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[v] Kontext zařízení, který zobrazuje tlačítko pole se seznamem.

*nCtlColor*<br/>
[v] Nepoužité.

### <a name="return-value"></a>Návratová hodnota

Zpracovat štětec, který rámec používá k malování pozadí tlačítka pole se seznamem.

### <a name="remarks"></a>Poznámky

Tato metoda také nastaví barvu textu tlačítka pole se seznamem.

## <a name="cmfctoolbarcomboboxbuttonondraw"></a><a name="ondraw"></a>CMFCToolBarComboBoxButton::OnDraw

Volat rámci nakreslit tlačítko pole se seznamem pomocí zadaných stylů a možností.

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
[v] Kontext zařízení, který zobrazí tlačítko.

*Rect*<br/>
[v] Ohraničovací obdélník tlačítka.

*pObrázky*<br/>
[v] Kolekce obrázků, která je přidružena k tlačítku.

*bHorz*<br/>
[v] Stav ukotvení nadřazeného panelu nástrojů. Pravda, pokud je panel nástrojů ukotven vodorovně a nepravda, když je panel nástrojů ukotven svisle.

*bPřizpůsobitrežim*<br/>
[v] Zda je aplikace v režimu přizpůsobení.

*bZvýraznění*<br/>
[v] Zda nakreslit tlačítko pole se seznamem zvýrazněné.

*bDrawBorder*<br/>
[v] Určuje, zda se má nakreslit tlačítko pole se seznamem s ohraničením.

*bGrayDisabledTlačítka*<br/>
[v] TRUE pro kreslení stínovaných zakázaných tlačítek; FALSE použít kolekci zakázaných obrázků.

## <a name="cmfctoolbarcomboboxbuttonondrawoncustomizelist"></a><a name="ondrawoncustomizelist"></a>CMFCToolBarComboBoxButton::OnDrawOnCustomizeList

Volat rámci nakreslit tlačítko pole se seznamem v podokně **příkazy** dialogového okna **Přizpůsobit.**

```
virtual int OnDrawOnCustomizeList(
    CDC* pDC,
    const CRect& rect,
    BOOL bSelected);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[v] Kontext zařízení, který zobrazuje tlačítko pole se seznamem.

*Rect*<br/>
[v] Ohraničovací obdélník tlačítka pole se seznamem.

*bVybrané*<br/>
[v] TRUE, pokud je vybráno tlačítko pole se seznamem; jinak NEPRAVDA.

### <a name="return-value"></a>Návratová hodnota

Šířka tlačítka pole se seznamem v pixelech.

## <a name="cmfctoolbarcomboboxbuttononglobalfontschanged"></a><a name="onglobalfontschanged"></a>CMFCToolBarComboBoxButton::OnGlobalFontsChanged

Volat rámci nastavit písmo tlačítka pole se seznamem při změně písma aplikace.

```
virtual void OnGlobalFontsChanged();
```

## <a name="cmfctoolbarcomboboxbuttononmove"></a><a name="onmove"></a>CMFCToolBarComboBoxButton::OnMove

Volat rámci změnit umístění tlačítka pole se seznamem při přesune nadřazený panel nástrojů.

```
virtual void OnMove();
```

## <a name="cmfctoolbarcomboboxbuttononshow"></a><a name="onshow"></a>CMFCToolBarComboBoxButton::OnShow

Volat rámci při pole se seznamem tlačítko je skrytý nebo zobrazen.

```
virtual void OnShow(BOOL bShow);
```

### <a name="parameters"></a>Parametry

*bZobrazit*<br/>
[v] Určuje, zda chcete skrýt nebo zobrazit tlačítko pole se seznamem.

## <a name="cmfctoolbarcomboboxbuttononsize"></a><a name="onsize"></a>CMFCToolBarComboBoxButton::OnSize

Volat rámci změnit velikost tlačítka pole se seznamem při změně nadřazeného panelu nástrojů změní velikost.

```
virtual void OnSize(int iSize);
```

### <a name="parameters"></a>Parametry

*iVelikost*<br/>
[v] Nová šířka tlačítka pole se seznamem.

## <a name="cmfctoolbarcomboboxbuttononupdatetooltip"></a><a name="onupdatetooltip"></a>CMFCToolBarComboBoxButton::OnUpdateToolTip

Volat rámci při uživatel změní tip nástroje pro tlačítko pole se seznamem.

```
virtual BOOL OnUpdateToolTip(
    CWnd* pWndParent,
    int iButtonIndex,
    CToolTipCtrl& wndToolTip,
    CString& str);
```

### <a name="parameters"></a>Parametry

*pWndParent*<br/>
[v] Ukazatel na nadřazené okno pro tlačítko pole se seznamem.

*iButtonIndex*<br/>
[v] ID tlačítka pole se seznamem.

*soubor nástrojů wnd*<br/>
[v] Tip nástroje pro přidružení k tlačítku pole se seznamem.

*Str*<br/>
[v] Text tipu nástroje.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud metoda zpracovává událost; jinak NEPRAVDA.

## <a name="cmfctoolbarcomboboxbuttonremoveallitems"></a><a name="removeallitems"></a>CMFCToolBarComboBoxButton::RemoveAllItems

Odstraní všechny položky ze seznamu a upravit pole.

```
void RemoveAllItems();
```

### <a name="remarks"></a>Poznámky

Odebere všechny položky ze seznamu a upravit ovládací prvek pole se seznamem.

## <a name="cmfctoolbarcomboboxbuttonselectitem"></a><a name="selectitem"></a>CMFCToolBarComboBoxButton::SelectItem

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
[v] Nulový index položky v seznamu.

*bUpozornit*<br/>
[v] TRUE upozornit na tlačítko pole se seznamem výběru; jinak FALSE.

*dwData*<br/>
[v] Data přidružená k položce v seznamu.

*lpszText*<br/>
[v] Text položky v seznamu.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud byla metoda úspěšná; jinak FALSE.

### <a name="remarks"></a>Poznámky

## <a name="cmfctoolbarcomboboxbuttonselectitemall"></a><a name="selectitemall"></a>CMFCToolBarComboBoxButton::SelectItemAll

Vybere položku v seznamu tlačítka pole se seznamem, která má zadané ID příkazu.

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
[v] ID příkazu tlačítka pole se seznamem, které obsahuje seznam.

*iIndex*<br/>
[v] Nulový index položky v seznamu. Hodnota -1 odebere libovolný aktuální výběr v seznamu a vymaže editační pole.

*dwData*<br/>
[v] Data položky v seznamu.

*lpszText*<br/>
[v] Text položky v seznamu.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud byla metoda úspěšná; jinak FALSE.

### <a name="remarks"></a>Poznámky

## <a name="cmfctoolbarcomboboxbuttonserialize"></a><a name="serialize"></a>CMFCToolBarComboBoxButton::Serializovat

Přečte tento objekt z archivu nebo jej zapíše do archivu.

```
virtual void Serialize(CArchive& ar);
```

### <a name="parameters"></a>Parametry

*ar*<br/>
[dovnitř, ven] Objekt `CArchive` serializovat.

### <a name="remarks"></a>Poznámky

Nastavení v `CArchive` objektu určují, zda tato metoda čte nebo zapisuje do archivu.

## <a name="cmfctoolbarcomboboxbuttonsetaccdata"></a><a name="setaccdata"></a>CMFCToolBarComboBoxButton::SetACCData

Naplní zadaný `CAccessibilityData` objekt pomocí dat usnadnění přístupu z tlačítka pole se seznamem.

```
virtual BOOL SetACCData(
    CWnd* pParent,
    CAccessibilityData& data);
```

### <a name="parameters"></a>Parametry

*pParent*<br/>
[v] Nadřazené okno tlačítka pole se seznamem.

*Dat*<br/>
[out] Objekt, `CAccessibilityData` který přijímá data usnadnění přístupu z pole se seznamem.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud byla metoda úspěšná; jinak FALSE.

## <a name="cmfctoolbarcomboboxbuttonsetcentervert"></a><a name="setcentervert"></a>CMFCToolBarComboBoxButton::SetCenterVert

Nastaví svislou polohu tlačítek pole se seznamem v aplikaci.

```
static void SetCenterVert(BOOL bCenterVert=TRUE);
```

### <a name="parameters"></a>Parametry

*bCenterVert*<br/>
[v] TRUE pro vystředění tlačítka pole se seznamem na panelu nástrojů; FALSE zarovnat tlačítko pole se seznamem do horní části panelu nástrojů.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení jsou tlačítka pole se seznamem zarovnána nahoru.

## <a name="cmfctoolbarcomboboxbuttonsetcontextmenuid"></a><a name="setcontextmenuid"></a>CMFCToolBarComboBoxButton::ID setcontextmenu

Nastaví ID prostředku místní nabídky pro tlačítko pole se seznamem.

```
void SetContextMenuID(UINT uiResID);
```

### <a name="parameters"></a>Parametry

*uiResID*<br/>
[v] ID prostředku místní nabídky.

## <a name="cmfctoolbarcomboboxbuttonsetdropdownheight"></a><a name="setdropdownheight"></a>CMFCToolBarComboBoxButton::SetDropDownHeight

Nastaví výšku seznamu, když je spadl dolů.

```
void SetDropDownHeight(int nHeight);
```

### <a name="parameters"></a>Parametry

*nVýška*<br/>
[v] Výška v pixelech seznamu.

### <a name="remarks"></a>Poznámky

Výchozí výška je 150 pixelů.

## <a name="cmfctoolbarcomboboxbuttonsetflatmode"></a><a name="setflatmode"></a>CMFCToolBarComboBoxButton::SetFlatMode

Nastaví plochý vzhled tlačítek pole se seznamem v aplikaci.

```
static void SetFlatMode(BOOL bFlat=TRUE);
```

### <a name="parameters"></a>Parametry

*bPlochý*<br/>
[v] TRUE pro plochý vzhled stylu; jinak FALSE.

### <a name="remarks"></a>Poznámky

Výchozí plochý styl pro tlačítka pole se seznamem je FALSE.

## <a name="cmfctoolbarcomboboxbuttonsetstyle"></a><a name="setstyle"></a>CMFCToolBarComboBoxButton::SetStyle

Nastaví zadaný styl tlačítka pole se seznamem a překreslí ovládací prvek, pokud není zakázán.

```
virtual void SetStyle(UINT nStyle);
```

### <a name="parameters"></a>Parametry

*nStyl*<br/>
[v] Bitová kombinace (OR) stylů panelů nástrojů.

### <a name="remarks"></a>Poznámky

Seznam stylů tlačítek panelu nástrojů naleznete v tématu [Styly ovládacích prvků nástrojů](../../mfc/reference/toolbar-control-styles.md)

## <a name="cmfctoolbarcomboboxbuttonsettext"></a><a name="settext"></a>CMFCToolBarComboBoxButton::SetText

Nastaví text v textovém poli tlačítka pole se seznamem.

```
void SetText(LPCTSTR lpszText);
```

### <a name="parameters"></a>Parametry

*lpszText*<br/>
[v] Ukazatel na řetězec, který obsahuje text pro textové pole.

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[Třída CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[Třída CComboBox](../../mfc/reference/ccombobox-class.md)<br/>
[CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)<br/>
[Návod: Umístění ovládacích prvků na panely nástrojů](../../mfc/walkthrough-putting-controls-on-toolbars.md)
