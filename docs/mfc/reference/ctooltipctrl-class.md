---
title: Třída CToolTipCtrl
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
ms.openlocfilehash: 53a5a5b6871680f9758d140174dcceae6c53f568
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752195"
---
# <a name="ctooltipctrl-class"></a>Třída CToolTipCtrl

Zapouzdřuje funkce "ovládacího prvku špičky nástroje", malé rozbalovací okno, které zobrazuje jeden řádek textu popisující účel nástroje v aplikaci.

## <a name="syntax"></a>Syntaxe

```
class CToolTipCtrl : public CWnd
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CToolTipCtrl::CToolTipCtrl](#ctooltipctrl)|Vytvoří `CToolTipCtrl` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CToolTipCtrl::Aktivovat](#activate)|Aktivuje a deaktivuje ovládání špičky nástroje.|
|[CToolTipCtrl::AddTool](#addtool)|Zaregistruje nástroj s ovládáním špičky nástroje.|
|[CToolTipCtrl::AdjustRect](#adjustrect)|Převede mezi obdélníkzobrazení textu ovládacího prvku špičky nástroje a jeho obdélník okna.|
|[CToolTipCtrl::Vytvořit](#create)|Vytvoří ovládací prvek špičky nástroje `CToolTipCtrl` a připojí jej k objektu.|
|[CToolTipCtrl::CreateEx](#createex)|Vytvoří ovládací prvek špičky nástroje se zadanými `CToolTipCtrl` rozšířenými styly systému Windows a připojí jej k objektu.|
|[CToolTipCtrl::DelTool](#deltool)|Odstraní nástroj z ovládacího prvku špičky nástroje.|
|[CToolTipCtrl::GetBubbleSize](#getbubblesize)|Načte velikost špičky nástroje.|
|[CToolTipCtrl::GetCurrentTool](#getcurrenttool)|Načte informace, například velikost, umístění a text okna popisku, které zobrazuje aktuální ovládací prvek popisku.|
|[CToolTipCtrl::GetDelayTime](#getdelaytime)|Načte počáteční, automaticky otevírané a reshow doby trvání, které jsou aktuálně nastaveny pro ovládací prvek špičky nástroje.|
|[CToolTipCtrl::GetMargin](#getmargin)|Načte horní, levý, dolní a pravý okraj, které jsou nastaveny pro okno tip nástroje.|
|[CToolTipCtrl::GetMaxTipWidth](#getmaxtipwidth)|Načte maximální šířku okna tipnástroje.|
|[CToolTipCtrl::GetText](#gettext)|Načte text, který ovládací prvek špičky nástroje udržuje pro nástroj.|
|[CToolTipCtrl::GetTipBkColor](#gettipbkcolor)|Načte barvu pozadí v okně tipu nástroje.|
|[CToolTipCtrl::GetTipTextColor](#gettiptextcolor)|Načte barvu textu v okně tipu nástroje.|
|[CToolTipCtrl::GetTitle](#gettitle)|Načte název aktuálního ovládacího prvku popisku.|
|[CToolTipCtrl::GetToolCount](#gettoolcount)|Načte počet nástrojů udržovaných ovládacím prvkem špičky nástroje.|
|[CToolTipCtrl::GetToolInfo](#gettoolinfo)|Načte informace, které ovládací prvek špičky nástroje udržuje o nástroji.|
|[CToolTipCtrl::HitTest](#hittest)|Testuje bod k určení, zda je v ohraničující obdélník daného nástroje. Pokud ano, načte informace o nástroji.|
|[CToolTipCtrl::Pop](#pop)|Odstraní zobrazené okno tipu nástroje ze zobrazení.|
|[CToolTipCtrl::Popup](#popup)|Způsobí, že aktuální ovládací prvek popisek se zobrazí na souřadnicích poslední zprávy myši.|
|[CToolTipCtrl::Událost relayeventu](#relayevent)|Předá zprávu myši ovládacímu prvku tip nástroje pro zpracování.|
|[CToolTipCtrl::SetDelayTime](#setdelaytime)|Nastaví počáteční, automaticky otevírané a re-show doby trvání ovládacího prvku špičky nástroje.|
|[CToolTipCtrl::SetMargin](#setmargin)|Nastaví horní, levý, dolní a pravý okraj okna tipu nástroje.|
|[CToolTipCtrl::SetMaxTipWidth](#setmaxtipwidth)|Nastaví maximální šířku okna tipu nástroje.|
|[CToolTipCtrl::SetTipBkColor](#settipbkcolor)|Nastaví barvu pozadí v okně tipu nástroje.|
|[CToolTipCtrl::SetTipTextColor](#settiptextcolor)|Nastaví barvu textu v okně tipu nástroje.|
|[CToolTipCtrl::SetTitle](#settitle)|Přidá standardní ikonu a název řetězce do tipu nástroje.|
|[CToolTipCtrl::SetToolInfo](#settoolinfo)|Nastaví informace, které pro nástroj udržuje špička nástroje.|
|[CToolTipCtrl::SetToolRect](#settoolrect)|Nastaví nový ohraničovací obdélník pro nástroj.|
|[CToolTipCtrl::SetWindowTheme](#setwindowtheme)|Nastaví vizuální styl okna tipu nástroje.|
|[CToolTipCtrl::Aktualizovat](#update)|Vynutí překreslit aktuální nástroj.|
|[CToolTipCtrl::UpdateTipText](#updatetiptext)|Nastaví text tipu nástroje.|

## <a name="remarks"></a>Poznámky

"Nástroj" je buď okno, například podřízené okno nebo ovládací prvek, nebo obdélníková oblast definovaná aplikací v klientské oblasti okna. Tip nástroje je většinou skrytý a zobrazuje se pouze v případě, že uživatel umístí kurzor na nástroj a ponechá jej tam přibližně na půl sekundy. Tip nástroje se zobrazí v blízkosti kurzoru a zmizí, když uživatel klepne na tlačítko myši nebo přesune kurzor mimo nástroj.

`CToolTipCtrl`poskytuje funkce pro řízení počátečního času a doby trvání špičky nástroje, šířky okrajů obklopujících text tipu nástroje, šířku samotného okna špičky nástroje a barvu pozadí a textu špičky nástroje. Jeden ovládací prvek špičky nástroje může poskytnout informace pro více než jeden nástroj.

Třída `CToolTipCtrl` poskytuje funkce ovládacího prvku windows společné ho nástroje tip. Tento ovládací prvek `CToolTipCtrl` (a tedy třída) je k dispozici pouze pro programy spuštěné v systémech Windows 95/98 a Windows NT verze 3.51 a novější.

Další informace o povolení tipů nástrojů naleznete [v tématu Tipy nástrojů v systému Windows, které nejsou odvozeny z CFrameWnd](../../mfc/tool-tips-in-windows-not-derived-from-cframewnd.md).

Další informace o `CToolTipCtrl`použití naleznete v [tématech Ovládací prvky](../../mfc/controls-mfc.md) a [Použití kláves CToolTipCtrl](../../mfc/using-ctooltipctrl.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

`CToolTipCtrl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxcmn.h

