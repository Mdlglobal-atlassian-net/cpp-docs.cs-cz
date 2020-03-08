---
title: Atributu CComboBoxEx – třída
ms.date: 11/04/2016
f1_keywords:
- CComboBoxEx
- AFXCMN/CComboBoxEx
- AFXCMN/CComboBoxEx::CComboBoxEx
- AFXCMN/CComboBoxEx::Create
- AFXCMN/CComboBoxEx::CreateEx
- AFXCMN/CComboBoxEx::DeleteItem
- AFXCMN/CComboBoxEx::GetComboBoxCtrl
- AFXCMN/CComboBoxEx::GetEditCtrl
- AFXCMN/CComboBoxEx::GetExtendedStyle
- AFXCMN/CComboBoxEx::GetImageList
- AFXCMN/CComboBoxEx::GetItem
- AFXCMN/CComboBoxEx::HasEditChanged
- AFXCMN/CComboBoxEx::InsertItem
- AFXCMN/CComboBoxEx::SetExtendedStyle
- AFXCMN/CComboBoxEx::SetImageList
- AFXCMN/CComboBoxEx::SetItem
- AFXCMN/CComboBoxEx::SetWindowTheme
helpviewer_keywords:
- CComboBoxEx [MFC], CComboBoxEx
- CComboBoxEx [MFC], Create
- CComboBoxEx [MFC], CreateEx
- CComboBoxEx [MFC], DeleteItem
- CComboBoxEx [MFC], GetComboBoxCtrl
- CComboBoxEx [MFC], GetEditCtrl
- CComboBoxEx [MFC], GetExtendedStyle
- CComboBoxEx [MFC], GetImageList
- CComboBoxEx [MFC], GetItem
- CComboBoxEx [MFC], HasEditChanged
- CComboBoxEx [MFC], InsertItem
- CComboBoxEx [MFC], SetExtendedStyle
- CComboBoxEx [MFC], SetImageList
- CComboBoxEx [MFC], SetItem
- CComboBoxEx [MFC], SetWindowTheme
ms.assetid: 33ca960a-2409-478c-84a4-a2ee8ecfe8f7
ms.openlocfilehash: 7d46f175a62cda7f1ff08327830f1dffe2967727
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78865545"
---
# <a name="ccomboboxex-class"></a>Atributu CComboBoxEx – třída

Rozšiřuje ovládací prvek pole se seznamem tím, že poskytuje podporu pro seznamy obrázků.

## <a name="syntax"></a>Syntaxe

