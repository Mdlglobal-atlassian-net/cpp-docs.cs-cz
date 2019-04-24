---
title: CStatusBarCtrl Class
ms.date: 11/04/2016
f1_keywords:
- CStatusBarCtrl
- AFXCMN/CStatusBarCtrl
- AFXCMN/CStatusBarCtrl::CStatusBarCtrl
- AFXCMN/CStatusBarCtrl::Create
- AFXCMN/CStatusBarCtrl::CreateEx
- AFXCMN/CStatusBarCtrl::DrawItem
- AFXCMN/CStatusBarCtrl::GetBorders
- AFXCMN/CStatusBarCtrl::GetIcon
- AFXCMN/CStatusBarCtrl::GetParts
- AFXCMN/CStatusBarCtrl::GetRect
- AFXCMN/CStatusBarCtrl::GetText
- AFXCMN/CStatusBarCtrl::GetTextLength
- AFXCMN/CStatusBarCtrl::GetTipText
- AFXCMN/CStatusBarCtrl::IsSimple
- AFXCMN/CStatusBarCtrl::SetBkColor
- AFXCMN/CStatusBarCtrl::SetIcon
- AFXCMN/CStatusBarCtrl::SetMinHeight
- AFXCMN/CStatusBarCtrl::SetParts
- AFXCMN/CStatusBarCtrl::SetSimple
- AFXCMN/CStatusBarCtrl::SetText
- AFXCMN/CStatusBarCtrl::SetTipText
helpviewer_keywords:
- CStatusBarCtrl [MFC], CStatusBarCtrl
- CStatusBarCtrl [MFC], Create
- CStatusBarCtrl [MFC], CreateEx
- CStatusBarCtrl [MFC], DrawItem
- CStatusBarCtrl [MFC], GetBorders
- CStatusBarCtrl [MFC], GetIcon
- CStatusBarCtrl [MFC], GetParts
- CStatusBarCtrl [MFC], GetRect
- CStatusBarCtrl [MFC], GetText
- CStatusBarCtrl [MFC], GetTextLength
- CStatusBarCtrl [MFC], GetTipText
- CStatusBarCtrl [MFC], IsSimple
- CStatusBarCtrl [MFC], SetBkColor
- CStatusBarCtrl [MFC], SetIcon
- CStatusBarCtrl [MFC], SetMinHeight
- CStatusBarCtrl [MFC], SetParts
- CStatusBarCtrl [MFC], SetSimple
- CStatusBarCtrl [MFC], SetText
- CStatusBarCtrl [MFC], SetTipText
ms.assetid: 8504ad38-7b91-4746-aede-ac98886eb47b
ms.openlocfilehash: 8db2be9b14f9d60f2103ce0b63b772962b079bbe
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62323827"
---
# <a name="cstatusbarctrl-class"></a>CStatusBarCtrl Class

Poskytuje funkce pro Windows běžné stav panelu ovládacího prvku.

## <a name="syntax"></a>Syntaxe

