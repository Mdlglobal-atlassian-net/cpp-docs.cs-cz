---
title: Cstatusbar – třída
ms.date: 11/04/2016
f1_keywords:
- CStatusBar
- AFXEXT/CStatusBar
- AFXEXT/CStatusBar::CStatusBar
- AFXEXT/CStatusBar::CommandToIndex
- AFXEXT/CStatusBar::Create
- AFXEXT/CStatusBar::CreateEx
- AFXEXT/CStatusBar::DrawItem
- AFXEXT/CStatusBar::GetItemID
- AFXEXT/CStatusBar::GetItemRect
- AFXEXT/CStatusBar::GetPaneInfo
- AFXEXT/CStatusBar::GetPaneStyle
- AFXEXT/CStatusBar::GetPaneText
- AFXEXT/CStatusBar::GetStatusBarCtrl
- AFXEXT/CStatusBar::SetIndicators
- AFXEXT/CStatusBar::SetPaneInfo
- AFXEXT/CStatusBar::SetPaneStyle
- AFXEXT/CStatusBar::SetPaneText
helpviewer_keywords:
- CStatusBar [MFC], CStatusBar
- CStatusBar [MFC], CommandToIndex
- CStatusBar [MFC], Create
- CStatusBar [MFC], CreateEx
- CStatusBar [MFC], DrawItem
- CStatusBar [MFC], GetItemID
- CStatusBar [MFC], GetItemRect
- CStatusBar [MFC], GetPaneInfo
- CStatusBar [MFC], GetPaneStyle
- CStatusBar [MFC], GetPaneText
- CStatusBar [MFC], GetStatusBarCtrl
- CStatusBar [MFC], SetIndicators
- CStatusBar [MFC], SetPaneInfo
- CStatusBar [MFC], SetPaneStyle
- CStatusBar [MFC], SetPaneText
ms.assetid: a3bde3db-e71c-4881-a3ca-1d5481c345ba
ms.openlocfilehash: cb52f1138ba7ff01c6fbf2f7ec13d5f39e9422d8
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57413391"
---
# <a name="cstatusbar-class"></a>Cstatusbar – třída

Ovládací panel s řádkem podoken textového výstupu nebo "ukazatelů".

## <a name="syntax"></a>Syntaxe

