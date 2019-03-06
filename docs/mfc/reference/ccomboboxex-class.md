---
title: Ccomboboxex – třída
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
ms.openlocfilehash: 44943803fdb422ccbf77302e7c81f23c34cc7433
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57420755"
---
# <a name="ccomboboxex-class"></a>Ccomboboxex – třída

Poskytnutím podpory pro seznamy obrázků rozšiřuje ovládací prvek pole se seznamem.

## <a name="syntax"></a>Syntaxe

```
class CComboBoxEx : public CComboBox
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CComboBoxEx::CComboBoxEx](#ccomboboxex)|Vytvoří `CComboBoxEx` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CComboBoxEx::Create](#create)|Vytvoří pole se seznamem a připojí ho k `CComboBoxEx` objektu.|
|[CComboBoxEx::CreateEx](#createex)|Vytvoří pole se seznamem se zadaným rozšířené styly Windows a připojí ho k `ComboBoxEx` objektu.|
|[CComboBoxEx::DeleteItem](#deleteitem)|Odebere položku z `ComboBoxEx` ovládacího prvku.|
|[CComboBoxEx::GetComboBoxCtrl](#getcomboboxctrl)|Načte ukazatel na podřízený ovládací prvek pole se seznamem.|
|[CComboBoxEx::GetEditCtrl](#geteditctrl)|Načte popisovač pro část ovládacího prvku úprav `ComboBoxEx` ovládacího prvku.|
|[CComboBoxEx::GetExtendedStyle](#getextendedstyle)|Rozšířené styly, které se používají pro načte `ComboBoxEx` ovládacího prvku.|
|[CComboBoxEx::GetImageList](#getimagelist)|Načte ukazatel na seznam obrázků přiřazeno `ComboBoxEx` ovládacího prvku.|
|[CComboBoxEx::GetItem](#getitem)|Načte položku informace pro danou `ComboBoxEx` položky.|
|[CComboBoxEx::HasEditChanged](#haseditchanged)|Určuje, jestli se uživatel změnil obsah `ComboBoxEx` ovládací prvek textové pole tak, že zadáte.|
|[CComboBoxEx::InsertItem](#insertitem)|Vloží novou položku `ComboBoxEx` ovládacího prvku.|
|[CComboBoxEx::SetExtendedStyle](#setextendedstyle)|Rozšířené styly v rámci nastaví `ComboBoxEx` ovládacího prvku.|
|[CComboBoxEx::SetImageList](#setimagelist)|Nastaví pro seznam obrázků `ComboBoxEx` ovládacího prvku.|
|[CComboBoxEx::SetItem](#setitem)|Nastaví atributy pro položku `ComboBoxEx` ovládacího prvku.|
|[CComboBoxEx::SetWindowTheme](#setwindowtheme)|Nastaví vizuální styl rozšířené pole se seznamem ovládací prvek pole.|

## <a name="remarks"></a>Poznámky

S použitím `CComboBoxEx` vytvořit ovládací prvky pole se seznamem, už potřebujete implementovat vlastní image kreslení kódu. Místo toho použijte `CComboBoxEx` k imagím přístup ze seznamu obrázků.

## <a name="image-list-support"></a>Podpora seznamu obrázků

Ve standardní se seznamem zodpovídá za kreslení obrázku tak, že vytvoříte pole se seznamem jako ovládací prvek vykreslené vlastníkem. vlastníkem pole se seznamem. Při použití `CComboBoxEx`, není nutné nastavovat vykreslování stylů CBS_OWNERDRAWFIXED a CBS_HASSTRINGS, protože jsou implicitní. V opačném případě musíte napsat kód k provedení operace kreslení. A `CComboBoxEx` ovládací prvek podporuje až tři Image jednu položku: jeden pro vybraný stav, jeden pro nevybraném stavu a jednu pro obrázek překrytí.

## <a name="styles"></a>Styly

`CComboBoxEx` podporuje styly CBS_SIMPLE, CBS_DROPDOWN, CBS_DROPDOWNLIST a WS_CHILD. Všechny styly, která se předá, když vytvoříte v okně se ignorují v ovládacím prvku. Po vytvoření v okně můžete zadat jiné pole se seznamem styly voláním `CComboBoxEx` členskou funkci [SetExtendedStyle](#setextendedstyle). Tyto styly vám umožní:

- Nastavení hledání v seznamu, aby se malá a velká písmena.

- Vytvoření pole se seznamem pole ovládacího prvku, který používá lomítko ("/"), zpětného lomítka ("\\") a období (".") znaků jako oddělovače aplikace word. Díky tomu uživatelé přejít z aplikace word pro word, pomocí klávesové zkratky CTRL + ŠIPKA.

- Nastavte pole se seznamem ovládací prvek pole pro zobrazení nebo obrázek se nezobrazí. Pokud žádný obrázek se zobrazí, můžete odebrat pole se seznamem odsazení textu, který přizpůsobuje bitovou kopii.

- Vytvoření ovládacího prvku pole se seznamem úzký pole, včetně změny velikosti, takže klipy širší pole se seznamem, které obsahuje.

Tyto příznaky styl jsou popsány dále v [používání atributu CComboBoxEx](../../mfc/using-ccomboboxex.md).

## <a name="item-retention-and-callback-item-attributes"></a>Uchování položky a atributy položky zpětného volání

Informace o položkách, jako jsou indexy pro položky a obrázky, hodnoty odsazení a textové řetězce, je uložen ve struktuře Win32 [COMBOBOXEXITEM](/windows/desktop/api/commctrl/ns-commctrl-tagcomboboxexitema), jak je popsáno v sadě Windows SDK. Struktura také obsahuje členy, které odpovídají příznaky zpětného volání.

Podrobné, koncepční informace, najdete v článku [používání atributu CComboBoxEx](../../mfc/using-ccomboboxex.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CComboBox](../../mfc/reference/ccombobox-class.md)

`CComboBoxEx`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxcmn.h

##  <a name="ccomboboxex"></a>  CComboBoxEx::CComboBoxEx

Voláním této členské funkce k vytvoření `CComboBoxEx` objektu.

```
CComboBoxEx();
```

##  <a name="create"></a>  CComboBoxEx::Create

Vytvoří pole se seznamem a připojí ho k `CComboBoxEx` objektu.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*dwStyle*<br/>
Určuje kombinaci styly pole se seznamem použít pro pole se seznamem. Zobrazit **poznámky** níže pro další informace o stylech.

*Rect*<br/>
Odkaz na [crect –](../../atl-mfc-shared/reference/crect-class.md) objektu nebo [RECT](/previous-versions/dd162897\(v=vs.85\)) struktury, což je umístění a velikost pole se seznamem.

*pParentWnd*<br/>
Ukazatel [CWnd](../../mfc/reference/cwnd-class.md) objekt, který je nadřazené okno pole se seznamem (obvykle `CDialog`). Nesmí být NULL.

*nID*<br/>
Určuje ID ovládacího prvku pole se seznamem

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud byl objekt vytvořen úspěšně; jinak 0.

### <a name="remarks"></a>Poznámky

Vytvoření `CComboBoxEx` objektu ve dvou krocích:

1. Volání [atributu CComboBoxEx](#ccomboboxex) k vytvoření `CComboBoxEx` objektu.

1. Voláním této členské funkce, která vytvoří rozšířené pole se seznamem Windows a připojí ho k `CComboBoxEx` objektu.

Při volání `Create`, inicializuje běžných ovládacích prvků MFC.

Při vytváření pole se seznamem, můžete zadat některé nebo všechny následující pole se seznamem stylů:

- CBS_SIMPLE

- CBS_DROPDOWN

- CBS_DROPDOWNLIST

- CBS_AUTOHSCROLL

- WS_CHILD

Všechny styly, která se předá, když vytvoříte v okně se ignorují. `ComboBoxEx` Ovládací prvek podporuje také rozšířené styly, které poskytují další funkce. Tyto styly jsou popsány v [ComboBoxEx řídit rozšířené styly](/windows/desktop/Controls/comboboxex-control-extended-styles), v sadě Windows SDK. Nastavte tyto styly voláním [SetExtendedStyle](#setextendedstyle).

Pokud chcete použít rozšířené windows styly ovládacího prvku, zavolejte [CreateEx](#createex) místo `Create`.

##  <a name="createex"></a>  CComboBoxEx::CreateEx

Voláním této funkce vytvoření ovládacího prvku rozšířené pole se seznamem (podřízené okno) a přidružte jej k `CComboBoxEx` objektu.

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
Určuje rozšířený styl ovládacího prvku vytváří. Seznam rozšířené styly Windows najdete v tématu *dwExStyle* parametr pro [CreateWindowEx](/windows/desktop/api/winuser/nf-winuser-createwindowexa) v sadě Windows SDK.

*dwStyle*<br/>
Styl ovládacího prvku pole se seznamem. Zobrazit [vytvořit](#create) seznam styly.

*Rect*<br/>
Odkaz na [RECT](/previous-versions/dd162897\(v=vs.85\)) struktura popisující, velikost a umístění okna, které nelze v souřadnice klienta *pParentWnd*.

*pParentWnd*<br/>
Ukazatel na okno, který je nadřazeného ovládacího prvku.

*nID*<br/>
ID ovládacího prvku podřízené okno.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Použití `CreateEx` místo `Create` použít rozšířené styly Windows určené předponu rozšířeného stylu Windows **WS_EX_**.

`CreateEx` Vytvoří ovládací prvek s rozšířené styly Windows určené *dwExStyle*. Je nutné nastavit rozšířené styly konkrétní do pomocí ovládacího prvku rozšířené pole se seznamem pole [SetExtendedStyle](#setextendedstyle). Například použít `CreateEx` nastavit tyto styly jako WS_EX_CONTEXTHELP, ale použijte `SetExtendedStyle` nastavit tyto styly jako CBES_EX_CASESENSITIVE. Další informace najdete v tématu styly popsané v tématu [styly ovládacího prvku rozšířené ComboBoxEx](/windows/desktop/Controls/comboboxex-control-extended-styles) v sadě Windows SDK.

##  <a name="deleteitem"></a>  CComboBoxEx::DeleteItem

Odebere položku z `ComboBoxEx` ovládacího prvku.

```
int DeleteItem(int iIndex);
```

### <a name="parameters"></a>Parametry

*iIndex*<br/>
Z nuly vycházející index položky k odebrání.

### <a name="return-value"></a>Návratová hodnota

Počet zbývajících v ovládacím prvku položek. Pokud *iIndex* je neplatný, funkce vrátí CB_ERR.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje funkce zprávy [CBEM_DELETEITEM](/windows/desktop/Controls/cbem-deleteitem), jak je popsáno v sadě Windows SDK. Při volání DeleteItem, [WM_NOTIFY](/windows/desktop/controls/wm-notify) se pošle zpráva s oznámením CBEN_DELETEITEM do nadřazeného okna.

##  <a name="getcomboboxctrl"></a>  CComboBoxEx::GetComboBoxCtrl

Voláním této členské funkce získání ukazatele na prvek pole se seznamem v rámci `CComboBoxEx` objektu.

```
CComboBox* GetComboBoxCtrl();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel `CComboBox` objektu.