```
class CStatusBarCtrl : public CWnd
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CStatusBarCtrl::CStatusBarCtrl](#cstatusbarctrl)|Vytvoří `CStatusBarCtrl` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CStatusBarCtrl::Create](#create)|Vytvoří ovládací prvek panelu stavu a připojí ho k `CStatusBarCtrl` objektu.|
|[CStatusBarCtrl::CreateEx](#createex)|Vytvoří ovládací prvek panelu stavu se zadaným rozšířené styly Windows a připojí ho k `CStatusBarCtrl` objektu.|
|[CStatusBarCtrl::DrawItem](#drawitem)|Volá se při úpravě vizuálního aspektu stav vykreslené vlastníkem panel ovládacího prvku změní.|
|[CStatusBarCtrl::GetBorders](#getborders)|Načte aktuální šířky vodorovného a svislého ohraničení ovládacího prvku panelu stavu.|
|[CStatusBarCtrl::GetIcon](#geticon)|Načte ikonu pro určitou část (označované také jako podokno) v ovládacím prvku panel aktuální stav.|
|[CStatusBarCtrl::GetParts](#getparts)|Získá počet částí v ovládacím prvku panel stavu.|
|[CStatusBarCtrl::GetRect](#getrect)|Načte ohraničující obdélník část v ovládacím prvku panel stavu.|
|[CStatusBarCtrl::GetText](#gettext)|Načte text z dané části ovládacího prvku panelu stavu.|
|[CStatusBarCtrl::GetTextLength](#gettextlength)|Načte délka ve znacích textu z části daného ovládacího prvku panelu stavu.|
|[CStatusBarCtrl::GetTipText](#gettiptext)|Načte text popisku pro podokno ve stavovém řádku.|
|[CStatusBarCtrl::IsSimple](#issimple)|Kontroluje stav ovládacího prvku okno k určení, zda je v stručném režimu.|
|[CStatusBarCtrl::SetBkColor](#setbkcolor)|Nastaví barvu pozadí ve stavovém řádku.|
|[CStatusBarCtrl::SetIcon](#seticon)|Určuje ikonu pro podokno ve stavovém řádku.|
|[CStatusBarCtrl::SetMinHeight](#setminheight)|Nastaví minimální výšku stav panelu oblasti pro kreslení ovládacího prvku.|
|[CStatusBarCtrl::SetParts](#setparts)|Nastaví počet částí ve stavovém řádku ovládacího prvku a souřadnice pravého okraje každé části.|
|[CStatusBarCtrl::SetSimple](#setsimple)|Určuje, zda ovládací prvek panelu stavu zobrazí jednoduchý text nebo zobrazí všechny části ovládacího prvku nastavil předchozí volání k `SetParts`.|
|[CStatusBarCtrl::SetText](#settext)|Nastaví text v dané části ovládacího prvku panelu stavu.|
|[CStatusBarCtrl::SetTipText](#settiptext)|Nastaví text popisu tlačítka pro podokno ve stavovém řádku.|

## <a name="remarks"></a>Poznámky

"Stav panelu ovládacího prvku" je horizontální okno, obvykle se zobrazí v dolní části nadřazené okno, ve kterém může aplikace zobrazit různé druhy informací o stavu. Ovládací prvek panelu stavu je možné rozdělit na části zobrazíte více než jeden typ informací.

Tento ovládací prvek (a tedy `CStatusBarCtrl` třídy) je dostupná jenom pro programy spuštěné v rámci Windows 95/98 a Windows NT verze 3.51 a vyšší.

Další informace o používání `CStatusBarCtrl`, naleznete v tématu [ovládací prvky](../../mfc/controls-mfc.md) a [použití třídy CStatusBarCtrl](../../mfc/using-cstatusbarctrl.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CStatusBarCtrl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxcmn.h

##  <a name="create"></a>  CStatusBarCtrl::Create

Vytvoří ovládací prvek panelu stavu a připojí ho k `CStatusBarCtrl` objektu.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*dwStyle*<br/>
Určuje styl ovládacího prvku panelu stavu. Použít libovolnou kombinaci stavového řádku – styly ovládacích prvků, které jsou uvedeny v [– styly běžných ovládacích prvků](/windows/desktop/Controls/common-control-styles) v sadě Windows SDK. Tento parametr musí obsahovat WS_CHILD style. Měl by obsahovat také WS_VISIBLE style.

*Rect*<br/>
Určuje ovládací prvek panelu stavu velikost a umístění. Může být buď [crect –](../../atl-mfc-shared/reference/crect-class.md) objektu nebo [RECT](/previous-versions/dd162897\(v=vs.85\)) struktury.

*pParentWnd*<br/>
Určuje stavového řádku nadřazené okno ovládacího prvku, obvykle `CDialog`. Nesmí být NULL.

*nID*<br/>
Určuje ID ovládacího prvku panelu stavu.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak nula.

### <a name="remarks"></a>Poznámky

Můžete vytvořit `CStatusBarCtrl` ve dvou krocích. Nejprve volat konstruktor a poté zavolejte `Create`, což vytvoří ovládací prvek panelu stavu a připojí ho k `CStatusBarCtrl` objektu.

Výchozí pozice okna. stav je v dolní části okna nadřazené, ale můžete určit styl CCS_TOP na něm se zobrazí v horní části klientské oblasti okna nadřazené. Můžete určit styl SBARS_SIZEGRIP zahrnout úchyt na pravém konci stavové okno. Kombinace stylů CCS_TOP a SBARS_SIZEGRIP se nedoporučuje, protože výsledná úchyt pro změnu velikosti není funkční, přestože systém nakreslí ho v okně Stav.

Chcete-li vytvořit stavový řádek s rozšířené styly oken, zavolejte [CStatusBarCtrl::CreateEx](#createex) místo `Create`.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CStatusBarCtrl#1](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_1.cpp)]

##  <a name="createex"></a>  CStatusBarCtrl::CreateEx

Vytvoří ovládací prvek (podřízené okno) a přidruží ji k `CStatusBarCtrl` objektu.

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
Určuje styl ovládacího prvku panelu stavu. Použít libovolnou kombinaci stavového řádku – styly ovládacích prvků, které jsou uvedeny v [– styly běžných ovládacích prvků](/windows/desktop/Controls/common-control-styles) v sadě Windows SDK. Tento parametr musí obsahovat WS_CHILD style. Měl by obsahovat také WS_VISIBLE style.

*Rect*<br/>
Odkaz na [RECT](/previous-versions/dd162897\(v=vs.85\)) struktura popisující, velikost a umístění okna, které nelze v souřadnice klienta *pParentWnd*.

*pParentWnd*<br/>
Ukazatel na okno, který je nadřazeného ovládacího prvku.

*nID*<br/>
ID ovládacího prvku podřízené okno.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Použití `CreateEx` místo [vytvořit](#create) použít rozšířené styly Windows určené předponu rozšířeného stylu Windows **WS_EX_**.

##  <a name="cstatusbarctrl"></a>  CStatusBarCtrl::CStatusBarCtrl

Vytvoří `CStatusBarCtrl` objektu.

```
CStatusBarCtrl();
```

##  <a name="drawitem"></a>  CStatusBarCtrl::DrawItem

Volá se rozhraním při úpravě vizuálního aspektu stav vykreslené vlastníkem panel ovládacího prvku změní.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Parametry

*lpDrawItemStruct*<br/>
Dlouhým ukazatelem na [drawitemstruct –](/windows/desktop/api/winuser/ns-winuser-tagdrawitemstruct) strukturu, která obsahuje informace o typu kreslení vyžaduje.

### <a name="remarks"></a>Poznámky

`itemAction` Člena `DRAWITEMSTRUCT` struktury definuje výkresu akci, která se má provést.

Tato členská funkce ve výchozím nastavení nemá žádný účinek. Přepsat tato členská funkce implementovat kreslení pro vykreslené vlastníkem `CStatusBarCtrl` objektu.

Aplikace by měl obnovit všechny grafiky zařízení rozhraní GDI systému objekty vybrané pro zadaný kontext zobrazení v *lpDrawItemStruct* před tento člen funkce skončí.

##  <a name="getborders"></a>  CStatusBarCtrl::GetBorders

Načte ovládací prvek panelu stavu aktuální šířky vodorovného a svislého ohraničení a mezery mezi obdélníků.

```
BOOL GetBorders(int* pBorders) const;

