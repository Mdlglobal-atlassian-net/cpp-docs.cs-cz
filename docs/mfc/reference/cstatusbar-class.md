---
title: CStatusBar – třída
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
ms.openlocfilehash: 0549ee10faa15b80b18a0bee2f115425002e1479
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376251"
---
# <a name="cstatusbar-class"></a>CStatusBar – třída

Ovládací panel s řadou podoken výstupu textu nebo indikátory.

## <a name="syntax"></a>Syntaxe

```
class CStatusBar : public CControlBar
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CStavový řádek::Stavový řádek](#cstatusbar)|Vytvoří `CStatusBar` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CStavový řádek::Příkaz](#commandtoindex)|Získá index pro dané ID indikátoru.|
|[CStavový řádek::Vytvořit](#create)|Vytvoří stavový řádek, připojí `CStatusBar` jej k objektu a nastaví počáteční písmo a výšku pruhu.|
|[CStavový pruh::CreateEx](#createex)|Vytvoří `CStatusBar` objekt s dalšími styly pro vložený `CStatusBarCtrl` objekt.|
|[CStatusBar::DrawItem](#drawitem)|Nazývá se při změně vizuální aspekt ovládacího prvku stavového řádku kreslení vlastníka.|
|[CStavový řádek::GetItemID](#getitemid)|Získá ID indikátoru pro daný index.|
|[CStatusBar::GetItemRect](#getitemrect)|Získá obdélník zobrazení pro daný index.|
|[CStatusBar::GetpaneInfo](#getpaneinfo)|Získá ID indikátoru, styl a šířku pro daný index.|
|[CStavový řádek::GetpaneStyle](#getpanestyle)|Získá styl indikátoru pro daný index.|
|[CStavový řádek::GetpaneText](#getpanetext)|Získá text indikátoru pro daný index.|
|[CStavový řádek::GetStatusBarCtrl](#getstatusbarctrl)|Umožňuje přímý přístup k základní společný ovládací prvek.|
|[CStavový řádek::SetIndicators](#setindicators)|Nastaví ID indikátorů.|
|[CStavový řádek::SetpaneInfo](#setpaneinfo)|Nastaví ID indikátoru, styl a šířku pro daný index.|
|[CStavový řádek::SetpaneStyle](#setpanestyle)|Nastaví styl ukazatele pro daný index.|
|[CStavový řádek::Setpanetext](#setpanetext)|Nastaví text indikátoru pro daný index.|

## <a name="remarks"></a>Poznámky

Výstupní podokna se běžně používají jako řádky zpráv a jako indikátory stavu. Mezi příklady patří řádky nápovědy nabídky, které stručně vysvětlují vybraný příkaz nabídky a indikátory, které zobrazují stav kláves SCROLL LOCK, NUM LOCK a dalších kláves.

[CStatusBar::GetStatusBarCtrl](#getstatusbarctrl), členská funkce nová pro knihovnu MFC 4.0, umožňuje využít podporu společného ovládacího prvku systému Windows pro přizpůsobení stavového řádku a další funkce. `CStatusBar`členské funkce poskytují většinu funkcí běžných ovládacích prvků systému Windows; Při volání `GetStatusBarCtrl`však můžete stavové panely ještě více z vlastností stavového řádku systému Windows 95/98. Při volání `GetStatusBarCtrl`vrátí odkaz na `CStatusBarCtrl` objekt. Další informace o návrhu panelů nástrojů pomocí běžných ovládacích prvků systému Windows naleznete v tématu [CStatusBarCtrl.](../../mfc/reference/cstatusbarctrl-class.md) Obecnější informace o běžných ovládacích prvcích naleznete v [tématu Common Controls](/windows/win32/Controls/common-controls-intro) in the Windows SDK.

Rozhraní Framework ukládá informace o indikátoru v poli s indikátorem nejvíce vlevo na pozici 0. Při vytváření stavového řádku použijete pole ID řetězců, které rozhraní framework přidružuje k odpovídajícím ukazatelům. Potom můžete použít buď ID řetězce nebo index pro přístup k indikátoru.

Ve výchozím nastavení je první indikátor "elastický": zabírá délku stavového řádku, kterou ostatní podokna indikátorů nepoužívají, takže ostatní podokna jsou zarovnána doprava.

Stavový řádek vytvoříte takto:

1. Vytvořte `CStatusBar` objekt.

1. Volání [vytvořit](#create) (nebo [CreateEx](#createex)) funkce vytvořit okno stavového `CStatusBar` řádku a připojit k objektu.

1. Volání [SetIndicators](#setindicators) přidružit ID řetězce s každým indikátorem.

Text v podokně stavového řádku lze aktualizovat třemi způsoby:

1. Volání [CWnd::SetWindowText](../../mfc/reference/cwnd-class.md#setwindowtext) aktualizovat text v podokně 0 pouze.

1. Volání [CCmdUI::SetText](../../mfc/reference/ccmdui-class.md#settext) v obslužné rutině ON_UPDATE_COMMAND_UI stavového řádku.

1. Volání [MAPaneText](#setpanetext) aktualizovat text pro libovolné podokno.

Volání [MAVAStyle](#setpanestyle) aktualizovat styl podokna stavového řádku.

Další informace o `CStatusBar`použití naleznete v článku [Implementace stavového řádku v knihovně MFC](../../mfc/status-bar-implementation-in-mfc.md) a [technická poznámka 31 : Ovládací panely](../../mfc/tn031-control-bars.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Ovládací panel CControl](../../mfc/reference/ccontrolbar-class.md)

`CStatusBar`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxext.h

## <a name="cstatusbarcommandtoindex"></a><a name="commandtoindex"></a>CStavový řádek::Příkaz

Získá index indikátoru pro dané ID.

```
int CommandToIndex(UINT nIDFind) const;
```

### <a name="parameters"></a>Parametry

*nIDNajít*<br/>
ID řetězce indikátoru, jehož index má být načten.

### <a name="return-value"></a>Návratová hodnota

Index indikátoru v případě úspěchu; -1, pokud není úspěšný.

### <a name="remarks"></a>Poznámky

Index prvního indikátoru je 0.

## <a name="cstatusbarcreate"></a><a name="create"></a>CStavový řádek::Vytvořit

Vytvoří stavový řádek (podřízené okno) a `CStatusBar` přidruží jej k objektu.

```
virtual BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_BOTTOM,
    UINT nID = AFX_IDW_STATUS_BAR);
