---
title: CHotKeyCtrl – třída
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
ms.openlocfilehash: a79cc0ab2c01633f96430477aa536a60385461e9
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81750810"
---
# <a name="chotkeyctrl-class"></a>CHotKeyCtrl – třída

Poskytuje funkce společného ovládacího prvku klávesové zkratky systému Windows.

## <a name="syntax"></a>Syntaxe

```
class CHotKeyCtrl : public CWnd
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CHotKeyCtrl::CHotKeyCtrl](#chotkeyctrl)|Vytvoří `CHotKeyCtrl` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CHotKeyCtrl::Vytvořit](#create)|Vytvoří ovládací prvek s klávesovou `CHotKeyCtrl` zkratkou a připojí jej k objektu.|
|[CHotKeyCtrl::CreateEx](#createex)|Vytvoří ovládací prvek s klávesovou zkratkou se zadanými rozšířenými styly systému Windows a připojí jej k objektu. `CHotKeyCtrl`|
|[CHotKeyCtrl::GetHotKey](#gethotkey)|Načte virtuální kód klíče a modifikátor příznaky klávesové zkratky z ovládacího prvku klávesové zkratky.|
|[CHotKeyCtrl::GetHotKeyName](#gethotkeyname)|Načte název klíče v místní znakové sadě přiřazený k klávesové klávesnici.|
|[CHotKeyCtrl::GetKeyName](#getkeyname)|Načte název klíče v místní znakové sadě přiřazený zadanému kódu virtuálního klíče.|
|[CHotKeyCtrl::SetHotKey](#sethotkey)|Nastaví kombinaci klávesových sklávesových kláves pro ovládací prvek s párpáry.|
|[CHotKeyCtrl::SetRules](#setrules)|Definuje neplatné kombinace a výchozí kombinaci modifikátoru pro ovládací prvek spárové klávesy.|

## <a name="remarks"></a>Poznámky

"Ovládací prvek spárové klávesy" je okno, které umožňuje uživateli vytvořit klávesovou zkratku. "Hot key" je kombinace kláves, kterou může uživatel rychle stisknout k provedení akce. (Uživatel může například vytvořit klávesovou zkratku, která aktivuje dané okno a přenese jej na začátek pořadí Z.) Ovládací prvek spárové klávesy zobrazí volby uživatele a zajistí, že uživatel vybere platnou kombinaci kláves.

Tento ovládací prvek `CHotKeyCtrl` (a tedy třída) je k dispozici pouze pro programy spuštěné v systémech Windows 95/98 a Windows NT verze 3.51 a novějších.

Pokud uživatel zvolí kombinaci kláves, aplikace může načíst zadanou kombinaci kláves z ovládacího prvku a pomocí WM_SETHOTKEY zprávy nastavit klávesovou zkratku v systému. Kdykoli uživatel stiskne klávesovou zkratku z libovolné části systému, zobrazí se v okně zadaném ve zprávě WM_SETHOTKEY WM_SYSCOMMAND zpráva určující SC_HOTKEY. Tato zpráva aktivuje okno, které ji obdrží. Klávesová zkratka zůstává platná, dokud aplikace, která volala WM_SETHOTKEY, neukončí.

Tento mechanismus se liší od podpory klávesových zkratky, která závisí na WM_HOTKEY zprávy a windows [RegisterHotKey](/windows/win32/api/winuser/nf-winuser-registerhotkey) a [unregisterHotKey](/windows/win32/api/winuser/nf-winuser-unregisterhotkey) funkce.

Další informace o `CHotKeyCtrl`použití naleznete v [tématech Ovládací prvky](../../mfc/controls-mfc.md) a [Použití kláves CHotKeyCtrl](../../mfc/using-chotkeyctrl.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

`CHotKeyCtrl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxcmn.h

## <a name="chotkeyctrlchotkeyctrl"></a><a name="chotkeyctrl"></a>CHotKeyCtrl::CHotKeyCtrl

Vytvoří `CHotKeyCtrl` objekt.

```
CHotKeyCtrl();
```

## <a name="chotkeyctrlcreate"></a><a name="create"></a>CHotKeyCtrl::Vytvořit