BOOL GetBorders(
    int& nHorz,
    int& nVert,
    int& nSpacing) const;
```

### <a name="parameters"></a>Parametry

*pBorders*<br/>
Adresa celočíselné pole s tři elementy. První prvek dostane šířka vodorovného ohraničení, druhý přijme šířku ohraničení svislé a třetí obdrží šířku ohraničení mezi obdélníků.

*nHorz*<br/>
Odkaz na celé číslo, které přijímá šířka vodorovného ohraničení.

*nVert*<br/>
Odkaz na celé číslo, které přijímá šířku ohraničení svislý.

*nSpacing*<br/>
Odkaz na celé číslo, které přijímá šířku ohraničení mezi obdélníků.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak nula.

### <a name="remarks"></a>Poznámky

Tyto ohraničení určují mezery mezi vnější okraj ovládacího prvku a obdélníky v ovládacím prvku, které obsahují text.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CStatusBarCtrl#2](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_2.cpp)]

##  <a name="geticon"></a>  CStatusBarCtrl::GetIcon

Načte ikonu pro určitou část (označované také jako podokno) v ovládacím prvku panel aktuální stav.

```
HICON GetIcon(int iPart) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*iPart*|[in] Z nuly vycházející index části, která obsahuje ikonu, která se má načíst. Pokud má parametr hodnotu -1, stavový řádek je považován za jednoduchý režim stavový řádek.|

