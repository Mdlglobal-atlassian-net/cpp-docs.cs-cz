---
title: Chotkeyctrl – třída
ms.date: 11/04/2016
f1_keywords:
- CHotKeyCtrl
- AFXCMN/CHotKeyCtrl
- AFXCMN/CHotKeyCtrl::CHotKeyCtrl
- AFXCMN/CHotKeyCtrl::Create
- AFXCMN/CHotKeyCtrl::CreateEx
- AFXCMN/CHotKeyCtrl::GetHotKey
- AFXCMN/CHotKeyCtrl::GetHotKeyName
- AFXCMN/CHotKeyCtrl::GetKeyName
- AFXCMN/CHotKeyCtrl::SetHotKey
- AFXCMN/CHotKeyCtrl::SetRules
helpviewer_keywords:
- CHotKeyCtrl [MFC], CHotKeyCtrl
- CHotKeyCtrl [MFC], Create
- CHotKeyCtrl [MFC], CreateEx
- CHotKeyCtrl [MFC], GetHotKey
- CHotKeyCtrl [MFC], GetHotKeyName
- CHotKeyCtrl [MFC], GetKeyName
- CHotKeyCtrl [MFC], SetHotKey
- CHotKeyCtrl [MFC], SetRules
ms.assetid: 896f9766-0718-4f58-aab2-20325e118ca6
ms.openlocfilehash: 9a06f3bd8a8c5646f384c3f788518078b121bfe1
ms.sourcegitcommit: 975098222db3e8b297607cecaa1f504570a11799
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53178132"
---
# <a name="chotkeyctrl-class"></a>Chotkeyctrl – třída

Poskytuje funkce ovládacího prvku Windows běžné výměně klíče.

## <a name="syntax"></a>Syntaxe

