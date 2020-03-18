---
title: CToolTipCtrl – třída
ms.date: 11/04/2016
f1_keywords:
- CToolTipCtrl
- AFXCMN/CToolTipCtrl
- AFXCMN/CToolTipCtrl::CToolTipCtrl
- AFXCMN/CToolTipCtrl::Activate
- AFXCMN/CToolTipCtrl::AddTool
- AFXCMN/CToolTipCtrl::AdjustRect
- AFXCMN/CToolTipCtrl::Create
- AFXCMN/CToolTipCtrl::CreateEx
- AFXCMN/CToolTipCtrl::DelTool
- AFXCMN/CToolTipCtrl::GetBubbleSize
- AFXCMN/CToolTipCtrl::GetCurrentTool
- AFXCMN/CToolTipCtrl::GetDelayTime
- AFXCMN/CToolTipCtrl::GetMargin
- AFXCMN/CToolTipCtrl::GetMaxTipWidth
- AFXCMN/CToolTipCtrl::GetText
- AFXCMN/CToolTipCtrl::GetTipBkColor
- AFXCMN/CToolTipCtrl::GetTipTextColor
- AFXCMN/CToolTipCtrl::GetTitle
- AFXCMN/CToolTipCtrl::GetToolCount
- AFXCMN/CToolTipCtrl::GetToolInfo
- AFXCMN/CToolTipCtrl::HitTest
- AFXCMN/CToolTipCtrl::Pop
- AFXCMN/CToolTipCtrl::Popup
- AFXCMN/CToolTipCtrl::RelayEvent
- AFXCMN/CToolTipCtrl::SetDelayTime
- AFXCMN/CToolTipCtrl::SetMargin
- AFXCMN/CToolTipCtrl::SetMaxTipWidth
- AFXCMN/CToolTipCtrl::SetTipBkColor
- AFXCMN/CToolTipCtrl::SetTipTextColor
- AFXCMN/CToolTipCtrl::SetTitle
- AFXCMN/CToolTipCtrl::SetToolInfo
- AFXCMN/CToolTipCtrl::SetToolRect
- AFXCMN/CToolTipCtrl::SetWindowTheme
- AFXCMN/CToolTipCtrl::Update
- AFXCMN/CToolTipCtrl::UpdateTipText
helpviewer_keywords:
- CToolTipCtrl [MFC], CToolTipCtrl
- CToolTipCtrl [MFC], Activate
- CToolTipCtrl [MFC], AddTool
- CToolTipCtrl [MFC], AdjustRect
- CToolTipCtrl [MFC], Create
- CToolTipCtrl [MFC], CreateEx
- CToolTipCtrl [MFC], DelTool
- CToolTipCtrl [MFC], GetBubbleSize
- CToolTipCtrl [MFC], GetCurrentTool
- CToolTipCtrl [MFC], GetDelayTime
- CToolTipCtrl [MFC], GetMargin
- CToolTipCtrl [MFC], GetMaxTipWidth
- CToolTipCtrl [MFC], GetText
- CToolTipCtrl [MFC], GetTipBkColor
- CToolTipCtrl [MFC], GetTipTextColor
- CToolTipCtrl [MFC], GetTitle
- CToolTipCtrl [MFC], GetToolCount
- CToolTipCtrl [MFC], GetToolInfo
- CToolTipCtrl [MFC], HitTest
- CToolTipCtrl [MFC], Pop
- CToolTipCtrl [MFC], Popup
- CToolTipCtrl [MFC], RelayEvent
- CToolTipCtrl [MFC], SetDelayTime
- CToolTipCtrl [MFC], SetMargin
- CToolTipCtrl [MFC], SetMaxTipWidth
- CToolTipCtrl [MFC], SetTipBkColor
- CToolTipCtrl [MFC], SetTipTextColor
- CToolTipCtrl [MFC], SetTitle
- CToolTipCtrl [MFC], SetToolInfo
- CToolTipCtrl [MFC], SetToolRect
- CToolTipCtrl [MFC], SetWindowTheme
- CToolTipCtrl [MFC], Update
- CToolTipCtrl [MFC], UpdateTipText
ms.assetid: 8973f70c-b73a-46c7-908d-758f364b9a97
ms.openlocfilehash: bf32671eb3535de1bf072e24bc642145e87c84ee
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79420902"
---
# <a name="ctooltipctrl-class"></a>CToolTipCtrl – třída

Zapouzdřuje funkce "ovládacího prvku popis tlačítka", což je malé automaticky otevírané okno, které zobrazuje jeden řádek textu popisujícího účel nástroje v aplikaci.

## <a name="syntax"></a>Syntaxe