### <a name="return-value"></a>Návratová hodnota

Popisovač na ikonu-li metoda úspěšná. v opačném případě hodnota NULL.

### <a name="remarks"></a>Poznámky

Tato metoda odesílá [SB_GETICON](/windows/desktop/Controls/sb-geticon) zprávu, která je popsána v sadě Windows SDK.

Ovládací prvek panelu stavu se skládá z řádku výstupní podokna textu, které se také označují jako částí. Další informace o stavového řádku, naleznete v tématu [stav panelu implementace v prostředí MFC](../../mfc/status-bar-implementation-in-mfc.md) a [nastavení režimu objektu CStatusBarCtrl](../../mfc/setting-the-mode-of-a-cstatusbarctrl-object.md).

### <a name="example"></a>Příklad

Následující příklad kódu definuje proměnnou, `m_statusBar`, která je pro přístup k ovládacím panelu aktuální stav. Tato proměnná se používá v následujícím příkladu.

[!code-cpp[NVC_MFC_CStatusBarCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_3.h)]

### <a name="example"></a>Příklad

Následující příklad kódu zkopíruje do dvou podoken aktuální stav ovládacího panelu ikonu. V dřívější části příklad kódu vytvořili jsme ovládacích prvků panelu Stav s tři podokna a pak přidá do podokna první ikona. Tento příklad načte ikonu z podokna první a poté jej přidá do podokna druhý a třetí.

[!code-cpp[NVC_MFC_CStatusBarCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_4.cpp)]

##  <a name="getparts"></a>  CStatusBarCtrl::GetParts

Získá počet částí v ovládacím prvku panel stavu.

```
int GetParts(
    int nParts,
    int* pParts) const;
```

### <a name="parameters"></a>Parametry

*nParts*<br/>
Počet částí, které se mají načíst souřadnice. Pokud tento parametr je větší než počet částí v ovládacím prvku, načte zprávy souřadnic pro existující pouze části.

*pParts*<br/>
Adresa celočíselné pole mají stejný počet prvků jako počet částí určené *nParts*. Každý prvek v poli obdrží klient souřadnice pravého okraje odpovídající části. Pokud element je nastavená na hodnotu - 1, pozice pravého okraje pro tuto část rozšiřuje na pravý okraj na stavovém řádku.

### <a name="return-value"></a>Návratová hodnota

Počet částí v ovládacím prvku v případě úspěchu nebo nula, jinak.

### <a name="remarks"></a>Poznámky

Tato členská funkce také načte souřadnice pravého okraje podle zadaného počtu částí.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CStatusBarCtrl#3](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_5.cpp)]

##  <a name="getrect"></a>  CStatusBarCtrl::GetRect

Načte ohraničující obdélník část v ovládacím prvku panel stavu.

```
BOOL GetRect(
    int nPane,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>Parametry

*nPane*<br/>
Z nuly vycházející index části, jehož ohraničující obdélník má být načtena.

*lpRect*<br/>
Adresa [RECT](/previous-versions/dd162897\(v=vs.85\)) struktura, která přijímá ohraničující obdélník.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak nula.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CStatusBarCtrl#4](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_6.cpp)]

##  <a name="gettext"></a>  CStatusBarCtrl::GetText

Načte text z dané části ovládacího prvku panelu stavu.

```
CString GetText(
    int nPane,
    int* pType = NULL) const;

int GetText(
    LPCTSTR lpszText,
    int nPane,
    int* pType = NULL) const;
