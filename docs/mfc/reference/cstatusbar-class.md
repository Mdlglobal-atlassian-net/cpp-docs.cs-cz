---
title: CStatusBar – – třída
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
ms.openlocfilehash: 48de31d95814ce5fc1fb015e69cf38d73337cb79
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502336"
---
# <a name="cstatusbar-class"></a>CStatusBar – – třída

Ovládací panel s řádkem podoken textových výstupů nebo "Indikátory".

## <a name="syntax"></a>Syntaxe

```
class CStatusBar : public CControlBar
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CStatusBar::CStatusBar](#cstatusbar)|`CStatusBar` Vytvoří objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CStatusBar::CommandToIndex](#commandtoindex)|Získá index pro dané ID ukazatele.|
|[CStatusBar –:: Create](#create)|Vytvoří stavový řádek, připojí ho k `CStatusBar` objektu a nastaví počáteční písmo a výšku pruhu.|
|[CStatusBar –:: CreateEx](#createex)|Vytvoří objekt s dalšími styly pro vložený `CStatusBarCtrl` objekt. `CStatusBar`|
|[CStatusBar –::D rawItem](#drawitem)|Volá se, když se změní vizuální aspekt ovládacího prvku pro vykreslení stavového řádku.|
|[CStatusBar::GetItemID](#getitemid)|Získá ID indikátoru pro daný index.|
|[CStatusBar –:: GetItemRect](#getitemrect)|Získá zobrazený obdélník pro daný index.|
|[CStatusBar::GetPaneInfo](#getpaneinfo)|Získá ID, styl a šířku indikátoru pro daný index.|
|[CStatusBar::GetPaneStyle](#getpanestyle)|Získá styl indikátoru pro daný index.|
|[CStatusBar::GetPaneText](#getpanetext)|Získá text indikátoru pro daný index.|
|[CStatusBar::GetStatusBarCtrl](#getstatusbarctrl)|Umožňuje přímý přístup k základnímu běžnému ovládacímu prvku.|
|[CStatusBar –:: SetIndicators](#setindicators)|Nastaví ID indikátorů.|
|[CStatusBar::SetPaneInfo](#setpaneinfo)|Nastaví ID, styl a šířku indikátoru pro daný index.|
|[CStatusBar::SetPaneStyle](#setpanestyle)|Nastaví styl indikátoru pro daný index.|
|[CStatusBar::SetPaneText](#setpanetext)|Nastaví text indikátoru pro daný index.|

## <a name="remarks"></a>Poznámky

Výstupní podokna se běžně používají jako řádky zpráv a indikátory stavu. Příkladem může být nabídka nabídky – řádky s zprávami, které stručně vysvětlují vybraný příkaz nabídky, a indikátory, které zobrazují stav zámku SCROLL LOCK, NUM LOCK a další klíče.

[CStatusBar –:: GetStatusBarCtrl](#getstatusbarctrl), členská funkce, která je novinkou pro MFC 4,0, vám umožní využít podporu obecného ovládacího prvku Windows pro přizpůsobení stavového řádku a další funkce. `CStatusBar`Členské funkce poskytují většinu funkcí běžných ovládacích prvků Windows. Když však zavoláte `GetStatusBarCtrl`, můžete svým stavovým pruhům poskytnout ještě více vlastností stavového řádku Windows 95/98. Při volání `GetStatusBarCtrl`vrátí odkaz `CStatusBarCtrl` na objekt. Další informace o navrhování panelů nástrojů pomocí běžných ovládacích prvků Windows najdete v tématu [CStatusBarCtrl](../../mfc/reference/cstatusbarctrl-class.md) . Obecnější informace o běžných ovládacích prvcích najdete v tématu [běžné ovládací prvky](/windows/win32/Controls/common-controls-intro) v Windows SDK.

Rozhraní ukládá informace o ukazateli v poli se indikátorem úplně vlevo na pozici 0. Při vytváření stavového řádku použijete pole ID řetězců, které rozhraní přidruží k odpovídajícím indikátorům. Pro přístup k ukazateli pak můžete použít buď ID řetězce, nebo index.

Ve výchozím nastavení je první ukazatel "elastický": zabírá délku stavového řádku, kterou nepoužívají ostatní podokna indikátorů, takže ostatní podokna jsou zarovnána vpravo.

Stavový řádek vytvoříte pomocí následujících kroků:

1. Sestavte `CStatusBar` objekt.

1. Voláním funkce [Create](#create) (nebo [CreateEx](#createex)) vytvořte okno stavového řádku a připojte `CStatusBar` ho k objektu.

1. Zavolejte [SetIndicators](#setindicators) a přidružte ID řetězce k jednotlivým ukazatelům.

Existují tři způsoby, jak text aktualizovat v podokně stavového řádku:

1. Chcete-li aktualizovat text pouze v podokně 0, zavolejte na hodnotu [CWnd:: SetWindowText](../../mfc/reference/cwnd-class.md#setwindowtext) .

1. V obslužné rutině ON_UPDATE_COMMAND_UI stavového řádku volejte [CCmdUI –:: SetText](../../mfc/reference/ccmdui-class.md#settext) .

1. Zavolejte [SetPaneText](#setpanetext) a aktualizujte text pro jakékoli podokno.

Zavolejte [SetPaneStyle](#setpanestyle) a aktualizujte styl podokna stavového řádku.

Další informace o použití `CStatusBar`naleznete v článku [Implementace stavového řádku v knihovně MFC](../../mfc/status-bar-implementation-in-mfc.md) a [technická Poznámka 31: Ovládací panely](../../mfc/tn031-control-bars.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CControlBar](../../mfc/reference/ccontrolbar-class.md)

`CStatusBar`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxext. h

##  <a name="commandtoindex"></a>CStatusBar –:: CommandToIndex

Získá index indikátoru pro daný identifikátor.

```
int CommandToIndex(UINT nIDFind) const;
```

### <a name="parameters"></a>Parametry

*nIDFind*<br/>
ID řetězce indikátoru, jehož index má být načten.

### <a name="return-value"></a>Návratová hodnota

Index indikátoru, pokud je úspěšný; -1, pokud neproběhlo úspěšně.

### <a name="remarks"></a>Poznámky

Index prvního indikátoru je 0.

##  <a name="create"></a>CStatusBar –:: Create

Vytvoří stavový řádek (podřízené okno) a přidruží ho k `CStatusBar` objektu.

```
virtual BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_BOTTOM,
    UINT nID = AFX_IDW_STATUS_BAR);