### <a name="remarks"></a>Poznámky

`CComboBoxEx` Ovládací prvek se skládá z nadřazené okno, který zapouzdřuje `CComboBox`.

`CComboBox` Objekt odkazovaný návratovou hodnotou je dočasný objekt a je zničen při nečinnosti příště zpracování.

##  <a name="geteditctrl"></a>  CComboBoxEx::GetEditCtrl

Voláním této členské funkce získání ukazatele na ovládací prvek pro úpravy pole se seznamem.

```
CEdit* GetEditCtrl();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel [CEdit](../../mfc/reference/cedit-class.md) objektu.

### <a name="remarks"></a>Poznámky

A `CComboBoxEx` ovládací prvek používá do textového pole při jeho vytváření stylem CBS_DROPDOWN.

`CEdit` Objekt odkazovaný návratovou hodnotou je dočasný objekt a je zničen při nečinnosti příště zpracování.

##  <a name="getextendedstyle"></a>  CComboBoxEx::GetExtendedStyle

Voláním této členské funkce, chcete-li získat rozšířené stylů použitých pro `CComboBoxEx` ovládacího prvku.

```
DWORD GetExtendedStyle() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota DWORD, která obsahuje rozšířené styly, které se používají pro ovládací prvek pole se seznamem.

### <a name="remarks"></a>Poznámky