```

### <a name="parameters"></a>Parametry

*lpszText*<br/>
Adresa vyrovnávací paměti, která přijímá text. Tento parametr je řetězec zakončený hodnotou null.

*nPane*<br/>
Z nuly vycházející index části, ze kterého se má načíst text.

*pType*<br/>
Ukazatel na celé číslo, které obdrží informace o typu. Typ může být jedna z těchto hodnot:

- **0** text je vykreslen s nižší než roviny stavového řádku se zobrazí ohraničení.

- Bez ohraničení je vykreslen SBT_NOBORDERS text.

- SBT_POPOUT text je vykreslen s ohraničení se zobrazovat na vyšších než rovina stavový řádek.

- SBT_OWNERDRAW Pokud text má SBT_OWNERDRAW typu, výkresu *pType* obdrží tuto zprávu a vrátí hodnotu 32-bit spojené s textem místo typu délku a operace.

### <a name="return-value"></a>Návratová hodnota

Délka ve znacích, textu nebo [CString](../../atl-mfc-shared/reference/cstringt-class.md) obsahující aktuální text.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CStatusBarCtrl#5](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_7.cpp)]

##  <a name="gettextlength"></a>  CStatusBarCtrl::GetTextLength

Načte délka ve znacích textu z části daného ovládacího prvku panelu stavu.

```
int GetTextLength(
    int nPane,
    int* pType = NULL) const;
```

### <a name="parameters"></a>Parametry

*nPane*<br/>
Z nuly vycházející index části, ze kterého se má načíst text.

*pType*<br/>
Ukazatel na celé číslo, které obdrží informace o typu. Typ může být jedna z těchto hodnot:

- **0** text je vykreslen s nižší než roviny stavového řádku se zobrazí ohraničení.

- Bez ohraničení je vykreslen SBT_NOBORDERS text.

- SBT_OWNERDRAW text je vykreslen pomocí nadřazeného okna.

- SBT_POPOUT text je vykreslen s ohraničení se zobrazovat na vyšších než rovina stavový řádek.

### <a name="return-value"></a>Návratová hodnota

Délka ve znacích textu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CStatusBarCtrl#6](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_8.cpp)]

##  <a name="gettiptext"></a>  CStatusBarCtrl::GetTipText

Načte text popisku pro podokno ve stavovém řádku.

```
CString GetTipText(int nPane) const;
```

### <a name="parameters"></a>Parametry

*nPane*<br/>
Index založený na nule podokno panelu stavu na přijetí textu popisku.

### <a name="return-value"></a>Návratová hodnota

A [CString](../../atl-mfc-shared/reference/cstringt-class.md) objekt obsahující text, který se použije v popisu.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [SB_GETTIPTEXT](/windows/desktop/Controls/sb-gettiptext), jak je popsáno v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CStatusBarCtrl#7](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_9.cpp)]

##  <a name="issimple"></a>  CStatusBarCtrl::IsSimple

Kontroluje stav ovládacího prvku okno k určení, zda je v stručném režimu.

```
BOOL IsSimple() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je ovládací prvek okno stavu v stručném režimu; jinak nula.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [SB_ISSIMPLE](/windows/desktop/Controls/sb-issimple), jak je popsáno v sadě Windows SDK.

##  <a name="setbkcolor"></a>  CStatusBarCtrl::SetBkColor

Nastaví barvu pozadí ve stavovém řádku.

```
COLORREF SetBkColor(COLORREF cr);
```

### <a name="parameters"></a>Parametry

*cr*<br/>
COLORREF hodnota, která určuje novou barvou pozadí. Zadejte hodnotu CLR_DEFAULT způsobit stavový řádek používat jeho výchozí barvu pozadí.

### <a name="return-value"></a>Návratová hodnota

A [COLORREF](/windows/desktop/gdi/colorref) hodnotu, která představuje předchozí výchozí barvu pozadí.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [SB_SETBKCOLOR](/windows/desktop/Controls/sb-setbkcolor), jak je popsáno v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CStatusBarCtrl#8](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_10.cpp)]

##  <a name="seticon"></a>  CStatusBarCtrl::SetIcon

Určuje ikonu pro podokno ve stavovém řádku.

```
BOOL SetIcon(
    int nPane,
    HICON hIcon);
```

### <a name="parameters"></a>Parametry

*nPane*<br/>
Index založený na nule v podokně se zobrazí ikona. Pokud má parametr hodnotu -1, stavový řádek je považován za jednoduché stavový řádek.