```
class CToolTipCtrl : public CWnd
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CToolTipCtrl:: CToolTipCtrl](#ctooltipctrl)|Vytvoří objekt `CToolTipCtrl`.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CToolTipCtrl:: Activate](#activate)|Aktivuje a deaktivuje ovládací prvek popis tlačítka.|
|[CToolTipCtrl:: AddTool](#addtool)|Registruje nástroj s ovládacím prvkem popis tlačítka.|
|[CToolTipCtrl:: AdjustRect](#adjustrect)|Převede mezi obdélníkem zobrazení textu ovládacího prvku Tip nástroje a jeho obdélníkem okna.|
|[CToolTipCtrl:: Create](#create)|Vytvoří ovládací prvek popis tlačítka a připojí ho k objektu `CToolTipCtrl`.|
|[CToolTipCtrl:: CreateEx](#createex)|Vytvoří ovládací prvek popis tlačítka se zadanými rozšířenými styly Windows a připojí ho k objektu `CToolTipCtrl`.|
|[CToolTipCtrl::D elTool](#deltool)|Odebere nástroj z ovládacího prvku popisek nástroje.|
|[CToolTipCtrl:: GetBubbleSize](#getbubblesize)|Načte velikost popisu tlačítka.|
|[CToolTipCtrl:: GetCurrentTool](#getcurrenttool)|Načte informace, jako je například velikost, pozice a text okna s popisem tlačítka, které zobrazuje aktuální ovládací prvek ToolTip.|
|[CToolTipCtrl:: GetDelayTime](#getdelaytime)|Načte počáteční, místní a znovu zobrazované doby trvání, které jsou aktuálně nastaveny pro ovládací prvek popis tlačítka.|
|[CToolTipCtrl:: getmarže](#getmargin)|Načte horní, levý, dolní a pravý okraj, který je nastaven pro okno s popisem tlačítka.|
|[CToolTipCtrl:: GetMaxTipWidth](#getmaxtipwidth)|Načte maximální šířku okna s popisem tlačítka.|
|[CToolTipCtrl:: GetText](#gettext)|Načte text, který ovládací prvek popisu tlačítka udržuje pro nástroj.|
|[CToolTipCtrl:: GetTipBkColor](#gettipbkcolor)|Načte barvu pozadí v okně popisu tlačítka.|
|[CToolTipCtrl:: GetTipTextColor](#gettiptextcolor)|Načte barvu textu v okně popisu tlačítka.|
|[CToolTipCtrl:: getTitle](#gettitle)|Načte název aktuálního ovládacího prvku ToolTip.|
|[CToolTipCtrl:: GetToolCount](#gettoolcount)|Načte počet nástrojů udržovaných ovládacím prvkem popis tlačítka.|
|[CToolTipCtrl:: GetToolInfo](#gettoolinfo)|Načte informace, které ovládací prvek popisu tlačítka udržuje o nástroji.|
|[CToolTipCtrl:: HitTest](#hittest)|Testuje bod, aby určil, zda se nachází uvnitř ohraničujícího obdélníku daného nástroje. Pokud ano, načte informace o nástroji.|
|[CToolTipCtrl::P op](#pop)|Odebere zobrazený okno s popisem tlačítka ze zobrazení.|
|[CToolTipCtrl::P opup](#popup)|Způsobí, že aktuální ovládací prvek ToolTip se zobrazí na souřadnicích poslední zprávy myši.|
|[CToolTipCtrl:: RelayEvent](#relayevent)|Předá zprávu myši ovládacímu prvku popisu tlačítka ke zpracování.|
|[CToolTipCtrl:: SetDelayTime](#setdelaytime)|Nastaví počáteční, místní a znovu zobrazované doby trvání pro ovládací prvek popis tlačítka.|
|[CToolTipCtrl:: SetMargin](#setmargin)|Nastaví horní, levý, dolní a pravý okraj okna s popisem tlačítka.|
|[CToolTipCtrl:: SetMaxTipWidth](#setmaxtipwidth)|Nastaví maximální šířku okna s popisem tlačítka.|
|[CToolTipCtrl:: SetTipBkColor](#settipbkcolor)|Nastaví barvu pozadí v okně popisu tlačítka.|
|[CToolTipCtrl:: SetTipTextColor](#settiptextcolor)|Nastaví barvu textu v okně popisu tlačítka.|
|[CToolTipCtrl:: SetTitle](#settitle)|Přidá standardní ikonu a řetězec názvu k popisu tlačítka.|
|[CToolTipCtrl:: SetToolInfo](#settoolinfo)|Nastaví informace, které Popis nástroje udržuje pro nástroj.|
|[CToolTipCtrl:: SetToolRect](#settoolrect)|Nastaví nový ohraničující obdélník pro nástroj.|
|[CToolTipCtrl:: SetWindowTheme](#setwindowtheme)|Nastaví styl vizuálu okna s popisem tlačítka.|
|[CToolTipCtrl:: Update](#update)|Vynutí překreslení aktuálního nástroje.|
|[CToolTipCtrl:: UpdateTipText](#updatetiptext)|Nastaví text tipu nástroje pro nástroj.|

## <a name="remarks"></a>Poznámky

"Nástroj" je buď okno, například podřízené okno nebo ovládací prvek, nebo obdélníkově definovaná aplikace v rámci klientské oblasti okna. Popis tlačítka je v tuto chvíli skrytý a zobrazuje se jenom v případě, že uživatel přesune kurzor na nástroj a ponechá ho na přibližně jednu polovinu sekundy. Pokud uživatel klikne na tlačítko myši nebo přesune kurzor mimo nástroj, zobrazí se popis tlačítka v blízkosti kurzoru a zmizí.

`CToolTipCtrl` poskytuje funkce pro řízení počátečního času a doby trvání popisu tlačítka, šířky okraje obklopující text popisu tlačítka, šířku samotného okna s popisem tlačítka a pozadí a barvu textu popisu tlačítka. Jeden ovládací prvek popis tlačítka může poskytovat informace pro více než jeden nástroj.

Třída `CToolTipCtrl` poskytuje funkce pro Common Windows Control Tip. Tento ovládací prvek (a proto třída `CToolTipCtrl`) je k dispozici pouze pro programy, které jsou spuštěny v systémech Windows 95/98 a Windows NT verze 3,51 a novější.

Další informace o povolení tipů nástrojů naleznete v tématu [tipy nástrojů v systému Windows nejsou odvozeny od CFrameWnd](../../mfc/tool-tips-in-windows-not-derived-from-cframewnd.md).

Další informace o použití `CToolTipCtrl`naleznete v tématu [Controls](../../mfc/controls-mfc.md) and [using CToolTipCtrl](../../mfc/using-ctooltipctrl.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CToolTipCtrl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxcmn. h

##  <a name="activate"></a>CToolTipCtrl:: Activate

Voláním této funkce aktivujete nebo deaktivujete ovládací prvek popis tlačítka.

```
void Activate(BOOL bActivate);
```

### <a name="parameters"></a>Parametry

*bActivate*<br/>
Určuje, zda má být ovládací prvek popis tlačítka aktivován nebo dezaktivován.

### <a name="remarks"></a>Poznámky

Pokud má *bActivate* hodnotu true, je aktivován ovládací prvek; Pokud je hodnota FALSE, deaktivuje se.

Když je ovládací prvek popis tlačítka aktivní, informace o popisu tlačítka se zobrazí, když se ukazatel myši nachází na nástroji, který je zaregistrován s ovládacím prvkem. Pokud je neaktivní, informace o popisu tlačítka se nezobrazí, ani když se ukazatel myši nachází na nástroji.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CPropertySheet –:: GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).

##  <a name="addtool"></a>CToolTipCtrl:: AddTool

Registruje nástroj s ovládacím prvkem popis tlačítka.

```
BOOL AddTool(
    CWnd* pWnd,
    UINT nIDText,
    LPCRECT lpRectTool = NULL,
    UINT_PTR nIDTool = 0);