```

### <a name="parameters"></a>Parametry

*pParentWnd*<br/>
Ukazatel na [cwnd](../../mfc/reference/cwnd-class.md) objekt, jehož okno systému Windows je nadřazený stavový řádek.

*dwStyl*<br/>
Styl stavového řádku. Kromě standardních [stylů](../../mfc/reference/styles-used-by-mfc.md#window-styles)systému Windows jsou tyto styly podporovány.

- CBRS_TOP Ovládací panel je v horní části okna rámce.

- CBRS_BOTTOM Ovládací panel je v dolní části okna rámce.

- CBRS_NOALIGN Ovládací panel není přemístěn, když je velikost nadřazené velikosti.

*Nid*<br/>
ID podřízeného okna panelu nástrojů.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Také nastaví počáteční písmo a výšku stavového řádku na výchozí hodnotu.

## <a name="cstatusbarcreateex"></a><a name="createex"></a>CStavový pruh::CreateEx

Volání této funkce k vytvoření stavového řádku (podřízené `CStatusBar` okno) a přidružit k objektu.

```
virtual BOOL CreateEx(
    CWnd* pParentWnd,
    DWORD dwCtrlStyle = 0,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_BOTTOM,
    UINT nID = AFX_IDW_STATUS_BAR);
```

### <a name="parameters"></a>Parametry

*pParentWnd*<br/>
Ukazatel na [cwnd](../../mfc/reference/cwnd-class.md) objekt, jehož okno systému Windows je nadřazený stavový řádek.

*dwCtrlStyl*<br/>
Další styly pro vytvoření vloženého objektu [CStatusBarCtrl.](../../mfc/reference/cstatusbarctrl-class.md) Výchozí nastavení určuje stavový řádek bez uzlu pro změnu velikosti nebo podpory popisů. Podporované styly stavového řádku jsou:

- SBARS_SIZEGRIP Ovládací prvek Stavový řádek obsahuje uzel pro změnu velikosti na pravém konci stavového řádku. Uzel velikosti je podobný ohraničení velikosti; jedná se o obdélníkovou oblast, na kterou může uživatel klepnout a přetáhnout a změnit velikost nadřazeného okna.

- SBT_TOOLTIPS Stavový řádek podporuje popisky.

Podrobnosti o těchto stylech naleznete v [tématu Nastavení klávesCStatusBarCtrl](../../mfc/settings-for-the-cstatusbarctrl.md).

*dwStyl*<br/>
Styl stavového řádku. Výchozí hodnota určuje, že v dolní části okna rámce bude vytvořen viditelný stavový řádek. Použijte libovolnou kombinaci stylů ovládacích prvků stavového řádku uvedených v [okně Styly](../../mfc/reference/styles-used-by-mfc.md#window-styles) a [CDialogBar::Vytvořit](../../mfc/reference/cdialogbar-class.md#create). Tento parametr by však měl vždy obsahovat WS_CHILD a WS_VISIBLE styly.

*Nid*<br/>
ID podřízeného okna stavového řádku.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Tato funkce také nastaví počáteční písmo a výšku stavového řádku na výchozí hodnotu.

Místo `CreateEx`funkce [Vytvořit](#create)použijte , pokud při vytváření vloženého ovládacího prvku stavového řádku musí být přítomny určité styly. Například nastavte *dwCtrlStyle* tak, aby SBT_TOOLTIPS zobrazení popisků v objektu stavového řádku.

## <a name="cstatusbarcstatusbar"></a><a name="cstatusbar"></a>CStavový řádek::Stavový řádek

Vytvoří `CStatusBar` objekt, v případě potřeby vytvoří výchozí písmo stavového řádku a nastaví vlastnosti písma na výchozí hodnoty.

```
CStatusBar();
```

## <a name="cstatusbardrawitem"></a><a name="drawitem"></a>CStatusBar::DrawItem

Tato členská funkce je volána rámci při vizuální aspekt nakreslený vlastník stavový řádek změny.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Parametry

*lpDrawItemStruct*<br/>
Ukazatel na strukturu [DRAWITEMSTRUCT,](/windows/win32/api/winuser/ns-winuser-drawitemstruct) která obsahuje informace o požadovaném typu výkresu.

### <a name="remarks"></a>Poznámky

Člen `itemAction` `DRAWITEMSTRUCT` struktury definuje kreslicí akci, která má být provedena. Přepsat tuto členovou funkci implementovat výkres `CStatusBar` pro objekt nakreslení vlastníka. Aplikace by měla obnovit všechny objekty rozhraní grafického zařízení (GDI) vybrané pro kontext zobrazení dodaný v *lpDrawItemStruct* před ukončením této členské funkce.

## <a name="cstatusbargetitemid"></a><a name="getitemid"></a>CStavový řádek::GetItemID

Vrátí ID indikátoru určeného *nIndex*.

```
UINT GetItemID(int nIndex) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index indikátoru, jehož ID má být načten.

