---
title: CComboBoxEx – třída
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
ms.openlocfilehash: 4151ea17fd3223c126715742c6149f2cf55bcbc7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369476"
---
# <a name="ccomboboxex-class"></a>CComboBoxEx – třída

Rozšiřuje ovládací prvek pole se seznamem tím, že poskytuje podporu pro seznamy obrázků.

## <a name="syntax"></a>Syntaxe

```
class CComboBoxEx : public CComboBox
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CComboBoxEx::CComboBoxEx](#ccomboboxex)|Vytvoří `CComboBoxEx` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CComboBoxEx::Vytvořit](#create)|Vytvoří pole se seznamem a `CComboBoxEx` připojí jej k objektu.|
|[CComboBoxEx::CreateEx](#createex)|Vytvoří pole se seznamem se zadanými rozšířenými `ComboBoxEx` styly systému Windows a připojí jej k objektu.|
|[CComboBoxEx::DeleteItem](#deleteitem)|Odebere položku `ComboBoxEx` z ovládacího prvku.|
|[CComboBoxEx::GetComboBoxCtrl](#getcomboboxctrl)|Načte ukazatel na podřízený ovládací prvek pole se seznamem.|
|[CComboBoxEx::GetEditCtrl](#geteditctrl)|Načte popisovač do ovládací části `ComboBoxEx` ovládacího prvku pro úpravy.|
|[CComboBoxEx::GetExtendedStyle](#getextendedstyle)|Načte rozšířené styly, které `ComboBoxEx` se používají pro ovládací prvek.|
|[CComboBoxEx::GetImageList](#getimagelist)|Načte ukazatel na seznam obrázků `ComboBoxEx` přiřazený ovládacímu prvku.|
|[CComboBoxEx::GetItem](#getitem)|Načte informace o `ComboBoxEx` položce pro danou položku.|
|[CComboBoxEx::HasEditChanged](#haseditchanged)|Určuje, zda uživatel změnil obsah `ComboBoxEx` ovládacího prvku úprav zadáním.|
|[CComboBoxEx::InsertItem](#insertitem)|Vloží novou položku `ComboBoxEx` do ovládacího prvku.|
|[CComboBoxEx::SetExtendedStyle](#setextendedstyle)|Nastaví rozšířené `ComboBoxEx` styly v rámci ovládacího prvku.|
|[CComboBoxEx::SetImageList](#setimagelist)|Nastaví seznam obrázků `ComboBoxEx` pro ovládací prvek.|
|[CComboBoxEx::SetItem](#setitem)|Nastaví atributy pro položku v ovládacím `ComboBoxEx` prvku.|
|[CComboBoxEx::SetWindowTheme](#setwindowtheme)|Nastaví vizuální styl rozšířeného ovládacího prvku pole se seznamem.|

## <a name="remarks"></a>Poznámky

Při `CComboBoxEx` vytváření ovládacích prvků se seznamem již nemusíte implementovat vlastní kód kreslení obrázků. Místo toho `CComboBoxEx` použijte pro přístup k obrázkům ze seznamu obrázků.

## <a name="image-list-support"></a>Podpora seznamu obrázků

Ve standardním poli se seznamem je vlastník pole se seznamem zodpovědný za kreslení obrázku vytvořením pole se seznamem jako ovládacíprvek kreslení vlastníka. Při použití `CComboBoxEx`není nutné nastavovat styly výkresu CBS_OWNERDRAWFIXED a CBS_HASSTRINGS, protože jsou implikované. V opačném případě je nutné napsat kód k provedení operací kreslení. Ovládací `CComboBoxEx` prvek podporuje až tři obrazy na položku: jeden pro vybraný stav, jeden pro nevybraný stav a jeden pro překryvný obraz.

## <a name="styles"></a>Styly

`CComboBoxEx`podporuje styly CBS_SIMPLE, CBS_DROPDOWN, CBS_DROPDOWNLIST a WS_CHILD. Všechny ostatní styly předané při vytváření okna jsou ovládacím prvkem ignorovány. Po vytvoření okna můžete zadat další styly pole `CComboBoxEx` se seznamem voláním členské funkce [SetExtendedStyle](#setextendedstyle). S těmito styly můžete:

- Nastavte hledání řetězců v seznamu tak, aby rozlišování malých a velkých písmen.

- Vytvořte ovládací prvek pole se seznamem, který používá\\znaky lomítka ('/'), zpětného lomítka (' a tečky ('.') jako oddělovače slov. To umožňuje uživatelům skákat z wordu na slovo pomocí klávesové zkratky CTRL+ ARROW.

- Nastavte ovládací prvek pole se seznamem tak, aby se obrázek zobrazoval nebo nezobrazoval. Pokud se nezobrazí žádný obrázek, pole se seznamem může odebrat odsazení textu, které je v ním přizpůsobeno.

- Vytvořte úzký ovládací prvek pole se seznamem, včetně jeho velikosti tak, aby osvoroval širší pole se seznamem, které obsahuje.

Tyto příznaky stylu jsou popsány dále v [použití CComboBoxEx](../../mfc/using-ccomboboxex.md).

## <a name="item-retention-and-callback-item-attributes"></a>Atributy uchování položek a zpětného volání

Informace o položkách, jako jsou indexy pro položky a obrázky, hodnoty odsazení a textové řetězce, jsou uloženy ve struktuře Win32 [COMBOBOXEXITEM](/windows/win32/api/commctrl/ns-commctrl-comboboxexitemw), jak je popsáno v sadě Windows SDK. Struktura také obsahuje členy, které odpovídají příznaky zpětného volání.

Podrobné koncepční diskuse naleznete [v tématu Použití CComboBoxEx](../../mfc/using-ccomboboxex.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[CComboBox](../../mfc/reference/ccombobox-class.md)

`CComboBoxEx`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxcmn.h

## <a name="ccomboboxexccomboboxex"></a><a name="ccomboboxex"></a>CComboBoxEx::CComboBoxEx

Volání této členské funkce `CComboBoxEx` k vytvoření objektu.

```
CComboBoxEx();
```

## <a name="ccomboboxexcreate"></a><a name="create"></a>CComboBoxEx::Vytvořit

Vytvoří pole se seznamem a `CComboBoxEx` připojí jej k objektu.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*dwStyl*<br/>
Určuje kombinaci stylů pole se seznamem aplikovaných na pole se seznamem. Další informace o stylech naleznete níže v **poznámkách.**

*Rect*<br/>
Odkaz na [CRect](../../atl-mfc-shared/reference/crect-class.md) objekt nebo [RECT](/previous-versions/dd162897\(v=vs.85\)) struktury, což je umístění a velikost pole se seznamem.

*pParentWnd*<br/>
Ukazatel na [cwnd](../../mfc/reference/cwnd-class.md) objekt, který je nadřazené `CDialog`okno pole se seznamem (obvykle a). Nesmí být null.

*Nid*<br/>
Určuje ID ovládacího prvku pole se seznamem.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byl objekt úspěšně vytvořen; jinak 0.

### <a name="remarks"></a>Poznámky

Vytvořte `CComboBoxEx` objekt ve dvou krocích:

1. Volání [CComboBoxEx](#ccomboboxex) k `CComboBoxEx` vytvoření objektu.

1. Volání této členské funkce, která vytvoří rozšířené pole se `CComboBoxEx` seznamem systému Windows a připojí jej k objektu.

Při volání `Create`knihovny MFC inicializuje běžné ovládací prvky.

Při vytváření pole se seznamem můžete určit některé nebo všechny následující styly pole se seznamem:

- CBS_SIMPLE

- CBS_DROPDOWN

- CBS_DROPDOWNLIST

- CBS_AUTOHSCROLL

- WS_CHILD

Všechny ostatní styly předané při vytváření okna jsou ignorovány. Ovládací `ComboBoxEx` prvek také podporuje rozšířené styly, které poskytují další funkce. Tyto styly jsou popsány v [ovládacím prvku ComboBoxEx rozšířené styly](/windows/win32/Controls/comboboxex-control-extended-styles), v sadě Windows SDK. Nastavte tyto styly voláním [SetExtendedStyle](#setextendedstyle).

Pokud chcete použít rozšířené styly oken s ovládacím `Create`prvkem, zavolejte [CreateEx](#createex) místo .

## <a name="ccomboboxexcreateex"></a><a name="createex"></a>CComboBoxEx::CreateEx

Volání této funkce vytvořit rozšířené ovládací prvek pole se seznamem `CComboBoxEx` (podřízené okno) a přidružit k objektu.

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*dwExStyl*<br/>
Určuje rozšířený styl vytvářeného ovládacího prvku. Seznam rozšířených stylů systému Windows naleznete v parametru *dwExStyle* pro [createwindowex](/windows/win32/api/winuser/nf-winuser-createwindowexw) v sadě Windows SDK.

*dwStyl*<br/>
Styl ovládacího prvku pole se seznamem. Seznam stylů najdete v tématu [Vytvoření.](#create)

*Rect*<br/>
Odkaz na [rect](/previous-versions/dd162897\(v=vs.85\)) strukturu popisující velikost a umístění okna, které mají být vytvořeny, v klientských souřadnicích *pParentWnd*.

*pParentWnd*<br/>
Ukazatel na okno, které je nadřazený ovládací prvek.

*Nid*<br/>
ID podřízeného okna ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Místo `CreateEx` toho `Create` použijte rozšířené styly systému Windows určené **předmluvou**rozšířeného stylu systému Windows WS_EX_ .

`CreateEx`vytvoří ovládací prvek s rozšířenými styly systému Windows určenými *dwExStyle*. Rozšířené styly je nutné nastavit specifické pro rozšířený ovládací prvek pole se seznamem pomocí [funkce SetExtendedStyle](#setextendedstyle). Použijte `CreateEx` například k nastavení takových stylů, `SetExtendedStyle` jako je WS_EX_CONTEXTHELP, ale slouží k nastavení takových stylů, jako je CBES_EX_CASESENSITIVE. Další informace naleznete v tématu [ComoBoxEx Control Extended Styles](/windows/win32/Controls/comboboxex-control-extended-styles) v sadě Windows SDK.

## <a name="ccomboboxexdeleteitem"></a><a name="deleteitem"></a>CComboBoxEx::DeleteItem

Odebere položku `ComboBoxEx` z ovládacího prvku.

```
int DeleteItem(int iIndex);
```

### <a name="parameters"></a>Parametry

*iIndex*<br/>
Nulový index položky, která má být odebrána.

### <a name="return-value"></a>Návratová hodnota

Počet položek, které zůstávají v ovládacím prvku. Pokud *je iIndex* neplatný, funkce vrátí CB_ERR.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje funkce [CBEM_DELETEITEM](/windows/win32/Controls/cbem-deleteitem)zpráv , jak je popsáno v sadě Windows SDK. Při volání DeleteItem bude odeslána [zpráva WM_NOTIFY](/windows/win32/controls/wm-notify) s oznámením CBEN_DELETEITEM do nadřazeného okna.

## <a name="ccomboboxexgetcomboboxctrl"></a><a name="getcomboboxctrl"></a>CComboBoxEx::GetComboBoxCtrl

Volání této členské funkce získat ukazatel na ovládací `CComboBoxEx` prvek pole se seznamem v rámci objektu.

```
CComboBox* GetComboBoxCtrl();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na `CComboBox` objekt.

