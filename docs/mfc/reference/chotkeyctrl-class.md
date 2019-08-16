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
ms.openlocfilehash: 9818c32a7779d646ca5a9485a1331dfa393408ba
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69506148"
---
# <a name="chotkeyctrl-class"></a>CHotKeyCtrl – třída

Poskytuje funkce pro běžný ovládací prvek Windows pro klávesovou zkratku.

## <a name="syntax"></a>Syntaxe

```
class CHotKeyCtrl : public CWnd
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CHotKeyCtrl::CHotKeyCtrl](#chotkeyctrl)|`CHotKeyCtrl` Vytvoří objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CHotKeyCtrl::Create](#create)|Vytvoří ovládací prvek s klávesou Hot a připojí ho k `CHotKeyCtrl` objektu.|
|[CHotKeyCtrl::CreateEx](#createex)|Vytvoří ovládací prvek s klávesou Hot pomocí zadaných rozšířených stylů Windows a připojí ho k `CHotKeyCtrl` objektu.|
|[CHotKeyCtrl::GetHotKey](#gethotkey)|Načte kód virtuálního klíče a příznaky modifikátoru horké klávesy z ovládacího prvku klávesová zkratka.|
|[CHotKeyCtrl::GetHotKeyName](#gethotkeyname)|Načte název klíče v místní znakové sadě přiřazený k klávesové zkratce.|
|[CHotKeyCtrl::GetKeyName](#getkeyname)|Načte název klíče v místní znakové sadě přiřazený zadanému kódu virtuálního klíče.|
|[CHotKeyCtrl::SetHotKey](#sethotkey)|Nastaví kombinaci klávesových zkratek pro ovládací prvek s klávesou Hot.|
|[CHotKeyCtrl::SetRules](#setrules)|Definuje neplatné kombinace a výchozí kombinaci modifikátoru pro ovládací prvek s klávesou Hot.|

## <a name="remarks"></a>Poznámky

Klíčové slovo "Hot Key Control" je okno, které umožňuje uživateli vytvořit klávesovou zkratku. "Horká klávesa" je kombinace kláves, kterou může uživatel stisknout k rychlému provedení akce. (Uživatel může například vytvořit klávesovou zkratku, která aktivuje dané okno a přesune ho do horní části objednávky Z.) Ovládací prvek klávesová zkratka zobrazuje možnosti uživatele a zajišťuje, že uživatel vybere platnou kombinaci kláves.

Tento ovládací prvek (a `CHotKeyCtrl` třída) je k dispozici pouze pro programy, které jsou spuštěny v systémech Windows 95/98 a Windows NT verze 3,51 a novější.

Pokud uživatel zvolí kombinaci kláves, může aplikace načíst zadanou kombinaci kláves z ovládacího prvku a pomocí zprávy WM_SETHOTKEY nastavit klávesovou zkratku v systému. Pokaždé, když uživatel stiskne klávesovou zkratku, z jakékoli části systému, zobrazí okno zadané ve zprávě WM_SETHOTKEY zprávu WM_SYSCOMMAND s určením SC_HOTKEY. Tato zpráva aktivuje okno, které ho přijme. Klávesová zkratka zůstane platná, dokud nebude ukončena aplikace, která se nazývá WM_SETHOTKEY.

Tento mechanismus se liší od podpory klávesových zkratek, která závisí na zprávě WM_HOTKEY a funkcích Windows [RegisterHotKey](/windows/win32/api/winuser/nf-winuser-registerhotkey) a [UnregisterHotKey](/windows/win32/api/winuser/nf-winuser-unregisterhotkey) .

Další informace o použití `CHotKeyCtrl`naleznete v tématu [Controls](../../mfc/controls-mfc.md) and [using CHotKeyCtrl](../../mfc/using-chotkeyctrl.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CHotKeyCtrl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxcmn. h

##  <a name="chotkeyctrl"></a>CHotKeyCtrl:: CHotKeyCtrl

`CHotKeyCtrl` Vytvoří objekt.

```
CHotKeyCtrl();
```

##  <a name="create"></a>CHotKeyCtrl:: Create

Vytvoří ovládací prvek s klávesou Hot a připojí ho k `CHotKeyCtrl` objektu.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*dwStyle*<br/>
Určuje styl ovládacího prvku klávesová zkratka. Použití libovolné kombinace stylů ovládacích prvků. Další informace najdete v tématu [Běžné styly ovládacích prvků](/windows/win32/Controls/common-control-styles) v Windows SDK.

*OBD*<br/>
Určuje velikost a polohu ovládacího prvku klávesová zkratka. Může to být buď objekt [CRect](../../atl-mfc-shared/reference/crect-class.md) , nebo [Struktura Rect](/windows/win32/api/windef/ns-windef-rect).

*pParentWnd*<br/>
Určuje nadřazené okno ovládacího prvku klávesová zkratka, obvykle [CDialog](../../mfc/reference/cdialog-class.md). Nesmí mít hodnotu NULL.

*nID*<br/>
Určuje ID ovládacího prvku klávesová zkratka.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud inicializace byla úspěšná; v opačném případě 0.

### <a name="remarks"></a>Poznámky

`CHotKeyCtrl` Vytvoříte objekt ve dvou krocích. Nejprve zavolejte konstruktor a potom zavolejte `Create`, čímž vytvoříte ovládací prvek Hot Key a připojíte ho `CHotKeyCtrl` k objektu.

Chcete-li použít rozšířené styly systému Windows s ovládacím prvkem, zavolejte [CreateEx](#createex) místo `Create`.

##  <a name="createex"></a>CHotKeyCtrl:: CreateEx

Voláním této funkce vytvořte ovládací prvek (podřízené okno) a přidružte jej `CHotKeyCtrl` k objektu.

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
Určuje rozšířený styl ovládacího prvku, který se vytváří. Seznam rozšířených stylů Windows naleznete v parametru *dwExStyle* pro [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) v Windows SDK.

*dwStyle*<br/>
Určuje styl ovládacího prvku klávesová zkratka. Použití libovolné kombinace stylů ovládacích prvků. Další informace najdete v tématu [Běžné styly ovládacích prvků](/windows/win32/Controls/common-control-styles) v Windows SDK.

*OBD*<br/>
Odkaz na strukturu [Rect](/previous-versions/dd162897\(v=vs.85\)) popisující velikost a umístění okna, které má být vytvořeno, v souřadnicích klienta *pParentWnd*.

*pParentWnd*<br/>
Ukazatel na okno, které je nadřazený ovládacímu prvku.

*nID*<br/>
ID podřízeného okna ovládacího prvku

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Použijte `CreateEx` místo příkaz [vytvořit](#create) pro použití rozšířených stylů Windows, které jsou určené **WS_EX_** rozšířeným stylem Windows.

##  <a name="gethotkey"></a>CHotKeyCtrl:: getklávesa

Načte kód virtuálního klíče a příznaky modifikátoru klávesové zkratky z ovládacího prvku klávesová zkratka.

```
DWORD GetHotKey() const;

