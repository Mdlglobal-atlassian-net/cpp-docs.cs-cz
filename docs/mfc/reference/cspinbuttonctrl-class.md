---
title: Třída CSpinButtonCtrl
ms.date: 11/04/2016
f1_keywords:
- CSpinButtonCtrl
- AFXCMN/CSpinButtonCtrl
- AFXCMN/CSpinButtonCtrl::CSpinButtonCtrl
- AFXCMN/CSpinButtonCtrl::Create
- AFXCMN/CSpinButtonCtrl::CreateEx
- AFXCMN/CSpinButtonCtrl::GetAccel
- AFXCMN/CSpinButtonCtrl::GetBase
- AFXCMN/CSpinButtonCtrl::GetBuddy
- AFXCMN/CSpinButtonCtrl::GetPos
- AFXCMN/CSpinButtonCtrl::GetRange
- AFXCMN/CSpinButtonCtrl::SetAccel
- AFXCMN/CSpinButtonCtrl::SetBase
- AFXCMN/CSpinButtonCtrl::SetBuddy
- AFXCMN/CSpinButtonCtrl::SetPos
- AFXCMN/CSpinButtonCtrl::SetRange
helpviewer_keywords:
- CSpinButtonCtrl [MFC], CSpinButtonCtrl
- CSpinButtonCtrl [MFC], Create
- CSpinButtonCtrl [MFC], CreateEx
- CSpinButtonCtrl [MFC], GetAccel
- CSpinButtonCtrl [MFC], GetBase
- CSpinButtonCtrl [MFC], GetBuddy
- CSpinButtonCtrl [MFC], GetPos
- CSpinButtonCtrl [MFC], GetRange
- CSpinButtonCtrl [MFC], SetAccel
- CSpinButtonCtrl [MFC], SetBase
- CSpinButtonCtrl [MFC], SetBuddy
- CSpinButtonCtrl [MFC], SetPos
- CSpinButtonCtrl [MFC], SetRange
ms.assetid: 509bfd76-1c5a-4af6-973f-e133c0b87734
ms.openlocfilehash: 4230d43bad8bcc15bcb26aaf0357e70216909ba1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318129"
---
# <a name="cspinbuttonctrl-class"></a>Třída CSpinButtonCtrl

Poskytuje funkce ovládacího prvku windows společné číselník.

## <a name="syntax"></a>Syntaxe

```
class CSpinButtonCtrl : public CWnd
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CSpinButtonCtrl::CSpinButtonCtrl](#cspinbuttonctrl)|Vytvoří `CSpinButtonCtrl` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CSpinButtonCtrl::Vytvořit](#create)|Vytvoří ovládací prvek číselníku a `CSpinButtonCtrl` připojí jej k objektu.|
|[CSpinButtonCtrl::CreateEx](#createex)|Vytvoří ovládací prvek číselníku se zadanými rozšířenými styly systému Windows a připojí jej k objektu. `CSpinButtonCtrl`|
|[CSpinButtonCtrl::GetAccel](#getaccel)|Načte informace o zrychlení pro ovládání číselníku.|
|[CSpinButtonCtrl::GetBase](#getbase)|Načte aktuální základnu pro ovládací prvek číselníku.|
|[CSpinButtonCtrl::GetBuddy](#getbuddy)|Načte ukazatel na aktuální okno kamaráda.|
|[CSpinButtonCtrl::GetPos](#getpos)|Načte aktuální pozici ovládacího prvku číselníku.|
|[CSpinButtonCtrl::GetRange](#getrange)|Načte horní a dolní meze (rozsah) pro ovládání číselníku.|
|[CSpinButtonCtrl::SetAccel](#setaccel)|Nastaví zrychlení ovládacího prvku číselníku.|
|[CSpinButtonCtrl::SetBase](#setbase)|Nastaví základnu pro ovládání číselníku.|
|[CSpinButtonCtrl::SetBuddy](#setbuddy)|Nastaví okno kamaráda pro ovládání číselníku.|
|[CSpinButtonCtrl::SetPos](#setpos)|Nastaví aktuální pozici ovládacího prvku.|
|[CSpinButtonCtrl::SetRange](#setrange)|Nastaví horní a dolní meze (rozsah) pro ovládání číselníku.|

## <a name="remarks"></a>Poznámky

"Spin button control" (označované také jako ovládací prvek nahoru dolů) je dvojice tlačítek se šipkami, na které může uživatel klepnout, aby zvýšil nebo snížil hodnotu, například pozici posouvání nebo číslo zobrazené v doprovodném ovládacím prvku. Hodnota přidružená k ovládacímu prvku číselníku se nazývá jeho aktuální poloha. Ovládací prvek číselníku se nejčastěji používá s doprovodným ovládacím prvkem nazývaným "okno kamaráda".

Tento ovládací prvek `CSpinButtonCtrl` (a tedy třída) je k dispozici pouze pro programy spuštěné v systémech Windows 95/98 a Windows NT verze 3.51 a novějších.

Pro uživatele ovládací prvek číselníku a jeho buddy okno často vypadají jako jeden ovládací prvek. Můžete určit, že ovládací prvek číselníku se automaticky umístí vedle okna kamaráda a že automaticky nastaví titulek okna kamaráda na jeho aktuální pozici. Pomocí ovládacího prvku číselníku s ovládacím prvkem pro úpravy můžete uživatele vyzvat k zadání číselného zadání.

Kliknutím na šipku nahoru posunete aktuální pozici směrem k maximu a klepnutím na šipku dolů posunete aktuální pozici směrem k minimu. Ve výchozím nastavení je minimum 100 a maximum je 0. Kdykoli je minimální nastavení větší než maximální nastavení (například při použití výchozího nastavení), klepnutím na šipku nahoru se sníží hodnota polohy a klepnutím na šipku dolů ji zvýšíte.

Ovládání číselníku bez okna kamaráda funguje jako jakýsi zjednodušený posuvník. Ovládací prvek tabulátoru například někdy zobrazuje ovládací prvek číselníku, který uživateli umožňuje posouvat další karty do zobrazení.

Další informace o `CSpinButtonCtrl`použití naleznete v [tématech Ovládací prvky](../../mfc/controls-mfc.md) a [Použití kláves CSpinButtonCtrl](../../mfc/using-cspinbuttonctrl.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

`CSpinButtonCtrl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxcmn.h