```
class CComboBoxEx : public CComboBox
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[Atributu CComboBoxEx:: atributu CComboBoxEx](#ccomboboxex)|Vytvoří objekt `CComboBoxEx`.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[Atributu CComboBoxEx:: Create](#create)|Vytvoří pole se seznamem a připojí ho k objektu `CComboBoxEx`.|
|[Atributu CComboBoxEx:: CreateEx](#createex)|Vytvoří pole se seznamem se zadanými rozšířenými styly Windows a připojí ho k objektu `ComboBoxEx`.|
|[Atributu CComboBoxEx::D eleteItem](#deleteitem)|Odebere položku z ovládacího prvku `ComboBoxEx`.|
|[Atributu CComboBoxEx:: GetComboBoxCtrl](#getcomboboxctrl)|Načte ukazatel na podřízený ovládací prvek pole se seznamem.|
|[Atributu CComboBoxEx:: GetEditCtrl](#geteditctrl)|Načte popisovač k části pro úpravu ovládacího prvku `ComboBoxEx`.|
|[Atributu CComboBoxEx:: GetExtendedStyle](#getextendedstyle)|Načte rozšířené styly, které jsou používány pro ovládací prvek `ComboBoxEx`.|
|[Atributu CComboBoxEx:: GetImageList](#getimagelist)|Načte ukazatel na seznam obrázků přiřazený ovládacímu prvku `ComboBoxEx`.|
|[Atributu CComboBoxEx:: GetItem](#getitem)|Načte informace o položce pro danou `ComboBoxEx` položku.|
|[Atributu CComboBoxEx:: HasEditChanged](#haseditchanged)|Určuje, zda uživatel změnil obsah ovládacího prvku `ComboBoxEx` pro úpravy zadáním.|
|[Atributu CComboBoxEx:: InsertItem](#insertitem)|Vloží novou položku do ovládacího prvku `ComboBoxEx`.|
|[Atributu CComboBoxEx:: SetExtendedStyle](#setextendedstyle)|Nastaví rozšířené styly v rámci ovládacího prvku `ComboBoxEx`.|
|[Atributu CComboBoxEx:: SetImageList](#setimagelist)|Nastaví seznam obrázků pro ovládací prvek `ComboBoxEx`.|
|[Atributu CComboBoxEx:: SetItem](#setitem)|Nastaví atributy pro položku v ovládacím prvku `ComboBoxEx`.|
|[Atributu CComboBoxEx:: SetWindowTheme](#setwindowtheme)|Nastaví styl vizuálu ovládacího prvku rozšířené pole se seznamem.|

## <a name="remarks"></a>Poznámky

Pomocí `CComboBoxEx` k vytváření ovládacích prvků pole se seznamem již není nutné implementovat vlastní kód pro vykreslování obrázků. Místo toho použijte `CComboBoxEx` k přístupu k obrázkům ze seznamu obrázků.

## <a name="image-list-support"></a>Podpora seznamu obrázků

Ve standardním poli se seznamem je vlastník pole se seznamem zodpovědný za vykreslení obrázku vytvořením pole se seznamem jako ovládacího prvku pro vykreslení vlastníka. Při použití `CComboBoxEx`není nutné nastavovat styly kreslení CBS_OWNERDRAWFIXED a CBS_HASSTRINGS, protože jsou implicitně odvozeny. V opačném případě musíte napsat kód, který provede operace vykreslování. Ovládací prvek `CComboBoxEx` podporuje až tři obrázky na jednu položku: jeden pro vybraný stav, jeden pro nevybraný stav a jeden pro překrývající se obrázek.

## <a name="styles"></a>Styly

`CComboBoxEx` podporuje styly CBS_SIMPLE, CBS_DROPDOWN, CBS_DROPDOWNLIST a WS_CHILD. Všechny ostatní styly předané při vytváření okna jsou ignorovány ovládacím prvkem. Po vytvoření okna můžete zadat další styly pole se seznamem voláním členské funkce `CComboBoxEx` [SetExtendedStyle](#setextendedstyle). S těmito styly můžete:

- V seznamu nastavte hledání řetězců, které rozlišuje velká a malá písmena.

- Vytvoří ovládací prvek pole se seznamem, který používá lomítko ('/'), zpětného lomítka ('\\') a tečky ('. ') jako oddělovače slov. To umožní uživatelům přejít z Wordu do Wordu pomocí klávesové zkratky CTRL + šipka.

- Nastavte ovládací prvek pole se seznamem na hodnotu zobrazit nebo nezobrazit obrázek. Pokud se nezobrazí žádný obrázek, pole se seznamem může odebrat odsazení textu, které se vejde na obrázek.

- Vytvořte úzký ovládací prvek pole se seznamem, včetně jeho velikosti tak, aby obsahoval širší pole se seznamem, které obsahuje.

Tyto příznaky stylu jsou podrobněji popsány v tématu [using atributu CComboBoxEx](../../mfc/using-ccomboboxex.md).

## <a name="item-retention-and-callback-item-attributes"></a>Uchování položek a atributy položky zpětného volání

Informace o položkách, jako jsou indexy pro položky a obrázky, hodnoty odsazení a textové řetězce, jsou uloženy ve struktuře Win32 [COMBOBOXEXITEM](/windows/win32/api/commctrl/ns-commctrl-comboboxexitemw), jak je popsáno v Windows SDK. Struktura také obsahuje členy, které odpovídají příznak zpětného volání.

Podrobné koncepční diskuzi najdete v tématu [použití atributu CComboBoxEx](../../mfc/using-ccomboboxex.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CComboBox –](../../mfc/reference/ccombobox-class.md)

`CComboBoxEx`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxcmn. h

##  <a name="ccomboboxex"></a>Atributu CComboBoxEx:: atributu CComboBoxEx

Chcete-li vytvořit objekt `CComboBoxEx`, zavolejte tuto členskou funkci.

```
CComboBoxEx();
```

##  <a name="create"></a>Atributu CComboBoxEx:: Create

Vytvoří pole se seznamem a připojí ho k objektu `CComboBoxEx`.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*dwStyle*<br/>
Určuje kombinaci stylů pole se seznamem použitou pro pole se seznamem. Další informace o stylech naleznete níže v části **poznámky** .

*OBD*<br/>
Odkaz na objekt [CRect](../../atl-mfc-shared/reference/crect-class.md) nebo strukturu [Rect](/previous-versions/dd162897\(v=vs.85\)) , což je pozice a velikost pole se seznamem.

*pParentWnd*<br/>
Ukazatel na objekt [CWnd](../../mfc/reference/cwnd-class.md) , který je nadřazené okno pole se seznamem (obvykle `CDialog`). Nesmí mít hodnotu NULL.

*nID*<br/>
Určuje ID ovládacího prvku pole se seznamem.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud byl objekt úspěšně vytvořen; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Vytvořte objekt `CComboBoxEx` ve dvou krocích:

1. Voláním [atributu CComboBoxEx](#ccomboboxex) vytvořte objekt `CComboBoxEx`.

1. Zavolejte tuto členskou funkci, která vytvoří rozšířené pole se seznamem Windows a připojí ho k objektu `CComboBoxEx`.

Při volání `Create`inicializuje knihovna MFC běžné ovládací prvky.

Při vytváření pole se seznamem můžete zadat libovolné nebo všechny následující styly pole se seznamem:

- CBS_SIMPLE

- CBS_DROPDOWN

- CBS_DROPDOWNLIST

- CBS_AUTOHSCROLL

- WS_CHILD

Všechny ostatní styly předané při vytváření okna jsou ignorovány. Ovládací prvek `ComboBoxEx` také podporuje rozšířené styly, které poskytují další funkce. Tyto styly jsou popsány v části [Rozšířené styly ovládacího prvku ComboBoxEx](/windows/win32/Controls/comboboxex-control-extended-styles)v Windows SDK. Nastavte tyto styly voláním [SetExtendedStyle](#setextendedstyle).

Chcete-li použít rozšířené styly systému Windows s ovládacím prvkem, zavolejte [CreateEx](#createex) místo `Create`.

##  <a name="createex"></a>Atributu CComboBoxEx:: CreateEx

Voláním této funkce vytvoříte rozšířený ovládací prvek pole se seznamem (podřízené okno) a přidružíte ho k objektu `CComboBoxEx`.

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*dwExStyle*<br/>
Určuje rozšířený styl ovládacího prvku, který se vytváří. Seznam rozšířených stylů Windows naleznete v parametru *dwExStyle* pro [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) v Windows SDK.

*dwStyle*<br/>
Styl ovládacího prvku pole se seznamem Seznam stylů najdete v tématu [Vytvoření](#create) .

*OBD*<br/>
Odkaz na strukturu [Rect](/previous-versions/dd162897\(v=vs.85\)) popisující velikost a umístění okna, které má být vytvořeno, v souřadnicích klienta *pParentWnd*.

*pParentWnd*<br/>
Ukazatel na okno, které je nadřazený ovládacímu prvku.

*nID*<br/>
ID podřízeného okna ovládacího prvku

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Použijte `CreateEx` místo `Create` pro použití rozšířených stylů Windows, které jsou určené **WS_EX_m**rozšířeným stylem pro Windows.

`CreateEx` vytvoří ovládací prvek s rozšířenými styly Windows specifikovanými pomocí *dwExStyle*. Je nutné nastavit rozšířené styly specifické pro rozšířený ovládací prvek pole se seznamem pomocí [SetExtendedStyle](#setextendedstyle). Například použijte `CreateEx` k nastavení stylů jako WS_EX_CONTEXTHELP, ale použijte `SetExtendedStyle` k nastavení stylů jako CBES_EX_CASESENSITIVE. Další informace naleznete v tématu styly popsané v tématu [ComboBoxEx rozšířené styly ovládacího prvku](/windows/win32/Controls/comboboxex-control-extended-styles) v Windows SDK.

##  <a name="deleteitem"></a>Atributu CComboBoxEx::D eleteItem

Odebere položku z ovládacího prvku `ComboBoxEx`.

```
int DeleteItem(int iIndex);
```

### <a name="parameters"></a>Parametry

*iIndex*<br/>
Index vycházející z položky, která má být odebrána.

### <a name="return-value"></a>Návratová hodnota

Počet položek zbývajících v ovládacím prvku Pokud je *iIndex* neplatný, funkce vrátí CB_ERR.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje funkce [CBEM_DELETEITEM](/windows/win32/Controls/cbem-deleteitem)zprávy, jak je popsáno v Windows SDK. Při volání DeleteItem se do nadřazeného okna pošle zpráva [WM_NOTIFY](/windows/win32/controls/wm-notify) s CBEN_DELETEITEM oznámení.

##  <a name="getcomboboxctrl"></a>Atributu CComboBoxEx:: GetComboBoxCtrl

Chcete-li získat ukazatel na ovládací prvek pole se seznamem v objektu `CComboBoxEx`, zavolejte tuto členskou funkci.

```
CComboBox* GetComboBoxCtrl();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na objekt `CComboBox`.