## <a name="ctooltipctrlactivate"></a><a name="activate"></a>CToolTipCtrl::Aktivovat

Voláním této funkce aktivujte nebo deaktivujte ovládací prvek špičky nástroje.

```cpp
void Activate(BOOL bActivate);
```

### <a name="parameters"></a>Parametry

*bAktivovat*<br/>
Určuje, zda má být ovládací prvek špičky nástroje aktivován nebo deaktivován.

### <a name="remarks"></a>Poznámky

Pokud *je funkce bActivate* TRUE, ovládací prvek se aktivuje. pokud false, je deaktivován.

Když je ovládací prvek špičky nástroje aktivní, zobrazí se informace o tipu nástroje, když je kurzor na nástroji, který je registrován u ovládacího prvku; pokud je neaktivní, informace o tipu nástroje se nezobrazí, i když je kurzor na nástroji.

### <a name="example"></a>Příklad

  Viz příklad [cpropertysheet::GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).

## <a name="ctooltipctrladdtool"></a><a name="addtool"></a>CToolTipCtrl::AddTool

Zaregistruje nástroj s ovládáním špičky nástroje.

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
ID prostředku řetězce, který obsahuje text nástroje.

*lpRectTool*<br/>
Ukazatel na strukturu [RECT](/windows/win32/api/windef/ns-windef-rect) obsahující souřadnice ohraničujícího obdélníku nástroje. Souřadnice jsou relativní k levému hornímu rohu klientské oblasti okna identifikovaného *pomocí pWnd*.

*nIDTool*<br/>
ID nástroje.

*lpszText*<br/>
Ukazatel na text nástroje. Pokud tento parametr obsahuje hodnotu LPSTR_TEXTCALLBACK, TTN_NEEDTEXT oznámení přejděte na nadřazené okno, které *pWnd* odkazuje na.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Parametry *lpRectTool* a *nIDTool* musí být platné, nebo pokud je *lpRectTool* NULL, *nIDTool* musí být 0.