Vytvoří ovládací prvek s klávesovou `CHotKeyCtrl` zkratkou a připojí jej k objektu.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*dwStyl*<br/>
Určuje styl ovládacího prvku s párklávesové zkratky. Použijte libovolnou kombinaci stylů ovládacích prvků. Další informace naleznete v [tématu Běžné styly ovládacích prvků](/windows/win32/Controls/common-control-styles) v sadě Windows SDK.

*Rect*<br/>
Určuje velikost a umístění ovládacího prvku s párklávesové zkratky. Může to být buď [cRect](../../atl-mfc-shared/reference/crect-class.md) objekt nebo [RECT struktura](/windows/win32/api/windef/ns-windef-rect).

*pParentWnd*<br/>
Určuje nadřazené okno ovládacího prvku spárové klávesy, obvykle [CDialog](../../mfc/reference/cdialog-class.md). Nesmí být null.

*Nid*<br/>
Určuje ID ovládacího prvku s pár klávesovým klíčem.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byla inicializace úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Objekt vytvoříte ve `CHotKeyCtrl` dvou krocích. Nejprve zavolejte konstruktoru `Create`a potom volání , který vytvoří `CHotKeyCtrl` ovládací prvek klávesové zkratky a připojí jej k objektu.

Pokud chcete použít rozšířené styly oken s ovládacím `Create`prvkem, zavolejte [CreateEx](#createex) místo .

## <a name="chotkeyctrlcreateex"></a><a name="createex"></a>CHotKeyCtrl::CreateEx

Volání této funkce vytvořit ovládací prvek (podřízené okno) a přidružit k objektu. `CHotKeyCtrl`

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
Určuje styl ovládacího prvku s párklávesové zkratky. Použijte libovolnou kombinaci stylů ovládacích prvků. Další informace naleznete v [tématu Common Control Styles](/windows/win32/Controls/common-control-styles) in the Windows SDK.

*Rect*<br/>
Odkaz na [rect](/windows/win32/api/windef/ns-windef-rect) strukturu popisující velikost a umístění okna, které mají být vytvořeny, v klientských souřadnicích *pParentWnd*.

*pParentWnd*<br/>
Ukazatel na okno, které je nadřazený ovládací prvek.

*Nid*<br/>
ID podřízeného okna ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Místo `CreateEx` funkce [Vytvořit](#create) použijte použití rozšířených stylů systému Windows určených **předmluvou**rozšířeného stylu systému Windows WS_EX_ .

## <a name="chotkeyctrlgethotkey"></a><a name="gethotkey"></a>CHotKeyCtrl::GetHotKey

Načte virtuální kód klíče a modifikátor příznaky klávesové zkratky z ovládacího prvku klávesové zkratky.

```
DWORD GetHotKey() const;

void GetHotKey(
    WORD& wVirtualKeyCode,
    WORD& wModifiers) const;
```

### <a name="parameters"></a>Parametry

*wVirtualKeyCode*<br/>
[out] Kód virtuálního klíče klávesové zkratky. Seznam standardních virtuálních kódů klíčů naleznete v souboru Winuser.h.

*modifikátory wModifiers*<br/>
[out] Bitová kombinace (OR) příznaků, které označují modifikační klávesy v klávesové zkratce.

Modifikátor příznaky jsou následující:

|Příznak|Odpovídající klíč|
|----------|-----------------------|
|HOTKEYF_ALT|ALT klávesa|
|HOTKEYF_CONTROL|klávesa CTRL|
|HOTKEYF_EXT|Rozšířený klíč|
|HOTKEYF_SHIFT|Klávesa SHIFT|

### <a name="return-value"></a>Návratová hodnota

V první přetížené metody DWORD, který obsahuje virtuální kód klíče a modifikátor příznaky. Bajt nízkého řádu slova nižšího řádu obsahuje virtuální kód klíče, bajt vysokého řádu slova nižšího řádu obsahuje modifikátorové příznaky a slovo vyššího řádu je nulové.

### <a name="remarks"></a>Poznámky

Kód virtuální klávesy a modifikační klávesy společně definují klávesovou zkratku.

## <a name="chotkeyctrlgethotkeyname"></a><a name="gethotkeyname"></a>CHotKeyCtrl::GetHotKeyName

Volání této členské funkce získat lokalizovaný název klávesové zkratky.

```
CString GetHotKeyName() const;
```

### <a name="return-value"></a>Návratová hodnota

Lokalizovaný název aktuálně vybrané klávesové zkratky. Pokud není vybrána žádná `GetHotKeyName` klávesová zkratka, vrátí prázdný řetězec.

### <a name="remarks"></a>Poznámky

Název, který tato členská funkce vrátí pochází z ovladače klávesnice. Můžete nainstalovat nelokalizovaný ovladač klávesnice v lokalizované verzi systému Windows a naopak.

## <a name="chotkeyctrlgetkeyname"></a><a name="getkeyname"></a>CHotKeyCtrl::GetKeyName

Volání této členské funkce získat lokalizovaný název klíče přiřazeného k zadanému kódu virtuálního klíče.

```
static CString GetKeyName(
    UINT vk,
    BOOL fExtended);
```

### <a name="parameters"></a>Parametry

*Vk*<br/>
Kód virtuálního klíče.

*fExtended*<br/>
Pokud je kód virtuálního klíče rozšířený klíč, PRAVDA; jinak FALSE.

### <a name="return-value"></a>Návratová hodnota

Lokalizovaný název klíče určeného parametrem *vk.* Pokud klíč nemá žádný mapovaný název, `GetKeyName` vrátí prázdný řetězec.

### <a name="remarks"></a>Poznámky

Název klíče, který tato funkce vrátí, pochází z ovladače klávesnice, takže můžete nainstalovat nelokalizovaný ovladač klávesnice v lokalizované verzi systému Windows a naopak.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCControlLadenDialog#69](../../mfc/codesnippet/cpp/chotkeyctrl-class_1.cpp)]

## <a name="chotkeyctrlsethotkey"></a><a name="sethotkey"></a>CHotKeyCtrl::SetHotKey

Nastaví klávesovou zkratku pro ovládací prvek s klávesovou zkratkou.

```cpp
void SetHotKey(
    WORD wVirtualKeyCode,
    WORD wModifiers);
```

### <a name="parameters"></a>Parametry

*wVirtualKeyCode*<br/>
[v] Kód virtuálního klíče klávesové zkratky. Seznam standardních virtuálních kódů klíčů naleznete v souboru Winuser.h.

*modifikátory wModifiers*<br/>
[v] Bitová kombinace (OR) příznaků, které označují modifikační klávesy v klávesové zkratce.

Modifikátor příznaky jsou následující:

|Příznak|Odpovídající klíč|
|----------|-----------------------|
|HOTKEYF_ALT|ALT klávesa|
|HOTKEYF_CONTROL|klávesa CTRL|
|HOTKEYF_EXT|Rozšířený klíč|
|HOTKEYF_SHIFT|Klávesa SHIFT|

### <a name="remarks"></a>Poznámky

Kód virtuální klávesy a modifikační klávesy společně definují klávesovou zkratku.

## <a name="chotkeyctrlsetrules"></a><a name="setrules"></a>CHotKeyCtrl::SetRules

Volánítéto funkce definuje neplatné kombinace a výchozí kombinaci modifikátoru pro ovládací prvek klávesové zkratky.

```cpp
void SetRules(
    WORD wInvalidComb,
    WORD wModifiers);
```

### <a name="parameters"></a>Parametry

*wInvalidComb*<br/>
Pole příznaků, které určuje neplatné kombinace kláves. Může to být kombinace následujících hodnot:

- HKCOMB_A ALT

- HKCOMB_C CTRL

- HKCOMB_CA CTRL+ALT

- HKCOMB_NONE Nezměněné klíče

- HKCOMB_S POSUN

- HKCOMB_SA SHIFT+ALT

- HKCOMB_SC SHIFT+CTRL

- HKCOMB_SCA SHIFT+CTRL+ALT

*modifikátory wModifiers*<br/>
Pole příznaků, které určuje kombinaci kláves, která se má použít, když uživatel zadá neplatnou kombinaci. Další informace o příznaky modifikátoru naleznete v tématu [GetHotKey](#gethotkey).

### <a name="remarks"></a>Poznámky

Když uživatel zadá neplatnou kombinaci kláves, jak je definována příznaky zadané v *wInvalidComb*, systém používá operátor OR kombinovat klíče zadané uživatelem s příznaky zadanými v *wModifiers*. Výsledná kombinace kláves je převedena na řetězec a poté zobrazena v ovládacím prvku klávesové zkratky.

## <a name="see-also"></a>Viz také

[CWnd – třída](../../mfc/reference/cwnd-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)