### <a name="return-value"></a>Návratová hodnota

ID indikátoru určeného *nIndex*.

## <a name="cstatusbargetitemrect"></a><a name="getitemrect"></a>CStatusBar::GetItemRect

Zkopíruje souřadnice indikátoru určeného *nIndex* do struktury, na kterou poukazuje *lpRect*.

```
void GetItemRect(
    int nIndex,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index indikátoru, jehož obdélníkové souřadnice mají být načteny.

*lpRect*<br/>
Odkazuje na [rect](/previous-versions/dd162897\(v=vs.85\)) strukturu nebo [CRect](../../atl-mfc-shared/reference/crect-class.md) objekt, který obdrží souřadnice indikátoru *určeného nIndex*.

### <a name="remarks"></a>Poznámky

Souřadnice jsou v obrazových bodech vzhledem k levému hornímu rohu stavového řádku.

## <a name="cstatusbargetpaneinfo"></a><a name="getpaneinfo"></a>CStatusBar::GetpaneInfo

Nastaví *nID*, *nStyle*a *cxWidth* na ID, styl a šířku podokna indikátoru v umístění určeném *nIndex*.

```
void GetPaneInfo(
    int nIndex,
    UINT& nID,
    UINT& nStyle,
    int& cxWidth) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index podokna, jehož informace mají být načteny.