```

### <a name="parameters"></a>Parametry

*pParentWnd*<br/>
Ukazatel na objekt [CWnd](../../mfc/reference/cwnd-class.md) , jehož okno systému Windows je nadřazeným prvkem stavového řádku.

*dwStyle*<br/>
Styl na stavovém řádku. Kromě standardních [stylů](../../mfc/reference/styles-used-by-mfc.md#window-styles)Windows jsou tyto styly podporovány.

- Ovládací panel CBRS_TOP je v horní části okna rámce.

- Ovládací panel CBRS_BOTTOM je v dolní části okna rámce.

- Ovládací panel CBRS_NOALIGN není přemístění při změně velikosti nadřazeného objektu.

*nID*<br/>
ID podřízeného okna panelu nástrojů

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Také nastaví počáteční písmo a nastaví výšku stavového řádku na výchozí hodnotu.

##  <a name="createex"></a>CStatusBar –:: CreateEx

Voláním této funkce vytvoříte stavový řádek (podřízené okno) a přidružíte ho `CStatusBar` k objektu.

```
virtual BOOL CreateEx(
    CWnd* pParentWnd,
    DWORD dwCtrlStyle = 0,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_BOTTOM,
    UINT nID = AFX_IDW_STATUS_BAR);
```

### <a name="parameters"></a>Parametry

*pParentWnd*<br/>
Ukazatel na objekt [CWnd](../../mfc/reference/cwnd-class.md) , jehož okno systému Windows je nadřazeným prvkem stavového řádku.

*dwCtrlStyle*<br/>
Další styly pro vytvoření vloženého objektu [CStatusBarCtrl](../../mfc/reference/cstatusbarctrl-class.md) Výchozí nastavení určuje stavový řádek bez podpory změny velikosti nebo popisu tlačítka. Podporované styly stavového řádku:

- SBARS_SIZEGRIP ovládací prvek stavového řádku obsahuje úchyt pro změnu velikosti na pravé straně stavového řádku. Úchyt pro změnu velikosti je podobný hranici velikosti; Jedná se o obdélníkovou oblast, kterou uživatel může kliknutím a přetažením změnit velikost nadřazeného okna.

- SBT_TOOLTIPS stavový řádek podporuje popisy tlačítek.

Podrobnosti o těchto stylech najdete v tématu [nastavení pro CStatusBarCtrl](../../mfc/settings-for-the-cstatusbarctrl.md).

*dwStyle*<br/>
Styl stavového řádku Výchozí určuje, že se v dolní části okna rámce vytvoří viditelný stavový řádek. Použít libovolnou kombinaci stylů ovládacích prvků stavového řádku uvedených v [oknech styly](../../mfc/reference/styles-used-by-mfc.md#window-styles) a [CDialogBar:: Create](../../mfc/reference/cdialogbar-class.md#create). Tento parametr by však měl vždy obsahovat styly WS_CHILD a WS_VISIBLE.

*nID*<br/>
ID podřízeného okna stavového řádku

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Tato funkce také nastaví počáteční písmo a nastaví výšku stavového řádku na výchozí hodnotu.

Použijte `CreateEx`místo [Create](#create), pokud je potřeba při vytváření vloženého ovládacího prvku stavového řádku zobrazit určité styly. Například nastavením *dwCtrlStyle* na SBT_TOOLTIPS zobrazíte popisy v objektu stavového řádku.

##  <a name="cstatusbar"></a>CStatusBar –:: CStatusBar –

`CStatusBar` Vytvoří objekt, v případě potřeby vytvoří výchozí písmo na stavovém řádku a nastaví vlastnosti písma na výchozí hodnoty.

```
CStatusBar();
```

##  <a name="drawitem"></a>CStatusBar –::D rawItem

Tato členská funkce je volána rozhraním, když se změní vizuální aspekt stavového řádku, který byl vykreslen jako vlastník.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Parametry

*lpDrawItemStruct*<br/>
Ukazatel na strukturu [DRAWITEMSTRUCT –](/windows/win32/api/winuser/ns-winuser-drawitemstruct) , která obsahuje informace o požadovaném typu výkresu.

### <a name="remarks"></a>Poznámky

`itemAction` Člen`DRAWITEMSTRUCT` struktury definuje akci kreslení, která má být provedena. Přepište tuto členskou funkci pro implementaci vykreslování pro objekt vykreslený `CStatusBar` vlastníkem. Aplikace by měla obnovit všechny objekty GDI (Graphics Device Interface) vybrané pro kontext zobrazení zadaný v *lpDrawItemStruct* před ukončením této členské funkce.

##  <a name="getitemid"></a>CStatusBar –:: getitemid

Vrátí ID indikátoru určeného parametrem *nIndex*.

```
UINT GetItemID(int nIndex) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index indikátoru, jehož ID má být načteno.