void GetHotKey(
    WORD& wVirtualKeyCode,
    WORD& wModifiers) const;
```

### <a name="parameters"></a>Parametry

*wVirtualKeyCode*<br/>
mimo Kód virtuálního klíče klávesové zkratky Seznam standardních kódů virtuálních klíčů naleznete v tématu Winuser. h.

*wModifiers*<br/>
mimo Bitových kombinací (nebo) příznaků, které označují modifikační klávesy v klávesových zkratce.

Příznaky modifikátoru jsou následující:

|Příznak|Odpovídající klíč|
|----------|-----------------------|
|HOTKEYF_ALT|ALT klávesa|
|HOTKEYF_CONTROL|Klávesa CTRL|
|HOTKEYF_EXT|Rozšířený klíč|
|HOTKEYF_SHIFT|Klávesa SHIFT|

### <a name="return-value"></a>Návratová hodnota

V první přetížené metodě je typu DWORD, který obsahuje kód virtuálního klíče a příznaky modifikátoru. Dolní bajt slova s nižším pořadím obsahuje kód virtuálního klíče, což je horní bajt slova s nižším pořadím, který obsahuje příznaky modifikátoru a slovo s vyšším pořadím je nula.

### <a name="remarks"></a>Poznámky

Klávesovou zkratku definujete kód virtuálního klíče a modifikační klávesy společně.

##  <a name="gethotkeyname"></a>CHotKeyCtrl:: getklávesová zkratka

Zavolejte tuto členskou funkci, aby se získal lokalizovaný název klávesy Hot.

```
CString GetHotKeyName() const;
```

### <a name="return-value"></a>Návratová hodnota

Lokalizovaný název aktuálně vybraného klávesové zkratky. Pokud není vybrána žádná klávesová zkratka, `GetHotKeyName` vrátí prázdný řetězec.

### <a name="remarks"></a>Poznámky

Název, který vrací tato členská funkce, pochází z ovladače klávesnice. V lokalizované verzi systému Windows můžete nainstalovat nelokalizovaný ovladač klávesnice a naopak.

##  <a name="getkeyname"></a>CHotKeyCtrl:: getkeyname

Volejte tuto členskou funkci pro získání lokalizovaného názvu klíče přiřazeného k zadanému kódu virtuálního klíče.

```
static CString GetKeyName(
    UINT vk,
    BOOL fExtended);