```
class CHotKeyCtrl : public CWnd
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CHotKeyCtrl::CHotKeyCtrl](#chotkeyctrl)|Vytvoří `CHotKeyCtrl` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CHotKeyCtrl::Create](#create)|Vytvoří ovládací prvek výměně klíčů a připojí ho k `CHotKeyCtrl` objektu.|
|[CHotKeyCtrl::CreateEx](#createex)|Vytvoří ovládací prvek výměně klíčů zadaný rozšířené styly Windows a připojí ho k `CHotKeyCtrl` objektu.|
|[CHotKeyCtrl::GetHotKey](#gethotkey)|Načte virtuální klíče kódu a modifikátor příznaky výměně klíče z ovládacího prvku výměně klíče.|
|[CHotKeyCtrl::GetHotKeyName](#gethotkeyname)|Načte název klíče, místní znakové sady, přiřazené klávesové zkratky.|
|[CHotKeyCtrl::GetKeyName](#getkeyname)|Načte název klíče, místní znakové sady, přiřazené k zadané virtuální kód.|
|[CHotKeyCtrl::SetHotKey](#sethotkey)|Nastaví klávesové kombinace kláves pro ovládací prvek výměně klíče.|
|[CHotKeyCtrl::SetRules](#setrules)|Definuje výchozí kombinaci Modifikátor pro ovládací prvek výměně klíčů a neplatná kombinace.|

## <a name="remarks"></a>Poznámky

"Hot ovládacího prvku" je okno, které umožňuje uživateli vytvořit klávesové zkratky. "Klávesové zkratky" je může uživatel udělat rychle stisknout kombinaci kláves. (Například uživatel může vytvořit klávesové zkratky, která aktivuje daném okně a ukončí na něm na začátek pořadí.) Výměně klíčů ovládací prvek zobrazí možnosti uživatele a zajistí, že uživatel vybere platnou kombinaci kláves.

Tento ovládací prvek (a tedy `CHotKeyCtrl` třídy) je dostupná jenom pro programy spuštěné v rámci Windows 95/98 a Windows NT verze 3.51 a vyšší.

Když uživatel se rozhodl kombinaci kláves, můžete aplikaci načíst zadanou kombinaci kláves z ovládacího prvku a pomocí WM_SETHOTKEY nastavení klávesové zkratky v systému. Vždy, když uživatel stiskne klávesovou zkratku po tomto datu, z jakékoliv části systému, určená ve zprávě WM_SETHOTKEY okno obdrží zprávu WM_SYSCOMMAND zadání SC_HOTKEY. Tato zpráva aktivuje okně, které obdrží. Klávesové zkratky zůstane platný až do aplikace, která volá WM_SETHOTKEY ukončí.

Tento mechanismus je odlišný od výměně klíčů podporu, která závisí na zprávu WM_HOTKEY a Windows [RegisterHotKey](https://msdn.microsoft.com/library/windows/desktop/ms646309) a [UnregisterHotKey](/windows/desktop/api/winuser/nf-winuser-unregisterhotkey) funkce.

Další informace o používání `CHotKeyCtrl`, naleznete v tématu [ovládací prvky](../../mfc/controls-mfc.md) a [používání atributu CHotKeyCtrl](../../mfc/using-chotkeyctrl.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CHotKeyCtrl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxcmn.h

##  <a name="chotkeyctrl"></a>  CHotKeyCtrl::CHotKeyCtrl

Vytvoří `CHotKeyCtrl` objektu.

```
CHotKeyCtrl();
```

##  <a name="create"></a>  CHotKeyCtrl::Create

Vytvoří ovládací prvek výměně klíčů a připojí ho k `CHotKeyCtrl` objektu.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*dwStyle*<br/>
Určuje styl výměně klíčů ovládacího prvku. Použijte libovolnou kombinaci – styly ovládacího prvku. Zobrazit [– styly běžných ovládacích prvků](/windows/desktop/Controls/common-control-styles) v sadě Windows SDK pro další informace.

*Rect*<br/>
Určuje velikost a umístění výměně klíčů ovládacího prvku. Může se jednat buď [crect –](../../atl-mfc-shared/reference/crect-class.md) objektu nebo [Rect – struktura](/windows/desktop/api/windef/ns-windef-tagrect).

*pParentWnd*<br/>
Určuje, výměně klíčů nadřazené okno ovládacího prvku, obvykle [CDialog](../../mfc/reference/cdialog-class.md). Nesmí být NULL.

*nID*<br/>
Určuje ID výměně klíčů ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud se inicializace byla úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Můžete vytvořit `CHotKeyCtrl` objektu ve dvou krocích. Nejprve volat konstruktor a poté zavolejte `Create`, která vytvoří ovládací prvek výměně klíčů a připojí ho k `CHotKeyCtrl` objektu.

Pokud chcete použít rozšířené windows styly ovládacího prvku, zavolejte [CreateEx](#createex) místo `Create`.

##  <a name="createex"></a>  CHotKeyCtrl::CreateEx

Voláním této funkce vytvoření ovládacího prvku (podřízené okno) a přidružte jej k `CHotKeyCtrl` objektu.

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
Určuje styl výměně klíčů ovládacího prvku. Použijte libovolnou kombinaci – styly ovládacího prvku. Další informace najdete v tématu [– styly běžných ovládacích prvků](/windows/desktop/Controls/common-control-styles) v sadě Windows SDK.

*Rect*<br/>
Odkaz na [RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897) struktura popisující, velikost a umístění okna, které nelze v souřadnice klienta *pParentWnd*.

*pParentWnd*<br/>
Ukazatel na okno, který je nadřazeného ovládacího prvku.

*nID*<br/>
ID ovládacího prvku podřízené okno.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Použití `CreateEx` místo [vytvořit](#create) použít rozšířené styly Windows určené předponu rozšířeného stylu Windows **WS_EX_**.

##  <a name="gethotkey"></a>  CHotKeyCtrl::GetHotKey

Načte virtuální klíče kódu a modifikátor příznaky klávesové zkratky z ovládacího prvku výměně klíče.

```
DWORD GetHotKey() const;

void GetHotKey(
    WORD& wVirtualKeyCode,
    WORD& wModifiers) const;
```

### <a name="parameters"></a>Parametry

*wVirtualKeyCode*<br/>
[out] Virtuální kód klávesové zkratky. Seznam kódů standardní virtuální klíče najdete v tématu winuser.

*wModifiers*<br/>
[out] Bitová kombinace (nebo) příznaků, které označují modifikační klávesy v klávesové zkratky.

Modifikátor příznaky jsou následující:

|Příznak|Odpovídajícím klíčem|
|----------|-----------------------|
|HOTKEYF_ALT|ALT klávesa|
|HOTKEYF_CONTROL|Klávesa CTRL|
|HOTKEYF_EXT|Delší klíče|
|HOTKEYF_SHIFT|Klávesa SHIFT|

### <a name="return-value"></a>Návratová hodnota

V první přetížená metoda, která obsahuje virtuální klíče kódu a modifikátor příznaky DWORD. Nejnižší bajt nižší řád slova obsahuje virtuální kód, na vyšší řád bajt nižší řád slova obsahuje modifikátor příznaky a vyšší řád slova je nula.

### <a name="remarks"></a>Poznámky

Virtuální kód a modifikační klávesy společně definují klávesové zkratky.

##  <a name="gethotkeyname"></a>  CHotKeyCtrl::GetHotKeyName

Voláním této členské funkce, chcete-li získat lokalizovaný název klávesovou zkratku.

```
CString GetHotKeyName() const;
```

### <a name="return-value"></a>Návratová hodnota

Lokalizovaný název aktuálně vybraného klávesovou zkratku. Pokud neexistuje žádné vybrané klávesovou zkratku, `GetHotKeyName` vrátí prázdný řetězec.

### <a name="remarks"></a>Poznámky

Název, který tato členská funkce vrátí pochází z ovladače klávesnice. Můžete nainstalovat ovladač nelokalizovaný klávesnice v lokalizované verzi systému Windows a naopak.

##  <a name="getkeyname"></a>  CHotKeyCtrl::GetKeyName

Voláním této členské funkce, chcete-li získat lokalizovaný název klíče přiřazená zadaný kód virtuální klávesy.

```
static CString GetKeyName(
    UINT vk,
    BOOL fExtended);