```
class CStatusBar : public CControlBar
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CStatusBar::CStatusBar](#cstatusbar)|Vytvoří `CStatusBar` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CStatusBar::CommandToIndex](#commandtoindex)|Získá index pro ID daného indikátoru.|
|[CStatusBar::Create](#create)|Vytvoří stavového řádku, připojí se k `CStatusBar` objekt a nastaví počáteční výška písma a panelem.|
|[CStatusBar::CreateEx](#createex)|Vytvoří `CStatusBar` objekt s další styly pro vložený `CStatusBarCtrl` objektu.|
|[CStatusBar::DrawItem](#drawitem)|Volá se při úpravě vizuálního aspektu stav vykreslené vlastníkem panel ovládacího prvku změní.|
|[CStatusBar::GetItemID](#getitemid)|Získá ukazatel ID pro daný index.|
|[CStatusBar::GetItemRect](#getitemrect)|Získá zobrazení rámeček pro daný index.|
|[CStatusBar::GetPaneInfo](#getpaneinfo)|Získá ID ukazatele, styl a šířku pro daný index.|
|[CStatusBar::GetPaneStyle](#getpanestyle)|Získá styl indikátoru pro daný index.|
|[CStatusBar::GetPaneText](#getpanetext)|Získá text indikátoru pro daný index.|
|[CStatusBar::GetStatusBarCtrl](#getstatusbarctrl)|Umožňuje přímý přístup k podkladové běžný ovládací prvek.|
|[CStatusBar::SetIndicators](#setindicators)|Nastaví ID indikátoru.|
|[CStatusBar::SetPaneInfo](#setpaneinfo)|Nastaví ID ukazatele, styl a šířku pro daný index.|
|[CStatusBar::SetPaneStyle](#setpanestyle)|Nastaví styl indikátoru pro daný index.|
|[CStatusBar::SetPaneText](#setpanetext)|Nastaví text indikátoru pro daný index.|

## <a name="remarks"></a>Poznámky

Výstupní podokna běžně slouží jako zprávy řádky a indikátory stavu. Mezi příklady patří řádky zprávu nápovědy nabídky, která stručně popisují příkaz vybrané nabídky a indikátory, které zobrazují stav SCROLL LOCK, NUM LOCK a další klíče.

[CStatusBar::GetStatusBarCtrl](#getstatusbarctrl), členské funkce nové knihovny MFC 4.0, vám umožní využít výhod podpory Windows běžné ovládacího prvku pro stavového řádku vlastního nastavení a další funkce. `CStatusBar` Členské funkce vám poskytnou většinu funkcí běžných ovládacích prvků Windows; ale při volání `GetStatusBarCtrl`, které poskytnete stavové řádky i více vlastností stavového řádku Windows 95/98. Při volání `GetStatusBarCtrl`, vrátí odkaz na `CStatusBarCtrl` objektu. Zobrazit [CStatusBarCtrl](../../mfc/reference/cstatusbarctrl-class.md) pro další informace o navrhování panely nástrojů, použití běžných ovládacích prvků Windows. Další obecné informace o běžných ovládacích prvků naleznete v tématu [běžné ovládací prvky](/windows/desktop/Controls/common-controls-intro) v sadě Windows SDK.

Rozhraní framework ukládá ukazatel informace v poli s nejvíce vlevo ukazatel na pozici 0. Při vytváření stavového řádku, použijte pole ID, které rozhraní přidruží odpovídající ukazatele řetězce. Pak můžete pomocí ID řetězce nebo indexu přístup indikátor.

Standardně je první indikátor "elastické": trvá až délka stavového řádku nepoužívá jiná podokna indikátor tak, aby jiná podokna jsou zarovnaná vpravo.

Chcete-li vytvořit stavového řádku, postupujte takto:

1. Vytvořit `CStatusBar` objektu.

1. Volání [vytvořit](#create) (nebo [CreateEx](#createex)) funkci pro vytváření stavového řádku okna a připojte ji k `CStatusBar` objektu.

1. Volání [SetIndicators](#setindicators) přidružit každý indikátor Identifikátoru řetězce.

Existují tři způsoby, jak aktualizovat textu panelu stavového řádku:

1. Volání [CWnd::SetWindowText](../../mfc/reference/cwnd-class.md#setwindowtext) k aktualizaci textu v podokně pouze 0.

1. Volání [CCmdUI::SetText](../../mfc/reference/ccmdui-class.md#settext) v obslužné rutině ON_UPDATE_COMMAND_UI stavový řádek.

1. Volání [SetPaneText](#setpanetext) k aktualizaci textu pro všechna podokna.

Volání [SetPaneStyle](#setpanestyle) k aktualizaci stylu panelu stavového řádku.

Další informace o používání `CStatusBar`, najdete v článku [stav panelu implementace v prostředí MFC](../../mfc/status-bar-implementation-in-mfc.md) a [Technická poznámka 31: Ovládací pruhy](../../mfc/tn031-control-bars.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CControlBar](../../mfc/reference/ccontrolbar-class.md)

`CStatusBar`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxext.h

##  <a name="commandtoindex"></a>  CStatusBar::CommandToIndex

Získá index indikátor pro dané ID.

```
int CommandToIndex(UINT nIDFind) const;
```

### <a name="parameters"></a>Parametry

*nIDFind*<br/>
ID řetězce indikátoru, jejíž index se má být načtena.

### <a name="return-value"></a>Návratová hodnota

Index indikátoru v případě úspěchu; -1, pokud nebylo úspěšné.

### <a name="remarks"></a>Poznámky

Index první indikátor je 0.

##  <a name="create"></a>  CStatusBar::Create

Vytvoří stavového řádku (podřízené okno) a přidruží ji k `CStatusBar` objektu.

```
virtual BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_BOTTOM,
    UINT nID = AFX_IDW_STATUS_BAR);