*Nid*<br/>
Odkaz na UINT, který je nastaven na ID podokna.

*nStyl*<br/>
Odkaz na UINT, který je nastaven na styl podokna.

*cxWidth*<br/>
Odkaz na celé číslo, které je nastaveno na šířku podokna.

## <a name="cstatusbargetpanestyle"></a><a name="getpanestyle"></a>CStavový řádek::GetpaneStyle

Volání této členské funkce načíst styl podokna stavového řádku.

```
UINT GetPaneStyle(int nIndex) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index podokna, jehož styl má být načten.

### <a name="return-value"></a>Návratová hodnota

Styl podokna stavového řádku určený *nIndex*.

### <a name="remarks"></a>Poznámky

Styl podokna určuje, jak se podokno zobrazí.

Seznam stylů dostupných pro stavové panely naleznete v tématu [Vytvoření](#create).

## <a name="cstatusbargetpanetext"></a><a name="getpanetext"></a>CStavový řádek::GetpaneText

Volánítéto členské funkce načíst text, který se zobrazí v podokně stavového řádku.

```
CString GetPaneText(int nIndex) const;  void GetPaneText(int nIndex, CString& rString) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index podokna, jehož text má být načten.

*rString*<br/>
Odkaz na [CString](../../atl-mfc-shared/reference/cstringt-class.md) objekt, který obsahuje text, který má být načten.

### <a name="return-value"></a>Návratová hodnota

Objekt `CString` obsahující text podokna.

### <a name="remarks"></a>Poznámky

Druhý formulář této členské funkce `CString` vyplní objekt textem řetězce.

## <a name="cstatusbargetstatusbarctrl"></a><a name="getstatusbarctrl"></a>CStavový řádek::GetStatusBarCtrl

Tato členská funkce umožňuje přímý přístup k základní společný ovládací prvek.

```
CStatusBarCtrl& GetStatusBarCtrl() const;
```

### <a name="return-value"></a>Návratová hodnota

Obsahuje odkaz na objekt [CStatusBarCtrl.](../../mfc/reference/cstatusbarctrl-class.md)

### <a name="remarks"></a>Poznámky

Slouží `GetStatusBarCtrl` k využití funkcí společného ovládacího prvku stavového řádku systému Windows a k využití podpory, kterou [cstatusbarctrl](../../mfc/reference/cstatusbarctrl-class.md) poskytuje pro přizpůsobení stavového řádku. Například pomocí společného ovládacího prvku můžete určit styl, který obsahuje uzel pro změnu velikosti na stavovém řádku, nebo můžete určit styl, aby se stavový řádek zobrazil v horní části klientské oblasti nadřazeného okna.

Obecnější informace o běžných ovládacích prvcích naleznete v [tématu Běžné ovládací prvky](/windows/win32/Controls/common-controls-intro) v sadě Windows SDK.

## <a name="cstatusbarsetindicators"></a><a name="setindicators"></a>CStavový řádek::SetIndicators