### <a name="remarks"></a>Poznámky

Ovládací `CComboBoxEx` prvek se skládá z nadřazeného `CComboBox`okna, které zapouzdřuje .

Objekt, `CComboBox` na který se vztahuje vrácená hodnota, je dočasný objekt a je zničen během další doby zpracování nečinnosti.

## <a name="ccomboboxexgeteditctrl"></a><a name="geteditctrl"></a>CComboBoxEx::GetEditCtrl

Volání této členské funkce získat ukazatel na ovládací prvek upravit pro pole se seznamem.

```
CEdit* GetEditCtrl();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na objekt [CEdit.](../../mfc/reference/cedit-class.md)

### <a name="remarks"></a>Poznámky

Ovládací `CComboBoxEx` prvek používá editační pole při jeho vytvoření s CBS_DROPDOWN stylu.

Objekt, `CEdit` na který se vztahuje vrácená hodnota, je dočasný objekt a je zničen během další doby zpracování nečinnosti.

## <a name="ccomboboxexgetextendedstyle"></a><a name="getextendedstyle"></a>CComboBoxEx::GetExtendedStyle

Volání této členské funkce získat rozšířené `CComboBoxEx` styly používané pro ovládací prvek.

```
DWORD GetExtendedStyle() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota DWORD, která obsahuje rozšířené styly, které se používají pro ovládací prvek pole se seznamem.