```

### <a name="parameters"></a>Parametry

*pParentWnd*<br/>
Ukazatel [CWnd](../../mfc/reference/cwnd-class.md) objekt, jehož okno Windows je nadřazeného člena stavový řádek.

*dwStyle*<br/>
Styl stavového řádku. Kromě standardní Windows [styly](../../mfc/reference/styles-used-by-mfc.md#window-styles), tyto styly jsou podporovány.

- CBRS_TOP ovládací panel je v horní části okna rámce.

- CBRS_BOTTOM ovládací panel je v dolní části okna rámce.

- Při změně velikosti nadřazené není přemístí CBRS_NOALIGN ovládací panel.

*nID*<br/>
ID podřízené okno panelu nástrojů

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Také nastaví počáteční písmo a nastaví stav Výška pruhu na výchozí hodnotu.

##  <a name="createex"></a>  CStatusBar::CreateEx

Voláním této funkce vytváření stavového řádku (podřízené okno) a přidružte jej k `CStatusBar` objektu.

```
virtual BOOL CreateEx(
    CWnd* pParentWnd,
    DWORD dwCtrlStyle = 0,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_BOTTOM,
    UINT nID = AFX_IDW_STATUS_BAR);
```

### <a name="parameters"></a>Parametry

*pParentWnd*<br/>
Ukazatel [CWnd](../../mfc/reference/cwnd-class.md) objekt, jehož okno Windows je nadřazeného člena stavový řádek.

*dwCtrlStyle*<br/>
Další styly pro vytvoření vložený [CStatusBarCtrl](../../mfc/reference/cstatusbarctrl-class.md) objektu. Určuje výchozí stavový řádek bez úchyt pro změnu velikosti nebo popisek podporovat. Stav panelu Styly podporovány jsou:

- SBARS_SIZEGRIP ovládací prvek panelu stavu zahrnuje úchyt na pravém konci stavový řádek. Úchyt pro změnu velikosti je podobná velikosti ohraničení; je obdélníkovou oblast, která uživatel může klikněte a přetáhněte pro změnu velikosti nadřazeného okna.

- SBT_TOOLTIPS stavový řádek podporuje zobrazení popisů tlačítek.

Podrobnosti o těchto stylů, najdete v části [nastavení pro třídu CStatusBarCtrl](../../mfc/settings-for-the-cstatusbarctrl.md).

*dwStyle*<br/>
Styl stavového řádku. Výchozí hodnota určuje, že se v dolní části okna rámce vytvořen viditelný stavový řádek. Použít libovolnou kombinaci stavového řádku – styly ovládacích prvků, které jsou uvedeny v [styly oken](../../mfc/reference/styles-used-by-mfc.md#window-styles) a [CDialogBar::Create](../../mfc/reference/cdialogbar-class.md#create). Nicméně tento parametr by měla vždycky obsahovat WS_CHILD a WS_VISIBLE styly.

*nID*<br/>
ID podřízeného okna. stavový řádek.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Tato funkce také nastaví počáteční písmo a nastaví stav Výška pruhu na výchozí hodnotu.

Použití `CreateEx`, namísto [vytvořit](#create), při určitých stylů musí být k dispozici při vytváření ovládacích prvků panelu vložený stav. Například nastavte *dwCtrlStyle* k SBT_TOOLTIPS zobrazit popisy tlačítek v objektu panelu stavu.

##  <a name="cstatusbar"></a>  CStatusBar::CStatusBar

Vytvoří `CStatusBar` objekt, vytvoří výchozí písmo stavového řádku v případě potřeby a nastaví na výchozí hodnoty vlastnosti font.

```
CStatusBar();
```

##  <a name="drawitem"></a>  CStatusBar::DrawItem

Tato členská funkce se volá se rozhraním při úpravě vizuálního aspektu panelu vykreslovaných vlastníkem stav se změní.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Parametry

*lpDrawItemStruct*<br/>
Ukazatel [drawitemstruct –](/windows/desktop/api/winuser/ns-winuser-tagdrawitemstruct) strukturu, která obsahuje informace o typu kreslení vyžaduje.

### <a name="remarks"></a>Poznámky

`itemAction` Člena `DRAWITEMSTRUCT` struktury definuje výkresu akci, která se má provést. Přepsat tato členská funkce implementovat kreslení pro vykreslené vlastníkem `CStatusBar` objektu. Aplikace by měl obnovit všechny grafiky zařízení rozhraní GDI systému objekty vybrané pro zadaný kontext zobrazení v *lpDrawItemStruct* před ukončením tato členská funkce.

##  <a name="getitemid"></a>  CStatusBar::GetItemID

Vrátí ID indikátor určené *nIndex*.

```
UINT GetItemID(int nIndex) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index indikátor, jejichž ID se má být načtena.