Zobrazit [styly ovládacího prvku rozšířené ComboBoxEx](/windows/desktop/Controls/comboboxex-control-extended-styles) v sadě Windows SDK pro další informace o tyto styly.

##  <a name="getimagelist"></a>  CComboBoxEx::GetImageList

Voláním této členské funkce k získání ukazatele na seznam obrázků používané `CComboBoxEx` ovládacího prvku.

```
CImageList* GetImageList() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel [atributu CImageList](../../mfc/reference/cimagelist-class.md) objektu. Pokud selže, tato členská funkce vrátí hodnotu NULL.

### <a name="remarks"></a>Poznámky

`CImageList` Objekt odkazovaný návratovou hodnotou je dočasný objekt a je zničen při nečinnosti příště zpracování.

##  <a name="getitem"></a>  CComboBoxEx::GetItem

Načte položku informace pro danou `ComboBoxEx` položky.

```
BOOL GetItem(COMBOBOXEXITEM* pCBItem);
```

### <a name="parameters"></a>Parametry

*pCBItem*<br/>
Ukazatel [COMBOBOXEXITEM](/windows/desktop/api/commctrl/ns-commctrl-tagcomboboxexitema) struktura, která se zobrazí informace o položce.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud byla operace úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje funkce zprávy [CBEM_GETITEM](/windows/desktop/Controls/cbem-getitem), jak je popsáno v sadě Windows SDK.

##  <a name="haseditchanged"></a>  CComboBoxEx::HasEditChanged

Určuje, jestli se uživatel změnil obsah `ComboBoxEx` ovládací prvek textové pole tak, že zadáte.

```
BOOL HasEditChanged();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud uživatel zadal ovládacího prvku textového pole; jinak 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje funkce zprávy [CBEM_HASEDITCHANGED](/windows/desktop/Controls/cbem-haseditchanged), jak je popsáno v sadě Windows SDK.