## <a name="cspinbuttonctrlcreate"></a><a name="create"></a>CSpinButtonCtrl::Vytvořit

Vytvoří ovládací prvek číselníku a `CSpinButtonCtrl` připojí jej k objektu..

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*dwStyl*<br/>
Určuje styl ovládacího prvku číselníku. Aplikujte na ovládací prvek libovolnou kombinaci stylů ovládání číselníku. Tyto styly jsou popsány v [části Styly ovládacího prvku nahoru dolů](/windows/win32/Controls/up-down-control-styles) v sadě Windows SDK.

*Rect*<br/>
Určuje velikost a polohu ovládacího prvku číselníku. Může to být buď [cRect](../../atl-mfc-shared/reference/crect-class.md) objekt nebo [rect](/previous-versions/dd162897\(v=vs.85\)) struktura

*pParentWnd*<br/>
Ukazatel na nadřazené okno ovládacího `CDialog`prvku číselníku, obvykle . Nesmí být null.

*Nid*<br/>
Určuje ID ovládacího prvku číselníku.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byla inicializace úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Nejprve `CSpinButtonCtrl` vytvoříte objekt ve dvou krocích, nejprve zavoláte konstruktor a pak zavoláte `Create`, který vytvoří ovládací prvek číselníku a připojí jej k objektu. `CSpinButtonCtrl`