### <a name="return-value"></a>Návratová hodnota

ID indikátoru určeného parametrem *nIndex*

##  <a name="getitemrect"></a>CStatusBar –:: GetItemRect

Zkopíruje souřadnice indikátoru určeného parametrem *nIndex* do struktury, na kterou ukazuje *lpRect*.

```
void GetItemRect(
    int nIndex,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index indikátoru, jehož souřadnice obdélníku mají být načteny.

*lpRect*<br/>
Odkazuje na strukturu [Rect](/previous-versions/dd162897\(v=vs.85\)) nebo objekt [CRect](../../atl-mfc-shared/reference/crect-class.md) , který získá souřadnice indikátoru určeného parametrem *nIndex*.

### <a name="remarks"></a>Poznámky

Souřadnice jsou v pixelech vzhledem k levému hornímu rohu stavového řádku.

##  <a name="getpaneinfo"></a>CStatusBar –:: GetPaneInfo

Nastaví *NID*, *nStyle*a *cxWidth* na ID, styl a šířku podokna indikátoru v umístění určeném parametrem *nIndex*.

```
void GetPaneInfo(
    int nIndex,
    UINT& nID,
    UINT& nStyle,
    int& cxWidth) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index podokna, jejichž informace mají být načteny.

*nID*<br/>
Odkaz na objekt UINT, který je nastaven na ID podokna.

*nStyle*<br/>
Odkaz na objekt UINT, který je nastaven na styl podokna.

*cxWidth*<br/>
Odkaz na celé číslo, které je nastaveno na šířku podokna.

##  <a name="getpanestyle"></a>CStatusBar –:: GetPaneStyle

Voláním této členské funkce načtěte styl podokna stavového řádku.

```
UINT GetPaneStyle(int nIndex) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index podokna, jehož styl má být načten.

### <a name="return-value"></a>Návratová hodnota

Styl podokna stavového řádku zadaného parametrem *nIndex*

### <a name="remarks"></a>Poznámky

Styl podokna určuje, jak se podokno zobrazuje.

Seznam stylů dostupných pro stavové řádky naleznete v tématu [Create](#create).

##  <a name="getpanetext"></a>CStatusBar –:: GetPaneText

Zavolejte tuto členskou funkci pro načtení textu, který se zobrazí v podokně stavového řádku.

```
CString GetPaneText(int nIndex) const;  void GetPaneText(int nIndex, CString& rString) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index podokna, jehož text má být načten.

*rString*<br/>
Odkaz na objekt [CString](../../atl-mfc-shared/reference/cstringt-class.md) , který obsahuje text, který má být načten.

### <a name="return-value"></a>Návratová hodnota

`CString` Objekt obsahující text podokna.

### <a name="remarks"></a>Poznámky

Druhá forma této členské funkce vyplní `CString` objekt textem řetězce.

##  <a name="getstatusbarctrl"></a>CStatusBar –:: GetStatusBarCtrl