### <a name="remarks"></a>Poznámky

Další informace o těchto stylech naleznete v tématu [Rozšířené styly ovládacího prvku ComboBoxEx](/windows/win32/Controls/comboboxex-control-extended-styles) v sadě Windows SDK.

## <a name="ccomboboxexgetimagelist"></a><a name="getimagelist"></a>CComboBoxEx::GetImageList

Volání této členské funkce získat ukazatel na seznam `CComboBoxEx` obrázků používá ovládací prvek.

```
CImageList* GetImageList() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na objekt [CImageList.](../../mfc/reference/cimagelist-class.md) Pokud se nezdaří, tato členská funkce vrátí hodnotu NULL.

### <a name="remarks"></a>Poznámky

Objekt, `CImageList` na který se vztahuje vrácená hodnota, je dočasný objekt a je zničen během další doby zpracování nečinnosti.

## <a name="ccomboboxexgetitem"></a><a name="getitem"></a>CComboBoxEx::GetItem

Načte informace o `ComboBoxEx` položce pro danou položku.

```
BOOL GetItem(COMBOBOXEXITEM* pCBItem);
```

### <a name="parameters"></a>Parametry

*pCBItem*<br/>
Ukazatel na [comboboxexitem](/windows/win32/api/commctrl/ns-commctrl-comboboxexitemw) struktury, která obdrží informace o položce.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byla operace úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje funkce [CBEM_GETITEM](/windows/win32/Controls/cbem-getitem)zpráv , jak je popsáno v sadě Windows SDK.

## <a name="ccomboboxexhaseditchanged"></a><a name="haseditchanged"></a>CComboBoxEx::HasEditChanged

Určuje, zda uživatel změnil obsah `ComboBoxEx` ovládacího prvku úprav zadáním.

```
BOOL HasEditChanged();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud uživatel zadal do textového pole ovládacího prvku; jinak 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje funkce [CBEM_HASEDITCHANGED](/windows/win32/Controls/cbem-haseditchanged)zprávy , jak je popsáno v sadě Windows SDK.