Nastaví ID každého indikátoru na hodnotu určenou odpovídajícím prvkem pole *lpIDArray*, načte prostředek řetězce určený každým ID a nastaví text indikátoru na řetězec.

```
BOOL SetIndicators(
    const UINT* lpIDArray,
    int nIDCount);
```

### <a name="parameters"></a>Parametry

*pole lpIDArray*<br/>
Ukazatel na pole ID.

*nIDCount*<br/>
Počet prvků v poli, na které se vztahuje *lpIDArray*.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

## <a name="cstatusbarsetpaneinfo"></a><a name="setpaneinfo"></a>CStavový řádek::SetpaneInfo

Nastaví zadané podokno indikátoru na nové ID, styl a šířku.

```
void SetPaneInfo(
    int nIndex,
    UINT nID,
    UINT nStyle,
    int cxWidth);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index podokna indikátorů, jehož styl má být nastaven.

*Nid*<br/>
Nové ID podokna indikátorů.

*nStyl*<br/>
Nový styl pro podokno indikátorů.

*cxWidth*<br/>
Nová šířka podokna indikátoru.

### <a name="remarks"></a>Poznámky

Podporovány jsou následující styly indikátorů:

- SBPS_NOBORDERS kolem tabule č. 3D ohraničení.

- SBPS_POPOUT Obrácené ohraničení tak, aby text "vyskočí.".

- SBPS_DISABLED Nekreslit text.

- SBPS_STRETCH podokně Roztáhnout, chcete-li vyplnit nevyužité místo. Tento styl může mít pouze jedno podokno na stavový řádek.

- SBPS_NORMAL Žádné protažení, ohraničení nebo vyskakovací okno.

## <a name="cstatusbarsetpanestyle"></a><a name="setpanestyle"></a>CStavový řádek::SetpaneStyle

Voláním této členské funkce nastavte styl podokna stavového řádku.

```
void SetPaneStyle(
    int nIndex,
    UINT nStyle);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index podokna, jehož styl má být nastaven.

*nStyl*<br/>
Styl podokna, jehož styl má být nastaven.

### <a name="remarks"></a>Poznámky

Styl podokna určuje, jak se podokno zobrazí.

Seznam stylů dostupných pro stavové panely naleznete v tématu [SetPaneInfo](#setpaneinfo).

## <a name="cstatusbarsetpanetext"></a><a name="setpanetext"></a>CStavový řádek::Setpanetext

Voláním této členské funkce nastavte text podokna na řetězec, na který je odkazován *lpszNewText*.

```
BOOL SetPaneText(
    int nIndex,
    LPCTSTR lpszNewText,
    BOOL bUpdate = TRUE);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index podokna, jehož text má být nastaven.

*lpszNewText*<br/>
Ukazatel na nový text podokna.

*bAktualizovat*<br/>
Pokud true, podokno je zrušena po nastavení textu.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Po volání `SetPaneText`je nutné přidat obslužnou rutinu aktualizace ui, aby se nový text zobrazil na stavovém řádku.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#176](../../mfc/codesnippet/cpp/cstatusbar-class_1.cpp)]

[!code-cpp[NVC_MFCDocView#177](../../mfc/codesnippet/cpp/cstatusbar-class_2.cpp)]

[!code-cpp[NVC_MFCDocView#178](../../mfc/codesnippet/cpp/cstatusbar-class_3.cpp)]

## <a name="see-also"></a>Viz také

[Ukázka knihovny MFC CTRLBARS](../../overview/visual-cpp-samples.md)<br/>
[Ukázka knihovny MFC DLGCBR32](../../overview/visual-cpp-samples.md)<br/>
[CControlBar – třída](../../mfc/reference/ccontrolbar-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třída CStatusBarCtrl](../../mfc/reference/cstatusbarctrl-class.md)<br/>
[CControlBar – třída](../../mfc/reference/ccontrolbar-class.md)