BOOL AddTool(
    CWnd* pWnd,
    LPCTSTR lpszText = LPSTR_TEXTCALLBACK,
    LPCRECT lpRectTool = NULL,
    UINT_PTR nIDTool = 0);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Ukazatel na okno, které obsahuje nástroj.

*nIDText*<br/>
ID řetězcového prostředku, který obsahuje text pro nástroj.

*lpRectTool*<br/>
Ukazatel na strukturu [Rect](/previous-versions/dd162897\(v=vs.85\)) obsahující souřadnice ohraničujícího obdélníku nástroje. Souřadnice jsou relativní vzhledem k levému hornímu rohu klientské oblasti okna identifikovaného pomocí *pWnd*.

*nIDTool*<br/>
ID nástroje

*lpszText*<br/>
Ukazatel na text pro nástroj. Pokud tento parametr obsahuje hodnotu LPSTR_TEXTCALLBACK, TTN_NEEDTEXT oznamovacích zpráv přejde na nadřazený prvek okna, na které odkazuje *pWnd* .

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Parametry *lpRectTool* a *nIDTool* musí být platné, nebo pokud má *lpRectTool* hodnotu null, *nIDTool* musí být 0.

Ovládací prvek popisu tlačítka může být přidružen k více než jednomu nástroji. Voláním této funkce zaregistrujete nástroj s ovládacím prvkem popis tlačítka, aby se informace uložené v popisku nástroje zobrazily, když je ukazatel myši na nástroji.

> [!NOTE]
>  Pomocí `AddTool`nelze nastavit popis tlačítka na statický ovládací prvek.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CPropertySheet –:: GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).

##  <a name="adjustrect"></a>CToolTipCtrl:: AdjustRect

Převede mezi obdélníkem zobrazení textu ovládacího prvku ToolTip a jeho obdélníkem okna.

```
BOOL AdjustRect(
    LPRECT lprc,
    BOOL bLarger = TRUE);
```