Ovládací prvek špičky nástroje může být přidružen k více než jednomu nástroji. Voláním této funkce zaregistrujte nástroj pomocí ovládacího prvku špičky nástroje, aby se informace uložené v tipu nástroje zobrazily, když je kurzor na nástroji.

> [!NOTE]
> Špičku nástroje nelze nastavit na `AddTool`statický ovládací prvek pomocí aplikace .

### <a name="example"></a>Příklad

  Viz příklad [cpropertysheet::GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).

## <a name="ctooltipctrladjustrect"></a><a name="adjustrect"></a>CToolTipCtrl::AdjustRect

Převede mezi obdélník zobrazení textu ovládacího prvku popisku a obdélník okna.

```
BOOL AdjustRect(
    LPRECT lprc,
    BOOL bLarger = TRUE);
```

### <a name="parameters"></a>Parametry

*lprc*<br/>
Ukazatel na [rect](/windows/win32/api/windef/ns-windef-rect) strukturu, která obsahuje obdélník okna tip nástroje nebo obdélník zobrazení textu.

*bVětší*<br/>
Pokud TRUE, *lprc* se používá k určení obdélníku zobrazení textu a obdrží odpovídající obdélník okna. Pokud FALSE, *lprc* se používá k určení obdélníku okna a obdrží odpovídající obdélník zobrazení textu.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je obdélník úspěšně upraven; jinak 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce vypočítá obdélník zobrazení textu ovládacího prvku špičky nástroje z obdélníku okna nebo obdélníkokna tipu nástroje potřebný k zobrazení zadaného obdélníku zobrazení textu.

Tato členská funkce implementuje chování [zprávy](/windows/win32/Controls/ttm-adjustrect)Win32 TTM_ADJUSTRECT , jak je popsáno v sadě Windows SDK.

## <a name="ctooltipctrlcreate"></a><a name="create"></a>CToolTipCtrl::Vytvořit

Vytvoří ovládací prvek špičky nástroje `CToolTipCtrl` a připojí jej k objektu.

```
virtual BOOL Create(CWnd* pParentWnd, DWORD dwStyle = 0);
```

### <a name="parameters"></a>Parametry

*pParentWnd*<br/>
Určuje nadřazené okno ovládacího `CDialog`prvku špičky nástroje, obvykle . Nesmí být null.

*dwStyl*<br/>
Určuje styl ovládacího prvku špičky nástroje. Další informace naleznete v části **Poznámky.**

### <a name="return-value"></a>Návratová hodnota

Nenulová, `CToolTipCtrl` pokud je objekt úspěšně vytvořen; jinak 0.

### <a name="remarks"></a>Poznámky

Můžete vytvořit `CToolTipCtrl` ve dvou krocích. Nejprve zavolejte konstruktoru `CToolTipCtrl` k vytvoření `Create` objektu a potom voláním vytvořte ovládací prvek špičky nástroje a připojte jej k objektu. `CToolTipCtrl`