```

### <a name="parameters"></a>Parametry

*vk*<br/>
Kód virtuálního klíče.

*fExtended*<br/>
Pokud je kód virtuálního klíče rozšířený klíč, pravda; v opačném případě FALSE.

### <a name="return-value"></a>Návratová hodnota

Lokalizovaný název klíče zadaného parametrem *VK* Pokud klíč nemá žádný mapovaný název, `GetKeyName` vrátí prázdný řetězec.

### <a name="remarks"></a>Poznámky

Název klíče, který tato funkce vrátí, pochází z ovladače klávesnice, takže můžete nainstalovat nelokalizovaný ovladač klávesnice v lokalizované verzi Windows a naopak.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCControlLadenDialog#69](../../mfc/codesnippet/cpp/chotkeyctrl-class_1.cpp)]

##  <a name="sethotkey"></a>CHotKeyCtrl:: SetHotKey

Nastaví klávesovou zkratku pro ovládací prvek s klávesou Hot.

```
void SetHotKey(
    WORD wVirtualKeyCode,
    WORD wModifiers);
```

### <a name="parameters"></a>Parametry

*wVirtualKeyCode*<br/>
pro Kód virtuálního klíče klávesové zkratky Seznam standardních kódů virtuálních klíčů naleznete v tématu Winuser. h.

*wModifiers*<br/>
pro Bitových kombinací (nebo) příznaků, které označují modifikační klávesy v klávesových zkratce.

Příznaky modifikátoru jsou následující:

|Příznak|Odpovídající klíč|
|----------|-----------------------|
|HOTKEYF_ALT|ALT klávesa|
|HOTKEYF_CONTROL|Klávesa CTRL|
|HOTKEYF_EXT|Rozšířený klíč|
|HOTKEYF_SHIFT|Klávesa SHIFT|

### <a name="remarks"></a>Poznámky

Klávesovou zkratku definujete kód virtuálního klíče a modifikační klávesy společně.

##  <a name="setrules"></a>CHotKeyCtrl:: SetRules

Voláním této funkce můžete definovat neplatné kombinace a výchozí kombinaci modifikátoru pro ovládací prvek s klávesou Hot.

```
void SetRules(
    WORD wInvalidComb,
    WORD wModifiers);
```

### <a name="parameters"></a>Parametry

*wInvalidComb*<br/>
Pole příznaků, které určuje neplatné kombinace kláves. Může se jednat o kombinaci následujících hodnot:

- HKCOMB_A ALT

- HKCOMB_C CTRL

- HKCOMB_CA CTRL + ALT

- HKCOMB_NONE nezměněných klíčů

- HKCOMB_S SHIFT

- HKCOMB_SA SHIFT + ALT

- HKCOMB_SC SHIFT + CTRL

- HKCOMB_SCA SHIFT + CTRL + ALT

*wModifiers*<br/>
Pole příznaků, které určuje kombinaci kláves, která se má použít, když uživatel zadá neplatnou kombinaci. Další informace o příznacích modifikátoru najdete v [](#gethotkey)tématu getklávesa.

### <a name="remarks"></a>Poznámky

Když uživatel zadá neplatnou kombinaci kláves, jak je definováno pomocí příznaků určených v *wInvalidComb*, systém pomocí operátoru OR sloučí klíče zadané uživatelem s příznaky určenými v *wModifiers*. Výsledná kombinace klíčů je převedena na řetězec a pak zobrazena v ovládacím prvku klávesová zkratka.

## <a name="see-also"></a>Viz také:

[CWnd – třída](../../mfc/reference/cwnd-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)