### <a name="remarks"></a>Poznámky

Ovládací prvek `CComboBoxEx` se skládá z nadřazeného okna, které zapouzdřuje `CComboBox`.

Objekt `CComboBox` odkazoval návratovou hodnotou je dočasný objekt a je zničen během příštího nečinného času zpracování.

##  <a name="geteditctrl"></a>Atributu CComboBoxEx:: GetEditCtrl

Chcete-li získat ukazatel na ovládací prvek pro úpravy pole se seznamem, zavolejte tuto členskou funkci.

```
CEdit* GetEditCtrl();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na objekt [CEdit](../../mfc/reference/cedit-class.md) .

### <a name="remarks"></a>Poznámky

`CComboBoxEx` ovládací prvek používá textové pole, když je vytvořen pomocí stylu CBS_DROPDOWN.

Objekt `CEdit` odkazoval návratovou hodnotou je dočasný objekt a je zničen během příštího nečinného času zpracování.

##  <a name="getextendedstyle"></a>Atributu CComboBoxEx:: GetExtendedStyle

Volejte tuto členskou funkci pro získání rozšířených stylů používaných pro ovládací prvek `CComboBoxEx`.

```
DWORD GetExtendedStyle() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota DWORD obsahující rozšířené styly, které jsou použity pro ovládací prvek pole se seznamem.