```

### <a name="parameters"></a>Parametry

*Vk*<br/>
Virtuální kód.

*fExtended*<br/>
Pokud virtuální kód je delší klíče, hodnotu PRAVDA. v opačném případě FALSE.

### <a name="return-value"></a>Návratová hodnota

Lokalizovaný název klíče určené *vk* parametru. Pokud klíč nemá žádný název mapované `GetKeyName` vrátí prázdný řetězec.

### <a name="remarks"></a>Poznámky

Název klíče, který tato funkce vrací pochází z ovladače klávesnice, můžete nainstalovat ovladač nelokalizovaný klávesnice v lokalizované verzi systému Windows a naopak.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCControlLadenDialog#69](../../mfc/codesnippet/cpp/chotkeyctrl-class_1.cpp)]

##  <a name="sethotkey"></a>  CHotKeyCtrl::SetHotKey

Nastaví klávesové zkratky pro ovládací prvek výměně klíče.

```
void SetHotKey(
    WORD wVirtualKeyCode,
    WORD wModifiers);
```

### <a name="parameters"></a>Parametry

*wVirtualKeyCode*<br/>
[in] Virtuální kód klávesové zkratky. Seznam kódů standardní virtuální klíče najdete v tématu winuser.

*wModifiers*<br/>
[in] Bitová kombinace (nebo) příznaků, které označují modifikační klávesy v klávesové zkratky.

Modifikátor příznaky jsou následující:

|Příznak|Odpovídajícím klíčem|
|----------|-----------------------|
|HOTKEYF_ALT|ALT klávesa|
|HOTKEYF_CONTROL|Klávesa CTRL|
|HOTKEYF_EXT|Delší klíče|
|HOTKEYF_SHIFT|Klávesa SHIFT|

### <a name="remarks"></a>Poznámky

Virtuální kód a modifikační klávesy společně definují klávesové zkratky.

##  <a name="setrules"></a>  CHotKeyCtrl::SetRules

Voláním této funkce pro definování neplatná kombinace a kombinaci výchozí Modifikátor pro ovládací prvek výměně klíčů.

```
void SetRules(
    WORD wInvalidComb,
    WORD wModifiers);
```

### <a name="parameters"></a>Parametry

*wInvalidComb*<br/>
Pole příznaky, které určuje neplatný kombinace kláves. Může být kombinací následujícího:

- HKCOMB_A ALT

- HKCOMB_C CTRL

- HKCOMB_CA CTRL + ALT

- Bez úprav HKCOMB_NONE klíče

- HKCOMB_S SHIFT

- HKCOMB_SA SHIFT + ALT

- HKCOMB_SC SHIFT + CTRL

- HKCOMB_SCA SHIFT + CTRL + ALT

*wModifiers*<br/>
Pole příznaky, které určuje kombinaci kláves používat, když uživatel zadá neplatnou kombinaci. Další informace o příznacích modifikátor najdete v tématu [GetHotKey](#gethotkey).

### <a name="remarks"></a>Poznámky

Když uživatel zadá neplatnou kombinaci kláves, jak jsou definovány pomocí příznaků zadaných ve *wInvalidComb*, systém použije operátor OR zkombinovat klíče zadané uživatelem pomocí příznaků zadaných ve *wModifiers*. Výsledný kombinace kláves je převést na řetězec a následně se zobrazí v ovládacím prvku výměně klíče.

## <a name="see-also"></a>Viz také

[CWnd – třída](../../mfc/reference/cwnd-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)