Tato členská funkce umožňuje přímý přístup k základnímu běžnému ovládacímu prvku.

```
CStatusBarCtrl& GetStatusBarCtrl() const;
```

### <a name="return-value"></a>Návratová hodnota

Obsahuje odkaz na objekt [CStatusBarCtrl](../../mfc/reference/cstatusbarctrl-class.md) .

### <a name="remarks"></a>Poznámky

Použijte `GetStatusBarCtrl` k využití funkcí společného ovládacího prvku stavového řádku systému Windows a k využití [CStatusBarCtrl](../../mfc/reference/cstatusbarctrl-class.md) podpory poskytuje přizpůsobení stavového řádku. Například pomocí běžného ovládacího prvku můžete určit styl, který obsahuje úchyt pro změnu velikosti na stavovém řádku, nebo můžete určit styl, který má zobrazovat stavový řádek v horní části klientské oblasti nadřazeného okna.

Obecnější informace o běžných ovládacích prvcích najdete v tématu [běžné ovládací prvky](/windows/win32/Controls/common-controls-intro) v Windows SDK.

##  <a name="setindicators"></a>CStatusBar –:: SetIndicators

Nastaví identifikátor každého indikátoru na hodnotu určenou odpovídajícím prvkem pole *lpIDArray*, načte prostředek řetězce určený jednotlivými ID a nastaví text indikátoru na řetězec.

```
BOOL SetIndicators(
    const UINT* lpIDArray,
    int nIDCount);
```

### <a name="parameters"></a>Parametry

*lpIDArray*<br/>
Ukazatel na pole identifikátorů.

*nIDCount*<br/>
Počet prvků v poli, na které ukazuje *lpIDArray*.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

##  <a name="setpaneinfo"></a>CStatusBar –:: SetPaneInfo

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
Index podokna indikátoru, jehož styl má být nastaven.

*nID*<br/>
Nové ID pro podokno indikátoru

*nStyle*<br/>
Nový styl pro podokno indikátoru

*cxWidth*<br/>
Nová šířka podokna indikátoru

### <a name="remarks"></a>Poznámky

Podporují se tyto styly ukazatelů:

- SBPS_NOBORDERS bez trojrozměrného ohraničení kolem podokna.

- SBPS_POPOUT obrácené ohraničení tak, že text "" zobrazí ".

- SBPS_DISABLED Nekreslit text.

- SBPS_STRETCH roztažené podokno pro vyplnění nevyužitého místa. Tento styl může mít pouze jeden panel na stavovém řádku.

- SBPS_NORMAL bez roztažení, ohraničení nebo automaticky otevíraného okna.

##  <a name="setpanestyle"></a>CStatusBar –:: SetPaneStyle

Chcete-li nastavit styl podokna stavového řádku, zavolejte tuto členskou funkci.

```
void SetPaneStyle(
    int nIndex,
    UINT nStyle);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index podokna, jehož styl má být nastaven

*nStyle*<br/>
Styl podokna, jehož styl má být nastaven

### <a name="remarks"></a>Poznámky

Styl podokna určuje, jak se podokno zobrazuje.

Seznam stylů dostupných pro stavové řádky naleznete v tématu [SetPaneInfo](#setpaneinfo).

##  <a name="setpanetext"></a>CStatusBar –:: SetPaneText

Zavolejte tuto členskou funkci pro nastavení textu podokna na řetězec, na který odkazuje *lpszNewText*.

```
BOOL SetPaneText(
    int nIndex,
    LPCTSTR lpszNewText,
    BOOL bUpdate = TRUE);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index podokna, jehož text má být nastaven

*lpszNewText*<br/>
Ukazatel na text nového podokna.

*bUpdate*<br/>
Pokud je nastaveno na TRUE, po nastavení textu se zruší platnost podokna.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Po volání `SetPaneText`je nutné přidat obslužnou rutinu aktualizace uživatelského rozhraní pro zobrazení nového textu ve stavovém řádku.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#176](../../mfc/codesnippet/cpp/cstatusbar-class_1.cpp)]

[!code-cpp[NVC_MFCDocView#177](../../mfc/codesnippet/cpp/cstatusbar-class_2.cpp)]

[!code-cpp[NVC_MFCDocView#178](../../mfc/codesnippet/cpp/cstatusbar-class_3.cpp)]

## <a name="see-also"></a>Viz také:

[CTRLBARS Sample MFC](../../overview/visual-cpp-samples.md)<br/>
[DLGCBR32 Sample MFC](../../overview/visual-cpp-samples.md)<br/>
[CControlBar – třída](../../mfc/reference/ccontrolbar-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CStatusBarCtrl – třída](../../mfc/reference/cstatusbarctrl-class.md)<br/>
[CControlBar – třída](../../mfc/reference/ccontrolbar-class.md)