## <a name="ccomboboxexinsertitem"></a><a name="insertitem"></a>CComboBoxEx::InsertItem

Vloží novou položku `ComboBoxEx` do ovládacího prvku.

```
int InsertItem(const COMBOBOXEXITEM* pCBItem);
```

### <a name="parameters"></a>Parametry

*pCBItem*<br/>
Ukazatel na [comboboxexitem](/windows/win32/api/commctrl/ns-commctrl-comboboxexitemw) struktury, která obdrží informace o položce. Tato struktura obsahuje hodnoty příznaku zpětného volání pro položku.

### <a name="return-value"></a>Návratová hodnota

Index, ve kterém byla nová položka vložena, pokud byla úspěšná; jinak -1.

### <a name="remarks"></a>Poznámky

Při volání `InsertItem`bude do nadřazeného okna odeslána [WM_NOTIFY](/windows/win32/controls/wm-notify) zpráva s oznámením [CBEN_INSERTITEM.](/windows/win32/Controls/cben-insertitem)

## <a name="ccomboboxexsetextendedstyle"></a><a name="setextendedstyle"></a>CComboBoxEx::SetExtendedStyle

Volání této členské funkce nastavit rozšířené styly používané pro rozšířené ovládací prvek pole se seznamem.

```
DWORD SetExtendedStyle(
    DWORD dwExMask,
    DWORD dwExStyles);
```

### <a name="parameters"></a>Parametry