Chcete-li vytvořit ovládací prvek číselníku s rozšířenými styly `Create`oken, zavolejte [CSpinButtonCtrl::CreateEx](#createex) místo .

## <a name="cspinbuttonctrlcreateex"></a><a name="createex"></a>CSpinButtonCtrl::CreateEx

Vytvoří ovládací prvek (podřízené okno) a `CSpinButtonCtrl` přidruží jej k objektu.

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
Určuje rozšířený styl vytvářeného ovládacího prvku. Seznam rozšířených stylů oken naleznete v parametru *dwExStyle* pro [createwindowex](/windows/win32/api/winuser/nf-winuser-createwindowexw) v sadě Windows SDK.

*dwStyl*<br/>
Určuje styl ovládacího prvku číselníku. Aplikujte na ovládací prvek libovolnou kombinaci stylů ovládání číselníku. Tyto styly jsou popsány v [části Styly ovládacího prvku nahoru dolů](/windows/win32/Controls/up-down-control-styles) v sadě Windows SDK.

*Rect*<br/>
Odkaz na [rect](/previous-versions/dd162897\(v=vs.85\)) strukturu popisující velikost a umístění okna, které mají být vytvořeny, v klientských souřadnicích *pParentWnd*.

*pParentWnd*<br/>
Ukazatel na okno, které je nadřazený ovládací prvek.

*Nid*<br/>
ID podřízeného okna ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Místo `CreateEx` funkce [Vytvořit](#create) použijte použití rozšířených stylů systému Windows určených předmluvou rozšířeného stylu systému Windows WS_EX_.

## <a name="cspinbuttonctrlcspinbuttonctrl"></a><a name="cspinbuttonctrl"></a>CSpinButtonCtrl::CSpinButtonCtrl

Vytvoří `CSpinButtonCtrl` objekt.

```
CSpinButtonCtrl();
```

## <a name="cspinbuttonctrlgetaccel"></a><a name="getaccel"></a>CSpinButtonCtrl::GetAccel

Načte informace o zrychlení pro ovládání číselníku.

```
UINT GetAccel(
    int nAccel,
    UDACCEL* pAccel) const;
```

### <a name="parameters"></a>Parametry

*nAccel*<br/>
Počet prvků v poli určeném *společností pAccel*.

*cAccel*<br/>
Ukazatel na pole struktur [UDACCEL,](/windows/win32/api/commctrl/ns-commctrl-udaccel) které přijímá informace o akceleraci.

### <a name="return-value"></a>Návratová hodnota

Počet načtení struktur akcelerátoru.

## <a name="cspinbuttonctrlgetbase"></a><a name="getbase"></a>CSpinButtonCtrl::GetBase

Načte aktuální základnu pro ovládací prvek číselníku.

```
UINT GetBase() const;
```

### <a name="return-value"></a>Návratová hodnota

Aktuální základní hodnota.

## <a name="cspinbuttonctrlgetbuddy"></a><a name="getbuddy"></a>CSpinButtonCtrl::GetBuddy

Načte ukazatel na aktuální okno kamaráda.

```
CWnd* GetBuddy() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na aktuální okno kamaráda.

## <a name="cspinbuttonctrlgetpos"></a><a name="getpos"></a>CSpinButtonCtrl::GetPos

Načte aktuální pozici ovládacího prvku číselníku.

```
int GetPos() const;  int GetPos32(LPBOOL lpbError = NULL) const;
```

### <a name="parameters"></a>Parametry

*Chyba lpbError*<br/>
Ukazatel na logickou hodnotu, která je nastavena na nulu, pokud je hodnota úspěšně načtena nebo nenulová, pokud dojde k chybě. Pokud je tento parametr nastaven na hodnotu NULL, nejsou hlášeny chyby.

### <a name="return-value"></a>Návratová hodnota

První verze vrátí 16bitovou aktuální pozici ve slově nižšího řádu. Slovo vyššího řádu je nenulové, pokud došlo k chybě.

Druhá verze vrátí 32bitovou pozici.

### <a name="remarks"></a>Poznámky

Když zpracovává vrácenou hodnotu, ovládací prvek aktualizuje svou aktuální pozici na základě titulku okna kamaráda. Ovládací prvek vrátí chybu, pokud neexistuje žádné okno kamaráda nebo pokud titulek určuje neplatnou hodnotu nebo hodnotu mimo rozsah.

## <a name="cspinbuttonctrlgetrange"></a><a name="getrange"></a>CSpinButtonCtrl::GetRange

Načte horní a dolní meze (rozsah) pro ovládání číselníku.

```
DWORD GetRange() const;

void GetRange(
    int& lower,
    int& upper) const;

void GetRange32(
    int& lower,
    int &upper) const;
```

### <a name="parameters"></a>Parametry

*Nižší*<br/>
Odkaz na celé číslo, které obdrží dolní limit pro ovládací prvek.

*Horní*<br/>
Odkaz na celé číslo, které obdrží horní limit pro ovládací prvek.

### <a name="return-value"></a>Návratová hodnota

První verze vrátí 32bitovou hodnotu obsahující horní a dolní mez. Slovo nižšího řádu je horní limit pro ovládací prvek a slovo vyššího řádu je dolní limit.

### <a name="remarks"></a>Poznámky

Členská `GetRange32` funkce načte rozsah ovládacího prvku číselníku jako 32bitové celé číslo.

## <a name="cspinbuttonctrlsetaccel"></a><a name="setaccel"></a>CSpinButtonCtrl::SetAccel

Nastaví zrychlení ovládacího prvku číselníku.

```
BOOL SetAccel(
    int nAccel,
    UDACCEL* pAccel);
```

### <a name="parameters"></a>Parametry

*nAccel*<br/>
Počet struktur [UDACCEL](/windows/win32/api/commctrl/ns-commctrl-udaccel) určených *v poAccelu*.

*cAccel*<br/>
Ukazatel na pole struktur UDACCEL, které obsahují informace o akceleraci. Prvky by měly být seřazeny vzestupně na základě `nSec` člena.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

## <a name="cspinbuttonctrlsetbase"></a><a name="setbase"></a>CSpinButtonCtrl::SetBase

Nastaví základnu pro ovládání číselníku.

```
int SetBase(int nBase);
```

### <a name="parameters"></a>Parametry

*nZákladna*<br/>
Nová základní hodnota ovládacího prvku. Může být 10 pro desetinné nebo 16 pro šestnáctkové.

### <a name="return-value"></a>Návratová hodnota

Předchozí základní hodnota, pokud je úspěšná, nebo nula, pokud je uveden neplatný základ.

### <a name="remarks"></a>Poznámky

Základní hodnota určuje, zda okno kamaráda zobrazí čísla v desítkových nebo šestnáctkových číslicích. Šestnáctková čísla jsou vždy nepodepsaná; desetinná čísla podepsána.

## <a name="cspinbuttonctrlsetbuddy"></a><a name="setbuddy"></a>CSpinButtonCtrl::SetBuddy

Nastaví okno kamaráda pro ovládání číselníku.

```
CWnd* SetBuddy(CWnd* pWndBuddy);
```

### <a name="parameters"></a>Parametry

*pWndBuddy*<br/>
Ukazatel na nové okno kamaráda.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na předchozí okno kamaráda.

### <a name="remarks"></a>Poznámky

Ovládací prvek odstřeďování je téměř vždy spojen s jiným oknem, jako je například ovládací prvek pro úpravy, který zobrazuje určitý obsah. Toto druhé okno se nazývá "buddy" ovládacího prvku spin.

## <a name="cspinbuttonctrlsetpos"></a><a name="setpos"></a>CSpinButtonCtrl::SetPos

Nastaví aktuální pozici ovládacího prvku číselníku.

```
int SetPos(int nPos);
int SetPos32(int nPos);
```

### <a name="parameters"></a>Parametry

*nPos*<br/>
Nová pozice pro ovládání. Tato hodnota musí být v rozsahu určeném horní a dolní meze ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Předchozí pozice (16bitová `SetPos`přesnost pro , 32bitová přesnost pro). `SetPos32`

### <a name="remarks"></a>Poznámky

`SetPos32`nastaví 32bitovou polohu.

## <a name="cspinbuttonctrlsetrange"></a><a name="setrange"></a>CSpinButtonCtrl::SetRange

Nastaví horní a dolní meze (rozsah) pro ovládání číselníku.

```
void SetRange(
    short nLower,
    short nUpper);

void SetRange32(
    int nLower,
    int nUpper);
```

### <a name="parameters"></a>Parametry

*nLower* a *nHorní*<br/>
Horní a dolní limity pro ovládací prvek. Pro `SetRange`, ani limit může být větší než UD_MAXVAL nebo menší než UD_MINVAL; kromě toho rozdíl mezi těmito dvěma limity nesmí překročit UD_MAXVAL. `SetRange32`neomezuje žádné limity; používat všechna celá čísla.

### <a name="remarks"></a>Poznámky

Členská `SetRange32` funkce nastavuje 32bitový rozsah pro ovládání číselníku.

> [!NOTE]
> Výchozí rozsah pro číselník má maximální nastavenou na nulu (0) a minimální hodnotu 100. Vzhledem k tomu, že maximální hodnota je menší než minimální hodnota, kliknutím na šipku nahoru se pozice sníží a klepnutím na šipku dolů ji zvýšíte. Slouží `CSpinButtonCtrl::SetRange` k úpravě těchto hodnot.

## <a name="see-also"></a>Viz také

[Ukázka knihovny MFC CMNCTRL2](../../overview/visual-cpp-samples.md)<br/>
[CWnd – třída](../../mfc/reference/cwnd-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CSliderCtrl – třída](../../mfc/reference/csliderctrl-class.md)