### <a name="remarks"></a>Poznámky

Další informace o těchto stylech naleznete v tématu [Rozšířené styly ovládacího prvku ComboBoxEx](/windows/win32/Controls/comboboxex-control-extended-styles) v Windows SDK.

##  <a name="getimagelist"></a>Atributu CComboBoxEx:: GetImageList

Voláním této členské funkce získáte ukazatel na seznam obrázků používaný ovládacím prvkem `CComboBoxEx`.

```
CImageList* GetImageList() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na objekt [atributu CImageList](../../mfc/reference/cimagelist-class.md) . Pokud dojde k chybě, tato členská funkce vrátí hodnotu NULL.

### <a name="remarks"></a>Poznámky

Objekt `CImageList` odkazoval návratovou hodnotou je dočasný objekt a je zničen během příštího nečinného času zpracování.

##  <a name="getitem"></a>Atributu CComboBoxEx:: GetItem

Načte informace o položce pro danou `ComboBoxEx` položku.

```
BOOL GetItem(COMBOBOXEXITEM* pCBItem);
```

### <a name="parameters"></a>Parametry

*pCBItem*<br/>
Ukazatel na strukturu [COMBOBOXEXITEM](/windows/win32/api/commctrl/ns-commctrl-comboboxexitemw) , která bude přijímat informace o položce.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud operace byla úspěšná; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje funkce [CBEM_GETITEM](/windows/win32/Controls/cbem-getitem)zprávy, jak je popsáno v Windows SDK.

##  <a name="haseditchanged"></a>Atributu CComboBoxEx:: HasEditChanged

Určuje, zda uživatel změnil obsah ovládacího prvku `ComboBoxEx` pro úpravy zadáním.

```
BOOL HasEditChanged();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud uživatel zadal v textovém poli ovládacího prvku; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje funkce [CBEM_HASEDITCHANGED](/windows/win32/Controls/cbem-haseditchanged)zprávy, jak je popsáno v Windows SDK.

##  <a name="insertitem"></a>Atributu CComboBoxEx:: InsertItem

Vloží novou položku do ovládacího prvku `ComboBoxEx`.

```
int InsertItem(const COMBOBOXEXITEM* pCBItem);
```

### <a name="parameters"></a>Parametry

*pCBItem*<br/>
Ukazatel na strukturu [COMBOBOXEXITEM](/windows/win32/api/commctrl/ns-commctrl-comboboxexitemw) , která bude přijímat informace o položce. Tato struktura obsahuje hodnoty příznaků zpětného volání pro položku.

### <a name="return-value"></a>Návratová hodnota

Index, na kterém byla nová položka vložena, pokud byla úspěšná; v opačném případě-1.

### <a name="remarks"></a>Poznámky

Při volání `InsertItem`se do nadřazeného okna pošle zpráva [WM_NOTIFY](/windows/win32/controls/wm-notify) s [CBEN_INSERTITEMm](/windows/win32/Controls/cben-insertitem) oznámením.