*dwExMaska*<br/>
Hodnota DWORD, která označuje, které styly v *dwExStyles* mají být ovlivněny. Budou změněny pouze rozšířené styly v *dwExMask.* Všechny ostatní styly budou zachovány tak, jak jsou. Pokud je tento parametr nula, budou ovlivněny všechny styly v *dwExStyles.*

*dwExStyly*<br/>
Hodnota DWORD, která obsahuje ovládací prvek se seznamem, rozšířené styly, které chcete nastavit pro ovládací prvek.

### <a name="return-value"></a>Návratová hodnota

Hodnota DWORD, která obsahuje rozšířené styly dříve používané pro ovládací prvek.

### <a name="remarks"></a>Poznámky

Další informace o těchto stylech naleznete v tématu [Rozšířené styly ovládacího prvku ComboBoxEx](/windows/win32/Controls/comboboxex-control-extended-styles) v sadě Windows SDK.

Chcete-li vytvořit rozšířený ovládací prvek se seznamem s rozšířenými styly oken, použijte [klávesu CreateEx](#createex).

## <a name="ccomboboxexsetimagelist"></a><a name="setimagelist"></a>CComboBoxEx::SetImageList

Nastaví seznam obrázků `ComboBoxEx` pro ovládací prvek.

```
CImageList* SetImageList(CImageList* pImageList);
```

### <a name="parameters"></a>Parametry

*seznam obrázků pImage*<br/>
Ukazatel na `CImageList` objekt obsahující obrazy, které `CComboBoxEx` mají být s ovládacím prvkem používány.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na objekt [CImageList](../../mfc/reference/cimagelist-class.md) obsahující obrazy dříve `CComboBoxEx` používané ovládacím prvkem. Null, pokud nebyl dříve nastaven žádný seznam obrázků.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje funkce [CBEM_SETIMAGELIST](/windows/win32/Controls/cbem-setimagelist)zpráv , jak je popsáno v sadě Windows SDK. Pokud změníte výšku výchozího ovládacího prvku pro úpravy, zavolejte funkci Win32 `SetImageList` [SetWindowPos,](/windows/win32/api/winuser/nf-winuser-setwindowpos) chcete-li změnit velikost ovládacího prvku po volání , nebo se nezobrazí správně.

Objekt, `CImageList` na který se vztahuje vrácená hodnota, je dočasný objekt a je zničen během další doby zpracování nečinnosti.

## <a name="ccomboboxexsetitem"></a><a name="setitem"></a>CComboBoxEx::SetItem

Nastaví atributy pro položku v ovládacím `ComboBoxEx` prvku.

```
BOOL SetItem(const COMBOBOXEXITEM* pCBItem);
```

### <a name="parameters"></a>Parametry

*pCBItem*<br/>
Ukazatel na [comboboxexitem](/windows/win32/api/commctrl/ns-commctrl-comboboxexitemw) struktury, která obdrží informace o položce.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byla operace úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje funkce [CBEM_SETITEM](/windows/win32/Controls/cbem-setitem)zprávy , jak je popsáno v sadě Windows SDK.

## <a name="ccomboboxexsetwindowtheme"></a><a name="setwindowtheme"></a>CComboBoxEx::SetWindowTheme

Nastaví vizuální styl rozšířeného ovládacího prvku pole se seznamem.

```
HRESULT SetWindowTheme(LPCWSTR pszSubAppName);
```

### <a name="parameters"></a>Parametry

*pszSubAppName*<br/>
Ukazatel na řetězec Unicode, který obsahuje rozšířený vizuální styl pole se seznamem, který chcete nastavit.

### <a name="return-value"></a>Návratová hodnota

Vrácená hodnota se nepoužívá.

### <a name="remarks"></a>Poznámky

Tato členská funkce emuluje funkce [zprávy CBEM_SETWINDOWTHEME,](/windows/win32/Controls/cbem-setwindowtheme) jak je popsáno v sadě Windows SDK.

## <a name="see-also"></a>Viz také

[MFC ukázka MFCIE](../../overview/visual-cpp-samples.md)<br/>
[Třída CComboBox](../../mfc/reference/ccombobox-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třída CComboBox](../../mfc/reference/ccombobox-class.md)