Parametr *dwStyle* může být libovolná kombinace [stylů oken](../../mfc/reference/styles-used-by-mfc.md#window-styles). Kromě toho má ovládací prvek špičky nástroje dva styly specifické pro třídu: TTS_ALWAYSTIP a TTS_NOPREFIX.

|Styl|Význam|
|-----------|-------------|
|TTS_ALWAYSTIP|Určuje, že tip nástroje se zobrazí, když je kurzor na nástroji, bez ohledu na to, zda je okno vlastníka ovládacího prvku špičky nástroje aktivní nebo neaktivní. Bez tohoto stylu se ovládací prvek špičky nástroje zobrazí, když je aktivní okno vlastníka nástroje, ale ne, když je neaktivní.|
|TTS_NOPREFIX|Tento styl zabraňuje systému odizolování znaku ampersand (&) z řetězce. Pokud ovládací prvek špičky nástroje nemá TTS_NOPREFIX stylu, systém automaticky proužkuje znaky ampersandu, což aplikaci umožňuje používat stejný řetězec jako položka nabídky i jako text v ovládacím prvku tip nástroje.|

Ovládací prvek tip nástroje má WS_POPUP a WS_EX_TOOLWINDOW styly oken, bez ohledu na to, zda je zadáte při vytváření ovládacího prvku.

Chcete-li vytvořit ovládací prvek tip nástroje s rozšířenými styly `Create`oken, zavolejte [CToolTipCtrl::CreateEx](#createex) místo .

### <a name="example"></a>Příklad

  Viz příklad [cpropertysheet::GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).

## <a name="ctooltipctrlcreateex"></a><a name="createex"></a>CToolTipCtrl::CreateEx

Vytvoří ovládací prvek (podřízené okno) `CToolTipCtrl` a přidruží jej k objektu.

```
virtual BOOL CreateEx(
    CWnd* pParentWnd,
    DWORD dwStyle = 0,
    DWORD dwStyleEx = 0);
```

### <a name="parameters"></a>Parametry

*pParentWnd*<br/>
Ukazatel na okno, které je nadřazený ovládací prvek.

*dwStyl*<br/>
Určuje styl ovládacího prvku špičky nástroje. Další informace naleznete v části **Poznámky** v části [Vytvořit.](#create)

*dwStyleEx*<br/>
Určuje rozšířený styl vytvářeného ovládacího prvku. Seznam rozšířených stylů systému Windows naleznete v parametru *dwExStyle* pro [createwindowex](/windows/win32/api/winuser/nf-winuser-createwindowexw) v sadě Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná jinak 0.

### <a name="remarks"></a>Poznámky

Místo `CreateEx` toho `Create` použijte rozšířené styly systému Windows určené **předmluvou**rozšířeného stylu systému Windows WS_EX_ .

## <a name="ctooltipctrlctooltipctrl"></a><a name="ctooltipctrl"></a>CToolTipCtrl::CToolTipCtrl

Vytvoří `CToolTipCtrl` objekt.

```
CToolTipCtrl();
```

### <a name="remarks"></a>Poznámky

Musíte volat `Create` po vytvoření objektu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCControlLadenDialog#74](../../mfc/codesnippet/cpp/ctooltipctrl-class_1.h)]

## <a name="ctooltipctrldeltool"></a><a name="deltool"></a>CToolTipCtrl::DelTool

Odstraní nástroj určený *pWnd* a *nIDTool* z kolekce nástrojů podporovaných ovládáním hrotu nástroje.

```cpp
void DelTool(
    CWnd* pWnd,
    UINT_PTR nIDTool = 0);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Ukazatel na okno, které obsahuje nástroj.

*nIDTool*<br/>
ID nástroje.

## <a name="ctooltipctrlgetbubblesize"></a><a name="getbubblesize"></a>CToolTipCtrl::GetBubbleSize

Načte velikost špičky nástroje.

```
CSize GetBubbleSize(LPTOOLINFO lpToolInfo) const;
```

### <a name="parameters"></a>Parametry

*lpToolInfo*<br/>
Ukazatel na strukturu [TOOLINFO](/windows/win32/api/commctrl/ns-commctrl-tttoolinfoa) tipu nástroje.

### <a name="return-value"></a>Návratová hodnota

Velikost hrotu nástroje.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování [zprávy](/windows/win32/Controls/ttm-getbubblesize)Win32 TTM_GETBUBBLESIZE , jak je popsáno v sadě Windows SDK.

## <a name="ctooltipctrlgetcurrenttool"></a><a name="getcurrenttool"></a>CToolTipCtrl::GetCurrentTool

Načte informace, například velikost, umístění a text okna popisku zobrazeného aktuálním ovládacím prvkem popisku.

```
BOOL GetCurrentTool(LPTOOLINFO lpToolInfo) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*lpToolInfo*|[out] Ukazatel na strukturu [TOOLINFO,](/windows/win32/api/commctrl/ns-commctrl-tttoolinfoa) která přijímá informace o aktuálním okně popisku.|

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud jsou informace načteny úspěšně; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

Tato metoda odešle [zprávu TTM_GETCURRENTTOOL,](/windows/win32/Controls/ttm-getcurrenttool) která je popsána v sadě Windows SDK.

### <a name="example"></a>Příklad

Následující příklad kódu načte informace o aktuálním okně popisku.

[!code-cpp[NVC_MFC_CToolBarCtrl_s1#6](../../mfc/reference/codesnippet/cpp/ctooltipctrl-class_2.cpp)]

## <a name="ctooltipctrlgetdelaytime"></a><a name="getdelaytime"></a>CToolTipCtrl::GetDelayTime

Načte počáteční, automaticky otevírané a reshow doby trvání aktuálně nastavené pro ovládací prvek špičky nástroje.

```
int GetDelayTime(DWORD dwDuration) const;
```

### <a name="parameters"></a>Parametry

*dwDuration*<br/>
Příznak, který určuje, která hodnota doby trvání bude načtena. Tento parametr může být jedna z následujících hodnot:

- TTDT_AUTOPOP Načíst dobu, po kterou zůstane okno tipu nástroje viditelné, pokud je ukazatel v ohraničovacím obdélníku nástroje nehybný.

- TTDT_INITIAL Načíst dobu, po kterou musí ukazatel zůstat nehybný v ohraničovacím obdélníku nástroje, než se zobrazí okno tipu nástroje.

- TTDT_RESHOW Načtěte dobu, po kterou se při pohybu ukazatele z jednoho nástroje do druhého zobrazí následující okna s tipem nástroje.

### <a name="return-value"></a>Návratová hodnota

Zadaná doba zpoždění v milisekundách

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování [zprávy](/windows/win32/Controls/ttm-getdelaytime)Win32 TTM_GETDELAYTIME , jak je popsáno v sadě Windows SDK.

## <a name="ctooltipctrlgetmargin"></a><a name="getmargin"></a>CToolTipCtrl::GetMargin

Načte horní, levý, dolní a pravý okraj nastavený pro okno tipu nástroje.

```cpp
void GetMargin(LPRECT lprc) const;
```

### <a name="parameters"></a>Parametry

*lprc*<br/>
Adresa `RECT` struktury, která obdrží informace o marži. Členy [rect](/windows/win32/api/windef/ns-windef-rect) struktury nedefinují ohraničující obdélník. Pro účely této zprávy jsou členové struktury interpretováni takto:

|Člen|Reprezentace|
|------------|--------------------|
|`top`|Vzdálenost mezi horním okrajem a horním textem špičky nástroje v obrazových bodech.|
|`left`|Vzdálenost mezi levým okrajem a levým koncem textu špičky v obrazových bodech.|
|`bottom`|Vzdálenost mezi dolním okrajem a dolním okrajem textu špičky v obrazových bodech.|
|`right`|Vzdálenost mezi pravým okrajem a pravým koncem textu špičky v obrazových bodech.|

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování [zprávy](/windows/win32/Controls/ttm-getmargin)Win32 TTM_GETMARGIN , jak je popsáno v sadě Windows SDK.

## <a name="ctooltipctrlgetmaxtipwidth"></a><a name="getmaxtipwidth"></a>CToolTipCtrl::GetMaxTipWidth

Načte maximální šířku okna tipnástroje.

```
int GetMaxTipWidth() const;
```

### <a name="return-value"></a>Návratová hodnota

Maximální šířka okna tipnástroje.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování [TTM_GETMAXTIPWIDTH](/windows/win32/Controls/ttm-getmaxtipwidth)zprávy Win32 , jak je popsáno v sadě Windows SDK.

## <a name="ctooltipctrlgettext"></a><a name="gettext"></a>CToolTipCtrl::GetText

Načte text, který ovládací prvek špičky nástroje udržuje pro nástroj.

```cpp
void GetText(
    CString& str,
    CWnd* pWnd,
    UINT_PTR nIDTool = 0) const;
```

### <a name="parameters"></a>Parametry

*Str*<br/>
Odkaz na `CString` objekt, který přijímá text nástroje.

*pWnd*<br/>
Ukazatel na okno, které obsahuje nástroj.

*nIDTool*<br/>
ID nástroje.

### <a name="remarks"></a>Poznámky

Parametry *pWnd* a *nIDTool* identifikují nástroj. Pokud byl tento nástroj dříve zaregistrován u ovládacího `CToolTipCtrl::AddTool`prvku špičky nástroje prostřednictvím předchozího volání , je objektu, na který odkazuje parametr *str,* přiřazen text nástroje.

## <a name="ctooltipctrlgettipbkcolor"></a><a name="gettipbkcolor"></a>CToolTipCtrl::GetTipBkColor

Načte barvu pozadí v okně tipu nástroje.

```
COLORREF GetTipBkColor() const;
```

### <a name="return-value"></a>Návratová hodnota

[Colorref](/windows/win32/gdi/colorref) hodnota, která představuje barvu pozadí.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování [zprávy](/windows/win32/Controls/ttm-gettipbkcolor)Win32 TTM_GETTIPBKCOLOR , jak je popsáno v sadě Windows SDK.

## <a name="ctooltipctrlgettiptextcolor"></a><a name="gettiptextcolor"></a>CToolTipCtrl::GetTipTextColor

Načte barvu textu v okně tipu nástroje.

```
COLORREF GetTipTextColor() const;
```

### <a name="return-value"></a>Návratová hodnota

[Colorref](/windows/win32/gdi/colorref) hodnota, která představuje barvu textu.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování [zprávy](/windows/win32/Controls/ttm-gettiptextcolor)Win32 TTM_GETTIPTEXTCOLOR , jak je popsáno v sadě Windows SDK.

## <a name="ctooltipctrlgettitle"></a><a name="gettitle"></a>CToolTipCtrl::GetTitle

Načte název aktuálního ovládacího prvku popisku.

```cpp
void GetTitle(PTTGETTITLE pttgt) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*pttgt*|[out] Ukazatel na strukturu [TTGETTITLE,](/windows/win32/api/commctrl/ns-commctrl-ttgettitle) která obsahuje informace o ovládacím prvku popis. Když tato metoda vrátí, *pszTitle* člen [TTGETTITLE](/windows/win32/api/commctrl/ns-commctrl-ttgettitle) struktury odkazuje na text titulu.|

### <a name="remarks"></a>Poznámky

Tato metoda odešle [zprávu TTM_GETTITLE,](/windows/win32/Controls/ttm-gettitle) která je popsána v sadě Windows SDK.

## <a name="ctooltipctrlgettoolcount"></a><a name="gettoolcount"></a>CToolTipCtrl::GetToolCount

Načte počet nástrojů registrovaných pomocí ovládacího prvku špičky nástroje.

```
int GetToolCount() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet nástrojů registrovaných pomocí ovládacího prvku špičky nástroje.

## <a name="ctooltipctrlgettoolinfo"></a><a name="gettoolinfo"></a>CToolTipCtrl::GetToolInfo

Načte informace, které ovládací prvek špičky nástroje udržuje o nástroji.

```
BOOL GetToolInfo(
    CToolInfo& ToolInfo,
    CWnd* pWnd,
    UINT_PTR nIDTool = 0) const;
```

### <a name="parameters"></a>Parametry

*Informace o nástroji*<br/>
Odkaz na `TOOLINFO` objekt, který přijímá text nástroje.

*pWnd*<br/>
Ukazatel na okno, které obsahuje nástroj.

*nIDTool*<br/>
ID nástroje.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

A `hwnd` `uId` členové [toolinfo](/windows/win32/api/commctrl/ns-commctrl-tttoolinfoa) struktury odkazuje *CToolInfo* identifikovat nástroj. Pokud byl tento nástroj zaregistrován u ovládacího `AddTool`prvku `TOOLINFO` špičky nástroje prostřednictvím předchozího volání , je struktura vyplněna informacemi o nástroji.

## <a name="ctooltipctrlhittest"></a><a name="hittest"></a>CToolTipCtrl::HitTest

Testuje bod k určení, zda je v ohraničujícíobdélník daného nástroje a pokud ano, načíst informace o nástroji.

```
BOOL HitTest(
    CWnd* pWnd,
    CPoint pt,
    LPTOOLINFO lpToolInfo) const;
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Ukazatel na okno, které obsahuje nástroj.

*Pt*<br/>
Ukazatel na `CPoint` objekt obsahující souřadnice bodu, který má být testován.

*lpToolInfo*<br/>
Ukazatel na [toolinfo](/windows/win32/api/commctrl/ns-commctrl-tttoolinfoa) strukturu, která obsahuje informace o nástroji.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je bod určený informacemi o testu přístupů v ohraničujícím obdélníku nástroje; jinak 0.

### <a name="remarks"></a>Poznámky

Pokud tato funkce vrátí nenulovou hodnotu, struktura, na kterou odkazová *hodnota LpToolInfo* ukazuje, je vyplněna informacemi o nástroji, v jehož obdélníku leží bod.

Struktura `TTHITTESTINFO` je definována takto:

```cpp
typedef struct _TT_HITTESTINFO { // tthti
    HWND hwnd;   // handle of tool or window with tool
    POINT pt;    // client coordinates of point to test
    TOOLINFO ti; // receives information about the tool
} TTHITTESTINFO, FAR * LPHITTESTINFO;
```

- `hwnd`

   Určuje úchyt nástroje.

- `pt`

   Určuje souřadnice bodu, pokud je bod v ohraničovacím obdélníku nástroje.

- `ti`

   Informace o nástroji. Další informace o `TOOLINFO` struktuře naleznete v tématu [CToolTipCtrl::GetToolInfo](#gettoolinfo).

## <a name="ctooltipctrlpop"></a><a name="pop"></a>CToolTipCtrl::Pop

Odebere ze zobrazení zobrazené okno tipu nástroje.

```cpp
void Pop();
```

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování [TTM_POP](/windows/win32/Controls/ttm-pop)zprávy Win32 , jak je popsáno v sadě Windows SDK.

## <a name="ctooltipctrlpopup"></a><a name="popup"></a>CToolTipCtrl::Popup

Způsobí, že aktuální ovládací prvek popisek se zobrazí na souřadnicích poslední zprávy myši.

```cpp
void Popup();
```

### <a name="remarks"></a>Poznámky

Tato metoda odešle [zprávu TTM_POPUP,](/windows/win32/Controls/ttm-popup) která je popsána v sadě Windows SDK.

### <a name="example"></a>Příklad

Následující příklad kódu zobrazí okno s popisem.

[!code-cpp[NVC_MFC_CToolBarCtrl_s1#7](../../mfc/reference/codesnippet/cpp/ctooltipctrl-class_3.cpp)]

## <a name="ctooltipctrlrelayevent"></a><a name="relayevent"></a>CToolTipCtrl::Událost relayeventu

Předá zprávu myši ovládacímu prvku tip nástroje pro zpracování.

```cpp
void RelayEvent(LPMSG lpMsg);
```

### <a name="parameters"></a>Parametry

*lpMsg*<br/>
Ukazatel na strukturu [MSG,](/windows/win32/api/winuser/ns-winuser-msg) která obsahuje zprávu k přenosu.

### <a name="remarks"></a>Poznámky

Ovládací prvek tip nástroje zpracovává pouze následující zprávy, `RelayEvent`které jsou do něj odesílány :

|WM_LBUTTONDOWN|WM_MOUSEMOVE|
|---------------------|-------------------|
|WM_LBUTTONUP|WM_RBUTTONDOWN|
|WM_MBUTTONDOWN|WM_RBUTTONUP|
|WM_MBUTTONUP||

### <a name="example"></a>Příklad

  Viz příklad [cpropertysheet::GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).

## <a name="ctooltipctrlsetdelaytime"></a><a name="setdelaytime"></a>CToolTipCtrl::SetDelayTime

Nastaví dobu zpoždění pro ovládání špičky nástroje.

```cpp
void SetDelayTime(UINT nDelay);

void SetDelayTime(
    DWORD dwDuration,
    int iTime);
```

### <a name="parameters"></a>Parametry

*nZpoždění*<br/>
Určuje novou dobu zpoždění v milisekundách.

*dwDuration*<br/>
Příznak, který určuje, která hodnota doby trvání bude načtena. Viz [CToolTipCtrl::GetDelayTime](#getdelaytime) popis platných hodnot.

*iTime*<br/>
Zadaná doba zpoždění v milisekundách.

### <a name="remarks"></a>Poznámky

Doba zpoždění je doba, po kterou musí kurzor zůstat na nástroji, než se zobrazí okno tipu nástroje. Výchozí doba zpoždění je 500 milisekund.

## <a name="ctooltipctrlsetmargin"></a><a name="setmargin"></a>CToolTipCtrl::SetMargin

Nastaví horní, levý, dolní a pravý okraj okna tipu nástroje.

```cpp
void SetMargin(LPRECT lprc);
```

### <a name="parameters"></a>Parametry

*lprc*<br/>
Adresa `RECT` struktury, která obsahuje informace o okraji, které mají být nastaveny. Členy `RECT` struktury nedefinují ohraničující obdélník. Viz [CToolTipCtrl::GetMargin](#getmargin) popis informací o okraji.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování [TTM_SETMARGIN](/windows/win32/Controls/ttm-setmargin)zprávy Win32 , jak je popsáno v sadě Windows SDK.

## <a name="ctooltipctrlsetmaxtipwidth"></a><a name="setmaxtipwidth"></a>CToolTipCtrl::SetMaxTipWidth

Nastaví maximální šířku okna tipu nástroje.

```
int SetMaxTipWidth(int iWidth);
```

### <a name="parameters"></a>Parametry

*iŠířka*<br/>
Maximální šířka okna tipu nástroje, která má být nastavena.

### <a name="return-value"></a>Návratová hodnota

Předchozí maximální šířka špičky.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování [zprávy](/windows/win32/Controls/ttm-setmaxtipwidth)Win32 TTM_SETMAXTIPWIDTH , jak je popsáno v sadě Windows SDK.

## <a name="ctooltipctrlsettipbkcolor"></a><a name="settipbkcolor"></a>CToolTipCtrl::SetTipBkColor

Nastaví barvu pozadí v okně tipu nástroje.

```cpp
void SetTipBkColor(COLORREF clr);
```

### <a name="parameters"></a>Parametry

*Clr*<br/>
Nová barva pozadí.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování [TTM_SETTIPBKCOLOR](/windows/win32/Controls/ttm-settipbkcolor)zprávy Win32 , jak je popsáno v sadě Windows SDK.

## <a name="ctooltipctrlsettiptextcolor"></a><a name="settiptextcolor"></a>CToolTipCtrl::SetTipTextColor

Nastaví barvu textu v okně tipu nástroje.

```cpp
void SetTipTextColor(COLORREF clr);
```

### <a name="parameters"></a>Parametry

*Clr*<br/>
Nová barva textu.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování [zprávy](/windows/win32/Controls/ttm-settiptextcolor)Win32 TTM_SETTIPTEXTCOLOR , jak je popsáno v sadě Windows SDK.

## <a name="ctooltipctrlsettitle"></a><a name="settitle"></a>CToolTipCtrl::SetTitle

Přidá standardní ikonu a název řetězce do tipu nástroje.

```
BOOL SetTitle(
    UINT uIcon,
    LPCTSTR lpstrTitle);
```

### <a name="parameters"></a>Parametry

*uIkona*<br/>
Viz *ikona* v [TTM_SETTITLE](/windows/win32/Controls/ttm-settitle) v sadě Windows SDK.

*lpstrTitle*<br/>
Ukazatel na řetězec nadpisu.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování [zprávy](/windows/win32/Controls/ttm-settitle)Win32 TTM_SETTITLE , jak je popsáno v sadě Windows SDK.

## <a name="ctooltipctrlsettoolinfo"></a><a name="settoolinfo"></a>CToolTipCtrl::SetToolInfo

Nastaví informace, které pro nástroj udržuje špička nástroje.

```cpp
void SetToolInfo(LPTOOLINFO lpToolInfo);
```

### <a name="parameters"></a>Parametry

*lpToolInfo*<br/>
Ukazatel na strukturu [TOOLINFO,](/windows/win32/api/commctrl/ns-commctrl-tttoolinfoa) která určuje informace, které mají být nastaveny.

## <a name="ctooltipctrlsettoolrect"></a><a name="settoolrect"></a>CToolTipCtrl::SetToolRect

Nastaví nový ohraničovací obdélník pro nástroj.

```cpp
void SetToolRect(
    CWnd* pWnd,
    UINT_PTR nIDTool,
    LPCRECT lpRect);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Ukazatel na okno, které obsahuje nástroj.

*nIDTool*<br/>
ID nástroje.

*lpRect*<br/>
Ukazatel na [rect](/windows/win32/api/windef/ns-windef-rect) strukturu určující nový ohraničující obdélník.

## <a name="ctooltipctrlsetwindowtheme"></a><a name="setwindowtheme"></a>CToolTipCtrl::SetWindowTheme

Nastaví vizuální styl okna tipu nástroje.

```
HRESULT SetWindowTheme(LPCWSTR pszSubAppName);
```

### <a name="parameters"></a>Parametry

*pszSubAppName*<br/>
Ukazatel na řetězec Unicode, který obsahuje vizuální styl, který chcete nastavit.

### <a name="return-value"></a>Návratová hodnota

Vrácená hodnota se nepoužívá.

### <a name="remarks"></a>Poznámky

Tato členská funkce emuluje funkce [zprávy TTM_SETWINDOWTHEME,](/windows/win32/Controls/ttm-setwindowtheme) jak je popsáno v sadě Windows SDK.

## <a name="ctooltipctrlupdate"></a><a name="update"></a>CToolTipCtrl::Aktualizovat

Vynutí překreslit aktuální nástroj.

```cpp
void Update();
```

## <a name="ctooltipctrlupdatetiptext"></a><a name="updatetiptext"></a>CToolTipCtrl::UpdateTipText

Aktualizuje text tipu nástroje pro nástroje tohoto ovládacího prvku.

```cpp
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
Ukazatel na text nástroje.

*pWnd*<br/>
Ukazatel na okno, které obsahuje nástroj.

*nIDTool*<br/>
ID nástroje.

*nIDText*<br/>
ID prostředku řetězce, který obsahuje text nástroje.

## <a name="see-also"></a>Viz také

[CWnd – třída](../../mfc/reference/cwnd-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CToolBar – třída](../../mfc/reference/ctoolbar-class.md)