##  <a name="insertitem"></a>  CComboBoxEx::InsertItem

Vloží novou položku `ComboBoxEx` ovládacího prvku.

```
int InsertItem(const COMBOBOXEXITEM* pCBItem);
```

### <a name="parameters"></a>Parametry

*pCBItem*<br/>
Ukazatel [COMBOBOXEXITEM](/windows/desktop/api/commctrl/ns-commctrl-tagcomboboxexitema) struktura, která se zobrazí informace o položce. Tato struktura obsahuje hodnoty příznak zpětného volání pro položku.

### <a name="return-value"></a>Návratová hodnota

Index, ve kterém byl vložen novou položku v případě úspěchu; v opačném případě hodnota-1.

### <a name="remarks"></a>Poznámky

Při volání `InsertItem`, [WM_NOTIFY](/windows/desktop/controls/wm-notify) zprávy s [CBEN_INSERTITEM](/windows/desktop/Controls/cben-insertitem) oznámení se odešlou do nadřazeného okna.

##  <a name="setextendedstyle"></a>  CComboBoxEx::SetExtendedStyle

Voláním této členské funkce pro nastavení rozšířené stylů použitých pro ovládacího prvku rozšířené pole se seznamem.

```
DWORD SetExtendedStyle(
    DWORD dwExMask,
    DWORD dwExStyles);
```

### <a name="parameters"></a>Parametry