### <a name="parameters"></a>Parametry

*lprc*<br/>
Ukazatel na strukturu [Rect](/previous-versions/dd162897\(v=vs.85\)) , která obsahuje obdélník okna s popisem tlačítka nebo obdélník pro zobrazení textu.

*bLarger*<br/>
Při hodnotě TRUE se k určení obdélníku zobrazení textu použije *lprc* a dostane odpovídající rámeček okna. Pokud je nastaveno na hodnotu FALSE, *lprc* se použije k určení obdélníku okna a obdrží odpovídající obdélník zobrazení textu.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je obdélník úspěšně upravován; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce vypočítá obdélník zobrazení textu ovládacího prvku s popisem tlačítka z jeho rámečku okna nebo obdélník okna s popisem tlačítka, který je potřeba k zobrazení zadaného obdélníku zobrazení textu.

Tato členská funkce implementuje chování zprávy Win32 [TTM_ADJUSTRECT](/windows/win32/Controls/ttm-adjustrect), jak je popsáno v Windows SDK.

##  <a name="create"></a>CToolTipCtrl:: Create

Vytvoří ovládací prvek popis tlačítka a připojí ho k objektu `CToolTipCtrl`.

```
virtual BOOL Create(CWnd* pParentWnd, DWORD dwStyle = 0);
```

### <a name="parameters"></a>Parametry

*pParentWnd*<br/>
Určuje nadřazené okno ovládacího prvku Tip nástroje, obvykle `CDialog`. Nesmí mít hodnotu NULL.

*dwStyle*<br/>
Určuje styl ovládacího prvku Tip nástroje. Další informace najdete v části **poznámky** .

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je objekt `CToolTipCtrl` úspěšně vytvořen; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Sestavíte `CToolTipCtrl` ve dvou krocích. Nejprve zavolejte konstruktor pro vytvoření objektu `CToolTipCtrl` a potom zavolejte `Create` k vytvoření ovládacího prvku popisu tlačítka a jeho připojení k objektu `CToolTipCtrl`.