##  <a name="setextendedstyle"></a>Atributu CComboBoxEx:: SetExtendedStyle

Zavolejte tuto členskou funkci pro nastavení rozšířených stylů použitých pro rozšířený ovládací prvek pole se seznamem.

```
DWORD SetExtendedStyle(
    DWORD dwExMask,
    DWORD dwExStyles);
```

### <a name="parameters"></a>Parametry

*dwExMask*<br/>
Hodnota DWORD, která určuje, které styly v *dwExStyles* mají být ovlivněny. Budou změněny pouze rozšířené styly v *dwExMask* . Všechny ostatní styly budou udržovány tak, jak jsou. Pokud má tento parametr hodnotu nula, bude to mít vliv na všechny styly v *dwExStyles* .

*dwExStyles*<br/>
Hodnota DWORD obsahující rozšířené styly ovládacího prvku pole se seznamem, které mají být nastaveny pro ovládací prvek.

### <a name="return-value"></a>Návratová hodnota

Hodnota DWORD obsahující rozšířené styly, které byly dříve použity pro ovládací prvek.

### <a name="remarks"></a>Poznámky

Další informace o těchto stylech naleznete v tématu [Rozšířené styly ovládacího prvku ComboBoxEx](/windows/win32/Controls/comboboxex-control-extended-styles) v Windows SDK.

Chcete-li vytvořit rozšířený ovládací prvek pole se seznamem pomocí rozšířených stylů Windows, použijte [CreateEx](#createex).

##  <a name="setimagelist"></a>Atributu CComboBoxEx:: SetImageList

Nastaví seznam obrázků pro ovládací prvek `ComboBoxEx`.

```
CImageList* SetImageList(CImageList* pImageList);
```

### <a name="parameters"></a>Parametry

*pImageList*<br/>
Ukazatel na objekt `CImageList` obsahující obrázky, které mají být použity s ovládacím prvkem `CComboBoxEx`.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na objekt [atributu CImageList](../../mfc/reference/cimagelist-class.md) obsahující obrázky dříve používané ovládacím prvkem `CComboBoxEx`. Hodnota NULL, pokud nebyl dříve nastaven seznam obrázků.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje funkce [CBEM_SETIMAGELIST](/windows/win32/Controls/cbem-setimagelist)zprávy, jak je popsáno v Windows SDK. Změníte-li výšku výchozího ovládacího prvku pro úpravy, zavolejte funkci Win32 [SetWindowPos](/windows/win32/api/winuser/nf-winuser-setwindowpos) , aby po volání `SetImageList`změnila velikost ovládacího prvku, nebo se nebude zobrazovat správně.

Objekt `CImageList` odkazoval návratovou hodnotou je dočasný objekt a je zničen během příštího nečinného času zpracování.

##  <a name="setitem"></a>Atributu CComboBoxEx:: SetItem

Nastaví atributy pro položku v ovládacím prvku `ComboBoxEx`.

```
BOOL SetItem(const COMBOBOXEXITEM* pCBItem);
```

### <a name="parameters"></a>Parametry

*pCBItem*<br/>
Ukazatel na strukturu [COMBOBOXEXITEM](/windows/win32/api/commctrl/ns-commctrl-comboboxexitemw) , která bude přijímat informace o položce.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud operace byla úspěšná; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje funkce [CBEM_SETITEM](/windows/win32/Controls/cbem-setitem)zprávy, jak je popsáno v Windows SDK.

##  <a name="setwindowtheme"></a>Atributu CComboBoxEx:: SetWindowTheme

Nastaví styl vizuálu ovládacího prvku rozšířené pole se seznamem.

```
HRESULT SetWindowTheme(LPCWSTR pszSubAppName);
```

### <a name="parameters"></a>Parametry

*pszSubAppName*<br/>
Ukazatel na řetězec v kódování Unicode, který obsahuje rozšířený vizuální styl pole se seznamem, který se má nastavit.

### <a name="return-value"></a>Návratová hodnota

Návratová hodnota se nepoužívá.

### <a name="remarks"></a>Poznámky

Tato členská funkce emuluje funkce [CBEM_SETWINDOWTHEME](/windows/win32/Controls/cbem-setwindowtheme) zprávy, jak je popsáno v Windows SDK.

## <a name="see-also"></a>Viz také

[MFCIE Sample MFC](../../overview/visual-cpp-samples.md)<br/>
[CComboBox – třída](../../mfc/reference/ccombobox-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CComboBox – třída](../../mfc/reference/ccombobox-class.md)