*dwExMask*<br/>
Hodnotu typu DWORD určující styly, které v *dwExStyles* se bude ovlivněná. Rozšířené styly pouze v *dwExMask* se změní. Další styly se zachová, protože je. Pokud tento parametr je nula, pak všechny styly *dwExStyles* bude mít vliv.

*dwExStyles*<br/>
Hodnota DWORD obsahující ovládací prvek pole se seznamem rozšířené styly pro ovládací prvek.

### <a name="return-value"></a>Návratová hodnota

Hodnota DWORD, která obsahuje rozšířené styly dříve použité pro ovládací prvek.

### <a name="remarks"></a>Poznámky

Zobrazit [styly ovládacího prvku rozšířené ComboBoxEx](/windows/desktop/Controls/comboboxex-control-extended-styles) v sadě Windows SDK pro další informace o tyto styly.

Chcete-li vytvořit pole se seznamem rozšířené ovládací prvek s rozšířenou windows styly, použijte [CreateEx](#createex).

##  <a name="setimagelist"></a>  CComboBoxEx::SetImageList

Nastaví pro seznam obrázků `ComboBoxEx` ovládacího prvku.

```
CImageList* SetImageList(CImageList* pImageList);
```

### <a name="parameters"></a>Parametry

*pImageList*<br/>
Ukazatel `CImageList` objekt, který obsahuje Image na použití s `CComboBoxEx` ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Ukazatel [atributu CImageList](../../mfc/reference/cimagelist-class.md) objekt, který obsahuje obrázky dříve používané v `CComboBoxEx` ovládacího prvku. Hodnota NULL, pokud byl dříve nastaven žádný seznam obrázků.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje funkce zprávy [CBEM_SETIMAGELIST](/windows/desktop/Controls/cbem-setimagelist), jak je popsáno v sadě Windows SDK. Pokud změníte Výška ovládacích prvků pro výchozí úpravy, zavolejte funkci Win32 [SetWindowPos](/windows/desktop/api/winuser/nf-winuser-setwindowpos) pro změnu velikosti ovládacího prvku po zavolání `SetImageList`, nebo by se nezobrazil správně.

`CImageList` Objekt odkazovaný návratovou hodnotou je dočasný objekt a je zničen při nečinnosti příště zpracování.

##  <a name="setitem"></a>  CComboBoxEx::SetItem

Nastaví atributy pro položku `ComboBoxEx` ovládacího prvku.

```
BOOL SetItem(const COMBOBOXEXITEM* pCBItem);
```

### <a name="parameters"></a>Parametry

*pCBItem*<br/>
Ukazatel [COMBOBOXEXITEM](/windows/desktop/api/commctrl/ns-commctrl-tagcomboboxexitema) struktura, která se zobrazí informace o položce.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud byla operace úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje funkce zprávy [CBEM_SETITEM](/windows/desktop/Controls/cbem-setitem), jak je popsáno v sadě Windows SDK.

##  <a name="setwindowtheme"></a>  CComboBoxEx::SetWindowTheme

Nastaví vizuální styl rozšířené pole se seznamem ovládací prvek pole.

```
HRESULT SetWindowTheme(LPCWSTR pszSubAppName);
```

### <a name="parameters"></a>Parametry

*pszSubAppName*<br/>
Ukazatel na řetězec znaků Unicode, který obsahuje vizuální styl pole Rozšířené pole se seznamem pro nastavení.

### <a name="return-value"></a>Návratová hodnota

Návratová hodnota se nepoužívá.

### <a name="remarks"></a>Poznámky

Tato členská funkce emuluje funkčnost [CBEM_SETWINDOWTHEME](/windows/desktop/Controls/cbem-setwindowtheme) zprávu, jak je popsáno v sadě Windows SDK.

## <a name="see-also"></a>Viz také:

[Ukázky knihovny MFC MFCIE](../../visual-cpp-samples.md)<br/>
[CComboBox – třída](../../mfc/reference/ccombobox-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CComboBox – třída](../../mfc/reference/ccombobox-class.md)