Parametr *dwStyle* může být libovolná kombinace [stylů oken](../../mfc/reference/styles-used-by-mfc.md#window-styles). Kromě toho ovládací prvek popis tlačítka má dva styly specifické pro třídu: TTS_ALWAYSTIP a TTS_NOPREFIX.

|Styl|Význam|
|-----------|-------------|
|TTS_ALWAYSTIP|Určuje, že se má popis tlačítka zobrazovat, když se ukazatel myši nachází na nástroji, bez ohledu na to, jestli je aktivní nebo neaktivní okno vlastníka ovládacího prvku Popis nástroje. Bez tohoto stylu se ovládací prvek popis tlačítka zobrazí, když je okno vlastníka nástroje aktivní, ale ne, pokud je neaktivní.|
|TTS_NOPREFIX|Tento styl brání systému v odložení znaku ampersandu (&) z řetězce. Pokud ovládací prvek popis tlačítka nemá styl TTS_NOPREFIX, systém automaticky odliští znaky ampersandu, což umožňuje aplikaci použít stejný řetězec jako položku nabídky a jako text v ovládacím prvku popis tlačítka.|

Ovládací prvek popis tlačítka má WS_POPUP a WS_EX_TOOLWINDOW styly oken bez ohledu na to, zda je při vytváření ovládacího prvku zadáno.

Chcete-li vytvořit ovládací prvek popis tlačítka pomocí rozšířených stylů Windows, zavolejte [CToolTipCtrl:: CreateEx](#createex) namísto `Create`.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CPropertySheet –:: GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).

##  <a name="createex"></a>CToolTipCtrl:: CreateEx

Vytvoří ovládací prvek (podřízené okno) a přidruží ho k objektu `CToolTipCtrl`.

```
virtual BOOL CreateEx(
    CWnd* pParentWnd,
    DWORD dwStyle = 0,
    DWORD dwStyleEx = 0);
```

### <a name="parameters"></a>Parametry

*pParentWnd*<br/>
Ukazatel na okno, které je nadřazený ovládacímu prvku.

*dwStyle*<br/>
Určuje styl ovládacího prvku Tip nástroje. Další informace najdete v části s **poznámkami** v tématu [Vytvoření](#create) .

*dwStyleEx*<br/>
Určuje rozšířený styl ovládacího prvku, který se vytváří. Seznam rozšířených stylů Windows naleznete v parametru *dwExStyle* pro [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) v Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné v opačném případě 0.

### <a name="remarks"></a>Poznámky

Použijte `CreateEx` místo `Create` pro použití rozšířených stylů Windows, které jsou určené **WS_EX_m**rozšířeným stylem pro Windows.

##  <a name="ctooltipctrl"></a>CToolTipCtrl:: CToolTipCtrl

Vytvoří objekt `CToolTipCtrl`.

```
CToolTipCtrl();
```

### <a name="remarks"></a>Poznámky

Po sestavení objektu je třeba volat `Create`.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCControlLadenDialog#74](../../mfc/codesnippet/cpp/ctooltipctrl-class_1.h)]

##  <a name="deltool"></a>CToolTipCtrl::D elTool

Odebere nástroj určený pomocí *pWnd* a *nIDTool* z kolekce nástrojů podporovaných ovládacím prvkem popis tlačítka.

```
void DelTool(
    CWnd* pWnd,
    UINT_PTR nIDTool = 0);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Ukazatel na okno, které obsahuje nástroj.

*nIDTool*<br/>
ID nástroje

##  <a name="getbubblesize"></a>CToolTipCtrl:: GetBubbleSize

Načte velikost popisu tlačítka.

```
CSize GetBubbleSize(LPTOOLINFO lpToolInfo) const;
```

### <a name="parameters"></a>Parametry

*lpToolInfo*<br/>
Ukazatel na strukturu [TOOLINFO](/windows/win32/api/commctrl/ns-commctrl-tttoolinfoa) popisu nástroje.

### <a name="return-value"></a>Návratová hodnota

Velikost popisu tlačítka

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [TTM_GETBUBBLESIZE](/windows/win32/Controls/ttm-getbubblesize), jak je popsáno v Windows SDK.

##  <a name="getcurrenttool"></a>CToolTipCtrl:: GetCurrentTool

Načte informace, například velikost, umístění a text, okna s popisem tlačítka zobrazeného aktuálním ovládacím prvkem ToolTip.

```
BOOL GetCurrentTool(LPTOOLINFO lpToolInfo) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*lpToolInfo*|mimo Ukazatel na strukturu [TOOLINFO](/windows/win32/api/commctrl/ns-commctrl-tttoolinfoa) , která přijímá informace o aktuálním okně s popisem.|

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud se informace úspěšně načítají; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Tato metoda pošle zprávu [TTM_GETCURRENTTOOL](/windows/win32/Controls/ttm-getcurrenttool) , která je popsána v Windows SDK.

### <a name="example"></a>Příklad

Následující příklad kódu načte informace o aktuálním okně s popisem tlačítka.

[!code-cpp[NVC_MFC_CToolBarCtrl_s1#6](../../mfc/reference/codesnippet/cpp/ctooltipctrl-class_2.cpp)]

##  <a name="getdelaytime"></a>CToolTipCtrl:: GetDelayTime

Načte počáteční, místní a znovu zobrazované doby trvání nastavené pro ovládací prvek popis tlačítka.

```
int GetDelayTime(DWORD dwDuration) const;
```

### <a name="parameters"></a>Parametry

*dwDuration*<br/>
Příznak, který určuje, která hodnota trvání bude načtena. Tento parametr může být jedna z následujících hodnot:

- TTDT_AUTOPOP načíst dobu, po kterou zůstane okno s popisem tlačítka viditelné, pokud je ukazatel v ohraničujícím obdélníku nástroje nehybný.

- TTDT_INITIAL načíst dobu, po kterou musí ukazatel v ohraničujícím obdélníku nástroje zůstat, než se zobrazí okno s popisem tlačítka.

- TTDT_RESHOW načíst dobu potřebnou k zobrazení dalších oken s popisem tlačítka, když se ukazatel myši přesune z jednoho nástroje na jiný.

### <a name="return-value"></a>Návratová hodnota

Zadaný čas zpoždění v milisekundách

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [TTM_GETDELAYTIME](/windows/win32/Controls/ttm-getdelaytime), jak je popsáno v Windows SDK.

##  <a name="getmargin"></a>CToolTipCtrl:: getmarže

Načte horní, levý, dolní a pravý okraj sady nástrojů pro okno s popisem tlačítka.

```
void GetMargin(LPRECT lprc) const;
```

### <a name="parameters"></a>Parametry

*lprc*<br/>
Adresa `RECT` struktury, která obdrží informace o okraji. Členové struktury [Rect](/previous-versions/dd162897\(v=vs.85\)) nedefinují ohraničující obdélník. Pro účely této zprávy jsou členy struktury interpretovány takto:

|Člen|Obrázek|
|------------|--------------------|
|`top`|Vzdálenost mezi horním ohraničením a horním textem tipu nástroje v pixelech|
|`left`|Vzdálenost mezi levým ohraničením a levým koncem textu tipu v pixelech|
|`bottom`|Vzdálenost mezi dolním ohraničením a dolním okrajem textu tipu (v pixelech)|
|`right`|Vzdálenost mezi pravým okrajem a pravým koncem textu tipu v pixelech|

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [TTM_GETMARGIN](/windows/win32/Controls/ttm-getmargin), jak je popsáno v Windows SDK.

##  <a name="getmaxtipwidth"></a>CToolTipCtrl:: GetMaxTipWidth

Načte maximální šířku okna s popisem tlačítka.

```
int GetMaxTipWidth() const;
```

### <a name="return-value"></a>Návratová hodnota

Maximální šířka okna s popisem tlačítka

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [TTM_GETMAXTIPWIDTH](/windows/win32/Controls/ttm-getmaxtipwidth), jak je popsáno v Windows SDK.

##  <a name="gettext"></a>CToolTipCtrl:: GetText

Načte text, který ovládací prvek popisu tlačítka udržuje pro nástroj.

```
void GetText(
    CString& str,
    CWnd* pWnd,
    UINT_PTR nIDTool = 0) const;
```

### <a name="parameters"></a>Parametry

*str*<br/>
Odkaz na objekt `CString`, který obdrží text nástroje.

*pWnd*<br/>
Ukazatel na okno, které obsahuje nástroj.

*nIDTool*<br/>
ID nástroje

### <a name="remarks"></a>Poznámky

Parametry *pWnd* a *nIDTool* identifikují nástroj. Pokud byl tento nástroj dříve zaregistrován pomocí ovládacího prvku popis tlačítka pomocí předchozího volání `CToolTipCtrl::AddTool`, je objekt, na který je odkazován parametrem *str* , přiřazený text nástroje.

##  <a name="gettipbkcolor"></a>CToolTipCtrl:: GetTipBkColor

Načte barvu pozadí v okně popisu tlačítka.

```
COLORREF GetTipBkColor() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota [COLORREF](/windows/win32/gdi/colorref) , která představuje barvu pozadí.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [TTM_GETTIPBKCOLOR](/windows/win32/Controls/ttm-gettipbkcolor), jak je popsáno v Windows SDK.

##  <a name="gettiptextcolor"></a>CToolTipCtrl:: GetTipTextColor

Načte barvu textu v okně popisu tlačítka.

```
COLORREF GetTipTextColor() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota [COLORREF](/windows/win32/gdi/colorref) , která představuje barvu textu.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [TTM_GETTIPTEXTCOLOR](/windows/win32/Controls/ttm-gettiptextcolor), jak je popsáno v Windows SDK.

##  <a name="gettitle"></a>CToolTipCtrl:: getTitle

Načte název aktuálního ovládacího prvku ToolTip.

```
void GetTitle(PTTGETTITLE pttgt) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*pttgt*|mimo Ukazatel na strukturu [TTGETTITLE](/windows/win32/api/commctrl/ns-commctrl-ttgettitle) , která obsahuje informace o ovládacím prvku ToolTip. Když tato metoda vrátí hodnotu, člen *pszTitle* struktury [TTGETTITLE](/windows/win32/api/commctrl/ns-commctrl-ttgettitle) odkazuje na text nadpisu.|

### <a name="remarks"></a>Poznámky

Tato metoda pošle zprávu [TTM_GETTITLE](/windows/win32/Controls/ttm-gettitle) , která je popsána v Windows SDK.

##  <a name="gettoolcount"></a>CToolTipCtrl:: GetToolCount

Načte počet nástrojů zaregistrovaných pomocí ovládacího prvku tip k nástroji.

```
int GetToolCount() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet nástrojů zaregistrovaných pomocí ovládacího prvku Tip nástroje.

##  <a name="gettoolinfo"></a>CToolTipCtrl:: GetToolInfo

Načte informace, které ovládací prvek popisu tlačítka udržuje o nástroji.

```
BOOL GetToolInfo(
    CToolInfo& ToolInfo,
    CWnd* pWnd,
    UINT_PTR nIDTool = 0) const;
```

### <a name="parameters"></a>Parametry

*ToolInfo*<br/>
Odkaz na objekt `TOOLINFO`, který obdrží text nástroje.

*pWnd*<br/>
Ukazatel na okno, které obsahuje nástroj.

*nIDTool*<br/>
ID nástroje

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

`hwnd` a `uId` členy struktury [TOOLINFO](/windows/win32/api/commctrl/ns-commctrl-tttoolinfoa) , na které odkazuje *CToolInfo* , identifikují nástroj. Pokud byl tento nástroj zaregistrován pomocí ovládacího prvku popis tlačítka pomocí předchozího volání `AddTool`, je struktura `TOOLINFO` vyplněna informacemi o nástroji.

##  <a name="hittest"></a>CToolTipCtrl:: HitTest

Testuje bod, aby zjistil, zda se nachází uvnitř ohraničujícího obdélníku daného nástroje, a pokud ano, načtěte informace o nástroji.

```
BOOL HitTest(
    CWnd* pWnd,
    CPoint pt,
    LPTOOLINFO lpToolInfo) const;
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Ukazatel na okno, které obsahuje nástroj.

*bodů*<br/>
Ukazatel na objekt `CPoint` obsahující souřadnice bodu, který má být testován.

*lpToolInfo*<br/>
Ukazatel na strukturu [TOOLINFO](/windows/win32/api/commctrl/ns-commctrl-tttoolinfoa) , která obsahuje informace o nástroji.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je bod určený informacemi o testu v rámci ohraničujícího obdélníku nástroje; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Pokud tato funkce vrací nenulovou hodnotu, struktura, na kterou se odkazuje pomocí *lpToolInfo* , je vyplněna informacemi o nástroji v rámci místa, kde leží bod v jeho obdélníku.

Struktura `TTHITTESTINFO` je definována takto:

```cpp
typedef struct _TT_HITTESTINFO { // tthti
    HWND hwnd;   // handle of tool or window with tool
    POINT pt;    // client coordinates of point to test
    TOOLINFO ti; // receives information about the tool
} TTHITTESTINFO, FAR * LPHITTESTINFO;
```

- `hwnd`

   Určuje popisovač nástroje.

- `pt`

   Určuje souřadnice bodu, pokud je bod v ohraničujícím obdélníku nástroje.

- `ti`

   Informace o nástroji. Další informace o struktuře `TOOLINFO` naleznete v tématu [CToolTipCtrl:: GetToolInfo](#gettoolinfo).

##  <a name="pop"></a>CToolTipCtrl::P op

Odebere ze zobrazení zobrazené okno s popisem nástroje.

```
void Pop();
```

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [TTM_POP](/windows/win32/Controls/ttm-pop), jak je popsáno v Windows SDK.

##  <a name="popup"></a>CToolTipCtrl::P opup

Způsobí, že aktuální ovládací prvek ToolTip se zobrazí na souřadnicích poslední zprávy myši.

```
void Popup();
```

### <a name="remarks"></a>Poznámky

Tato metoda pošle zprávu [TTM_POPUP](/windows/win32/Controls/ttm-popup) , která je popsána v Windows SDK.

### <a name="example"></a>Příklad

Následující příklad kódu zobrazí okno s popisem tlačítka.

[!code-cpp[NVC_MFC_CToolBarCtrl_s1#7](../../mfc/reference/codesnippet/cpp/ctooltipctrl-class_3.cpp)]

##  <a name="relayevent"></a>CToolTipCtrl:: RelayEvent

Předá zprávu myši ovládacímu prvku popisu tlačítka ke zpracování.

```
void RelayEvent(LPMSG lpMsg);
```

### <a name="parameters"></a>Parametry

*lpMsg*<br/>
Ukazatel [na strukturu zprávy](/windows/win32/api/winuser/ns-winuser-msg) , která obsahuje zprávu pro předání.

### <a name="remarks"></a>Poznámky

Ovládací prvek popis tlačítka zpracovává pouze následující zprávy, které jsou do něj odesílány `RelayEvent`:

|WM_LBUTTONDOWN|WM_MOUSEMOVE|
|---------------------|-------------------|
|WM_LBUTTONUP|WM_RBUTTONDOWN|
|WM_MBUTTONDOWN|WM_RBUTTONUP|
|WM_MBUTTONUP||

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CPropertySheet –:: GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).

##  <a name="setdelaytime"></a>CToolTipCtrl:: SetDelayTime

Nastaví dobu zpoždění pro ovládací prvek popis tlačítka.

```
void SetDelayTime(UINT nDelay);

void SetDelayTime(
    DWORD dwDuration,
    int iTime);
```

### <a name="parameters"></a>Parametry

*nDelay*<br/>
Určuje novou dobu zpoždění (v milisekundách).

*dwDuration*<br/>
Příznak, který určuje, která hodnota trvání bude načtena. Popis platných hodnot naleznete v tématu [CToolTipCtrl:: GetDelayTime](#getdelaytime) .

*iTime*<br/>
Zadaný čas zpoždění v milisekundách.

### <a name="remarks"></a>Poznámky

Doba zpoždění je doba, po kterou musí kurzor zůstat na nástroji, aby se zobrazilo okno s popisem tlačítka. Výchozí doba zpoždění je 500 milisekund.

##  <a name="setmargin"></a>CToolTipCtrl:: SetMargin

Nastaví horní, levý, dolní a pravý okraj okna s popisem tlačítka.

```
void SetMargin(LPRECT lprc);
```

### <a name="parameters"></a>Parametry

*lprc*<br/>
Adresa `RECT` struktury obsahující informace o okraji, které mají být nastaveny. Členové struktury `RECT` nedefinují ohraničující obdélník. Popis informací o okrajích naleznete v tématu [CToolTipCtrl:: Getmarže](#getmargin) .

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [TTM_SETMARGIN](/windows/win32/Controls/ttm-setmargin), jak je popsáno v Windows SDK.

##  <a name="setmaxtipwidth"></a>CToolTipCtrl:: SetMaxTipWidth

Nastaví maximální šířku okna s popisem tlačítka.

```
int SetMaxTipWidth(int iWidth);
```

### <a name="parameters"></a>Parametry

*iWidth*<br/>
Hodnota maximální šířky okna pro popis tlačítka

### <a name="return-value"></a>Návratová hodnota

Předchozí maximální šířka tipu.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [TTM_SETMAXTIPWIDTH](/windows/win32/Controls/ttm-setmaxtipwidth), jak je popsáno v Windows SDK.

##  <a name="settipbkcolor"></a>CToolTipCtrl:: SetTipBkColor

Nastaví barvu pozadí v okně popisu tlačítka.

```
void SetTipBkColor(COLORREF clr);
```

### <a name="parameters"></a>Parametry

*CLR*<br/>
Nová barva pozadí.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [TTM_SETTIPBKCOLOR](/windows/win32/Controls/ttm-settipbkcolor), jak je popsáno v Windows SDK.

##  <a name="settiptextcolor"></a>CToolTipCtrl:: SetTipTextColor

Nastaví barvu textu v okně popisu tlačítka.

```
void SetTipTextColor(COLORREF clr);
```

### <a name="parameters"></a>Parametry

*CLR*<br/>
Nová barva textu.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [TTM_SETTIPTEXTCOLOR](/windows/win32/Controls/ttm-settiptextcolor), jak je popsáno v Windows SDK.

##  <a name="settitle"></a>CToolTipCtrl:: SetTitle

Přidá standardní ikonu a řetězec názvu k popisu tlačítka.

```
BOOL SetTitle(
    UINT uIcon,
    LPCTSTR lpstrTitle);
```

### <a name="parameters"></a>Parametry

*uIcon*<br/>
Viz *ikona* v [TTM_SETTITLE](/windows/win32/Controls/ttm-settitle) Windows SDK.

*lpstrTitle*<br/>
Ukazatel na řetězec názvu.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [TTM_SETTITLE](/windows/win32/Controls/ttm-settitle), jak je popsáno v Windows SDK.

##  <a name="settoolinfo"></a>CToolTipCtrl:: SetToolInfo

Nastaví informace, které Popis nástroje udržuje pro nástroj.

```
void SetToolInfo(LPTOOLINFO lpToolInfo);
```

### <a name="parameters"></a>Parametry

*lpToolInfo*<br/>
Ukazatel na strukturu [TOOLINFO](/windows/win32/api/commctrl/ns-commctrl-tttoolinfoa) , která určuje informace, které mají být nastaveny.

##  <a name="settoolrect"></a>CToolTipCtrl:: SetToolRect

Nastaví nový ohraničující obdélník pro nástroj.

```
void SetToolRect(
    CWnd* pWnd,
    UINT_PTR nIDTool,
    LPCRECT lpRect);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Ukazatel na okno, které obsahuje nástroj.

*nIDTool*<br/>
ID nástroje

*lpRect*<br/>
Ukazatel na strukturu [Rect](/previous-versions/dd162897\(v=vs.85\)) určující nový ohraničovací obdélník.

##  <a name="setwindowtheme"></a>CToolTipCtrl:: SetWindowTheme

Nastaví styl vizuálu okna s popisem tlačítka.

```
HRESULT SetWindowTheme(LPCWSTR pszSubAppName);
```

### <a name="parameters"></a>Parametry

*pszSubAppName*<br/>
Ukazatel na řetězec v kódování Unicode, který obsahuje vizuální styl, který se má nastavit.

### <a name="return-value"></a>Návratová hodnota

Návratová hodnota se nepoužívá.

### <a name="remarks"></a>Poznámky

Tato členská funkce emuluje funkce [TTM_SETWINDOWTHEME](/windows/win32/Controls/ttm-setwindowtheme) zprávy, jak je popsáno v Windows SDK.

##  <a name="update"></a>CToolTipCtrl:: Update

Vynutí překreslení aktuálního nástroje.

```
void Update();
```

##  <a name="updatetiptext"></a>CToolTipCtrl:: UpdateTipText

Aktualizuje text tipu nástroje pro nástroje tohoto ovládacího prvku.

```
void UpdateTipText(
    LPCTSTR lpszText,
    CWnd* pWnd,
    UINT_PTR nIDTool = 0);

void UpdateTipText(
    UINT nIDText,
    CWnd* pWnd,
    UINT_PTR nIDTool = 0);
```

### <a name="parameters"></a>Parametry

*lpszText*<br/>
Ukazatel na text pro nástroj.

*pWnd*<br/>
Ukazatel na okno, které obsahuje nástroj.

*nIDTool*<br/>
ID nástroje

*nIDText*<br/>
ID řetězcového prostředku, který obsahuje text pro nástroj.

## <a name="see-also"></a>Viz také

[CWnd – třída](../../mfc/reference/cwnd-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CToolBar – třída](../../mfc/reference/ctoolbar-class.md)