### <a name="return-value"></a>Návratová hodnota

ID indikátor určené *nIndex*.

##  <a name="getitemrect"></a>  CStatusBar::GetItemRect

Zkopíruje souřadnic ukazatele určené *nIndex* do struktury, na které odkazuje *lprect –*.

```
void GetItemRect(
    int nIndex,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index ukazatel, jehož souřadnice obdélník se mají načíst.

*lpRect*<br/>
Odkazuje na [RECT](/previous-versions/dd162897\(v=vs.85\)) struktury nebo [crect –](../../atl-mfc-shared/reference/crect-class.md) objekt, který bude příjemcem souřadnic ukazatele určené *nIndex*.

### <a name="remarks"></a>Poznámky

Souřadnice jsou uváděny v pixelech vzhledem k levého horního rohu stavového řádku.

##  <a name="getpaneinfo"></a>  CStatusBar::GetPaneInfo

Nastaví *nID*, *nStyle*, a *cxWidth* ID, styl a šířka v podokně ukazatel v místě určeném *nIndex*.

```
void GetPaneInfo(
    int nIndex,
    UINT& nID,
    UINT& nStyle,
    int& cxWidth) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index v podokně, jehož informace má být načtena.

*nID*<br/>
Odkaz na UINT, která je nastavena na ID v podokně.

*nStyle*<br/>
Odkaz na UINT, který je nastaven styl panelu.

*cxWidth*<br/>
Odkaz na celé číslo, které je nastavena na šířku panelu.

##  <a name="getpanestyle"></a>  CStatusBar::GetPaneStyle

Voláním této členské funkce k načtení styl stavového řádku stavového řádku.

```
UINT GetPaneStyle(int nIndex) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index v podokně, jehož styl má být načtena.

### <a name="return-value"></a>Návratová hodnota

Styl panelu stavového řádku určené *nIndex*.

### <a name="remarks"></a>Poznámky

Do podokna styl určuje, jak se zobrazí v podokně.

Seznam styly, které jsou k dispozici pro stavové řádky najdete v tématu [vytvořit](#create).

##  <a name="getpanetext"></a>  CStatusBar::GetPaneText

Voláním této členské funkce k načtení textu, který se zobrazí panelu stavového řádku.

```
CString GetPaneText(int nIndex) const;  void GetPaneText(int nIndex, CString& rString) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index v podokně, jejichž text je se má načíst.

*rString*<br/>
Odkaz na [CString](../../atl-mfc-shared/reference/cstringt-class.md) objekt, který obsahuje text, který se má načíst.

### <a name="return-value"></a>Návratová hodnota

A `CString` objekt, který obsahuje text v podokně.

### <a name="remarks"></a>Poznámky

Tedy o druhou podobu této členské funkce výplně `CString` objekt s text řetězce.

##  <a name="getstatusbarctrl"></a>  CStatusBar::GetStatusBarCtrl

Tato členská funkce umožňuje přímý přístup k podkladové běžný ovládací prvek.

```
CStatusBarCtrl& GetStatusBarCtrl() const;
```

### <a name="return-value"></a>Návratová hodnota

Obsahuje odkaz na [CStatusBarCtrl](../../mfc/reference/cstatusbarctrl-class.md) objektu.

### <a name="remarks"></a>Poznámky

Použití `GetStatusBarCtrl` využít funkce Windows stavový řádek běžný ovládací prvek a chcete využít výhod podpory [CStatusBarCtrl](../../mfc/reference/cstatusbarctrl-class.md) poskytuje pro přizpůsobení na stavovém řádku. Například pomocí běžný ovládací prvek můžete zadat styl, který obsahuje úchyt pro změnu velikosti ve stavovém řádku nebo můžete určit styl mít stavový řádek zobrazí v horní části klientské oblasti okna nadřazené.