*hIcon*<br/>
Zpracování na ikonu nastavení. Pokud je tato hodnota NULL, odeberou se z části ikonu.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak nula.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [SB_SETICON](/windows/desktop/Controls/sb-seticon), jak je popsáno v sadě Windows SDK.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CStatusBarCtrl::SetBkColor](#setbkcolor).

##  <a name="setminheight"></a>  CStatusBarCtrl::SetMinHeight

Nastaví minimální výšku stav panelu oblasti pro kreslení ovládacího prvku.

```
void SetMinHeight(int nMin);
```

### <a name="parameters"></a>Parametry

*nMin*<br/>
Minimální výška v pixelech, ovládacího prvku.

### <a name="remarks"></a>Poznámky

Minimální výška je součet *Nminimum* a dvakrát šířku v pixelech, svislé ohraničení ovládacího prvku panelu stavu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CStatusBarCtrl#9](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_11.cpp)]

##  <a name="setparts"></a>  CStatusBarCtrl::SetParts

Nastaví počet částí ve stavovém řádku ovládacího prvku a souřadnice pravého okraje každé části.

```
BOOL SetParts(
    int nParts,
    int* pWidths);
```

### <a name="parameters"></a>Parametry

*nParts*<br/>
Počet částí k nastavení. Počet částí nemůže být větší než 255.

*pWidths*<br/>
Adresa celočíselné pole mají stejný počet prvků jako části určené *nParts*. Každý prvek v poli určuje umístění klienta souřadnice pravého okraje odpovídající části. Pokud je element - 1, pozice pravého okraje pro tuto část rozšiřuje na pravý okraj ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak nula.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CStatusBarCtrl#10](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_12.cpp)]

##  <a name="setsimple"></a>  CStatusBarCtrl::SetSimple

Určuje, zda ovládací prvek panelu stavu zobrazí jednoduchý text nebo zobrazí všechny části ovládacího prvku nastavil předchozí volání [SetParts](#setparts).

```
BOOL SetSimple(BOOL bSimple = TRUE);
```

### <a name="parameters"></a>Parametry

*bSimple*<br/>
[in] Příznak zobrazení typu. Pokud tento parametr má hodnotu TRUE, ovládací prvek zobrazí jednoduchý text; Pokud je FALSE, zobrazí se více částí.

### <a name="return-value"></a>Návratová hodnota

Vždy vrátí hodnotu 0.

### <a name="remarks"></a>Poznámky

Pokud aplikace změní ovládací prvek panelu stavu z neprostého jednoduchý, nebo naopak, systém okamžitě překreslí ovládacího prvku.

##  <a name="settext"></a>  CStatusBarCtrl::SetText

Nastaví text v dané části ovládacího prvku panelu stavu.

```
BOOL SetText(
    LPCTSTR lpszText,
    int nPane,
    int nType);
```

### <a name="parameters"></a>Parametry

*lpszText*<br/>
Adresa řetězec zakončený hodnotou null zadáte text, který má nastavit. Pokud *nTyp* je SBT_OWNERDRAW, *lpszText* představuje 32 bitů data.

*nPane*<br/>
Z nuly vycházející index části nastavit. Pokud je tato hodnota 255, ovládací prvek panelu stavu je považován za jednoduché ovládací prvek s pouze jednu část.

*nType*<br/>
Typ operace kreslení. Zobrazit [SB_SETTEXT zpráva](/windows/desktop/Controls/sb-settext) seznam možných hodnot.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak nula.

### <a name="remarks"></a>Poznámky

Zpráva zruší platnost části ovládacího prvku, který se změnil, by ji zobrazíte novým textem, když ovládací prvek dále obdrží zprávu WM_PAINT.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CStatusBarCtrl#11](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_13.cpp)]

##  <a name="settiptext"></a>  CStatusBarCtrl::SetTipText

Nastaví text popisu tlačítka pro podokno ve stavovém řádku.

```
void SetTipText(
    int nPane,
    LPCTSTR pszTipText);
```

### <a name="parameters"></a>Parametry

*nPane*<br/>
Index založený na nule podokno panelu stavu na přijetí textu popisku.

*pszTipText*<br/>
Ukazatel na řetězec obsahující text popisku.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [SB_SETTIPTEXT](/windows/desktop/Controls/sb-settiptext), jak je popsáno v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CStatusBarCtrl#12](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_14.cpp)]

## <a name="see-also"></a>Viz také:

[CWnd – třída](../../mfc/reference/cwnd-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CToolBarCtrl – třída](../../mfc/reference/ctoolbarctrl-class.md)