Další obecné informace o běžných ovládacích prvků naleznete v tématu [běžné ovládací prvky](/windows/desktop/Controls/common-controls-intro) v sadě Windows SDK.

##  <a name="setindicators"></a>  CStatusBar::SetIndicators

Nastaví ID každé ukazatel na hodnotu zadanou pomocí odpovídající prvek pole *lpIDArray*, načte řetězec prostředku zadaného parametrem každé ID a nastaví text ukazatele na řetězec.

```
BOOL SetIndicators(
    const UINT* lpIDArray,
    int nIDCount);
```

### <a name="parameters"></a>Parametry

*lpIDArray*<br/>
Ukazatel na pole ID.

*nIDCount*<br/>
Počet prvků v poli odkazované *lpIDArray*.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

##  <a name="setpaneinfo"></a>  CStatusBar::SetPaneInfo

Nastaví podokno zadaný ukazatel na nové ID, styl a šířku.

```
void SetPaneInfo(
    int nIndex,
    UINT nID,
    UINT nStyle,
    int cxWidth);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index v podokně ukazatel, jehož styl, je možné nastavit.

*nID*<br/>
Nové ID pro podokno indikátoru.

*nStyle*<br/>
Nový styl indikátoru podokna.

*cxWidth*<br/>
Novou šířku pro podokno indikátoru.

### <a name="remarks"></a>Poznámky

Podporují se tyto styly indikátoru:

- Bez SBPS_NOBORDERS 3D ohraničení okolo panelu.

- SBPS_POPOUT Reverse ohraničení, která se tak, aby text "vyskočí."

- Proveďte SBPS_DISABLED není kreslení textu.

- Podokno SBPS_STRETCH roztáhnout tak, aby vyplnil nevyužité místo. Tento styl může mít jenom jedno podokno na stavovém řádku.

- Ne SBPS_NORMAL roztáhnout, ohraničení nebo rozbalení.

##  <a name="setpanestyle"></a>  CStatusBar::SetPaneStyle

Voláním této členské funkce, chcete-li nastavit styl stavového řádku stavového řádku.

```
void SetPaneStyle(
    int nIndex,
    UINT nStyle);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index v podokně, jehož styl, je možné nastavit.

*nStyle*<br/>
Styl stavového, jehož styl, je možné nastavit.

### <a name="remarks"></a>Poznámky

Do podokna styl určuje, jak se zobrazí v podokně.

Seznam styly, které jsou k dispozici pro stavové řádky najdete v tématu [SetPaneInfo](#setpaneinfo).

##  <a name="setpanetext"></a>  CStatusBar::SetPaneText

Voláním této členské funkce se nastavit text podokna na řetězec, který ukazuje *lpszNewText*.

```
BOOL SetPaneText(
    int nIndex,
    LPCTSTR lpszNewText,
    BOOL bUpdate = TRUE);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index v podokně, jejichž text je nastavit.

*lpszNewText*<br/>
Ukazatel na nové podokno textu.

*bUpdate*<br/>
Při hodnotě TRUE se v podokně zneplatněna po nastavení text.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Po zavolání `SetPaneText`, je nutné přidat obslužnou rutinu aktualizace uživatelského rozhraní pro zobrazení nového textu ve stavovém řádku.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#176](../../mfc/codesnippet/cpp/cstatusbar-class_1.cpp)]

[!code-cpp[NVC_MFCDocView#177](../../mfc/codesnippet/cpp/cstatusbar-class_2.cpp)]

[!code-cpp[NVC_MFCDocView#178](../../mfc/codesnippet/cpp/cstatusbar-class_3.cpp)]

## <a name="see-also"></a>Viz také:

[Ukázky knihovny MFC CTRLBARS](../../visual-cpp-samples.md)<br/>
[Ukázka DLGCBR32 knihovny MFC](../../visual-cpp-samples.md)<br/>
[CControlBar – třída](../../mfc/reference/ccontrolbar-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CStatusBarCtrl – třída](../../mfc/reference/cstatusbarctrl-class.md)<br/>
[CControlBar – třída](../../mfc/reference/ccontrolbar-class.md)
