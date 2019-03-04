---
title: Cspinbuttonctrl – třída
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
ms.openlocfilehash: 3c973d92550469804a5389b84f53005e4f2c154f
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57290427"
---
# <a name="cspinbuttonctrl-class"></a>Cspinbuttonctrl – třída

Poskytuje funkce pro Windows běžné tlačítko číselníku.

## <a name="syntax"></a>Syntaxe

```
class CSpinButtonCtrl : public CWnd
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CSpinButtonCtrl::CSpinButtonCtrl](#cspinbuttonctrl)|Vytvoří `CSpinButtonCtrl` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CSpinButtonCtrl::Create](#create)|Ovládací prvek číselníku vytvoří a připojí ho k `CSpinButtonCtrl` objektu.|
|[CSpinButtonCtrl::CreateEx](#createex)|Vytvoří ovládací prvek číselníku se zadaným rozšířené styly Windows a připojí ho k `CSpinButtonCtrl` objektu.|
|[CSpinButtonCtrl::GetAccel](#getaccel)|Načte informace o zrychlení pro ovládací prvek číselníku.|
|[CSpinButtonCtrl::GetBase](#getbase)|Načte aktuální základ pro ovládací prvek číselníku.|
|[CSpinButtonCtrl::GetBuddy](#getbuddy)|Načte ukazatel na aktuální asociovaného okna.|
|[CSpinButtonCtrl::GetPos](#getpos)|Načte aktuální pozici ovládací prvek číselníku.|
|[CSpinButtonCtrl::GetRange](#getrange)|Načte horní a dolní mez (oblast) pro ovládací prvek číselníku.|
|[CSpinButtonCtrl::SetAccel](#setaccel)|Nastaví zrychlení pro ovládací prvek číselníku.|
|[CSpinButtonCtrl::SetBase](#setbase)|Nastaví základ pro ovládací prvek číselníku.|
|[CSpinButtonCtrl::SetBuddy](#setbuddy)|Nastaví asociovaného okna pro ovládací prvek číselníku.|
|[CSpinButtonCtrl::SetPos](#setpos)|Nastaví aktuální pozici pro ovládací prvek.|
|[CSpinButtonCtrl::SetRange](#setrange)|Nastaví horní a dolní mez (oblast) pro ovládací prvek číselníku.|

## <a name="remarks"></a>Poznámky

"Otočný ovládací prvek tlačítko" (označované také jako ovládací prvek směrem nahoru a dolů) je pár tlačítek, které uživatel může klepnout a zvýšit nebo snížit hodnotu, jako je například pozici posunutí nebo číslo zobrazí v ovládacím prvku Průvodce vyhledáváním. Hodnota přidružená k ovládací prvek číselníku se nazývá své aktuální pozici. Ovládací prvek číselníku se nejčastěji používá s ovládacím prvkem Průvodce vyhledáváním, nazývá "asociované okno."

Tento ovládací prvek (a tedy `CSpinButtonCtrl` třídy) je dostupná jenom pro programy spuštěné v rámci Windows 95/98 a Windows NT verze 3.51 a vyšší.

Pro uživatele ovládací prvek číselníku a jeho asociované okno často vypadat jako jeden ovládací prvek. Můžete určit, že ovládací prvek číselníku umožňuje automatické umísťování samotné vedle jeho asociované okno, a to automaticky nastaví titulek asociovaného okna na aktuální pozici. Ovládací prvek číselníku pomocí ovládacího prvku pro úpravy můžete požádat uživatele o číselných údajů na vstupu.

Kliknutím na šipku nahoru Přesune aktuální pozice směrem k maximální a kliknutím na šipku dolů přesune aktuální pozice směrem k minimální. Ve výchozím nastavení minimální hodnota je 100 a maximální hodnota je 0. Pokaždé, když je větší než maximální nastavení (například když použijete výchozí nastavení), klepnutím na položku nahoru šipka snížení nastavení minimální hodnota pozice a kliknutím na šipku dolů zvyšuje.

Ovládací prvek číselníku bez asociované okno funguje jako řazení zjednodušené posuvníku. Například ovládací prvek karty zobrazí někdy ovládací prvek číselníku umožňující uživateli přejděte do zobrazení další záložky.

Další informace o používání `CSpinButtonCtrl`, naleznete v tématu [ovládací prvky](../../mfc/controls-mfc.md) a [používání atributu CSpinButtonCtrl](../../mfc/using-cspinbuttonctrl.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CSpinButtonCtrl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxcmn.h

##  <a name="create"></a>  CSpinButtonCtrl::Create

Ovládací prvek číselníku vytvoří a připojí ho k `CSpinButtonCtrl` objektu...

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*dwStyle*<br/>
Určuje styl tlačítka číselníku. Použijte libovolnou kombinaci styly ovládací prvek typu číselník tlačítek do ovládacího prvku. Tyto styly jsou popsány v [– styly ovládacího prvku číselník](/windows/desktop/Controls/up-down-control-styles) v sadě Windows SDK.

*Rect*<br/>
Určuje velikost a umístění tlačítko číselníku. Může být buď [crect –](../../atl-mfc-shared/reference/crect-class.md) objektu nebo [RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897) struktura

*pParentWnd*<br/>
Ukazatel na prvek typu číselník button nadřazené okno, obvykle `CDialog`. Nesmí být NULL.

*nID*<br/>
Určuje ID tlačítko číselníku.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud se inicializace byla úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Můžete vytvořit `CSpinButtonCtrl` objekt ve dvou krocích, volání konstruktoru a následně zavolat `Create`, otočný ovládací prvek tlačítko vytvoří a připojí ho k `CSpinButtonCtrl` objektu.

Chcete-li vytvořit ovládací prvek číselníku s rozšířené styly oken, zavolejte [CSpinButtonCtrl::CreateEx](#createex) místo `Create`.

##  <a name="createex"></a>  CSpinButtonCtrl::CreateEx

Vytvoří ovládací prvek (podřízené okno) a přidruží ji k `CSpinButtonCtrl` objektu.

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
Určuje rozšířený styl ovládacího prvku vytváří. Seznam rozšířených windows stylů, najdete v článku *dwExStyle* parametr pro [CreateWindowEx](/windows/desktop/api/winuser/nf-winuser-createwindowexa) v sadě Windows SDK.

*dwStyle*<br/>
Určuje styl tlačítka číselníku. Použijte libovolnou kombinaci styly ovládací prvek typu číselník tlačítek do ovládacího prvku. Tyto styly jsou popsány v [– styly ovládacího prvku číselník](/windows/desktop/Controls/up-down-control-styles) v sadě Windows SDK.

*Rect*<br/>
Odkaz na [RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897) struktura popisující, velikost a umístění okna, které nelze v souřadnice klienta *pParentWnd*.

*pParentWnd*<br/>
Ukazatel na okno, který je nadřazeného ovládacího prvku.

*nID*<br/>
ID ovládacího prvku podřízené okno.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Použití `CreateEx` místo [vytvořit](#create) použít rozšířené styly Windows určené předponu rozšířeného stylu Windows WS_EX_.

##  <a name="cspinbuttonctrl"></a>  CSpinButtonCtrl::CSpinButtonCtrl

Vytvoří `CSpinButtonCtrl` objektu.

```
CSpinButtonCtrl();
```

##  <a name="getaccel"></a>  CSpinButtonCtrl::GetAccel

Načte informace o zrychlení pro ovládací prvek číselníku.

```
UINT GetAccel(
    int nAccel,
    UDACCEL* pAccel) const;
```

### <a name="parameters"></a>Parametry

*nAccel*<br/>
Počet prvků v poli určeném *pAccel*.

*pAccel*<br/>
Ukazatel na pole [UDACCEL](/windows/desktop/api/commctrl/ns-commctrl-_udaccel) struktury, které obdrží informace o zrychlení.

### <a name="return-value"></a>Návratová hodnota

Počet struktur akcelerátoru načtení.

##  <a name="getbase"></a>  CSpinButtonCtrl::GetBase

Načte aktuální základ pro ovládací prvek číselníku.

```
UINT GetBase() const;
```

### <a name="return-value"></a>Návratová hodnota

Aktuální základní hodnoty.

##  <a name="getbuddy"></a>  CSpinButtonCtrl::GetBuddy

Načte ukazatel na aktuální asociovaného okna.

```
CWnd* GetBuddy() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na aktuální asociovaného okna.

##  <a name="getpos"></a>  CSpinButtonCtrl::GetPos

Načte aktuální pozici ovládací prvek číselníku.

```
int GetPos() const;  int GetPos32(LPBOOL lpbError = NULL) const;
```

### <a name="parameters"></a>Parametry

*lpbError*<br/>
Ukazatel na logickou hodnotu, která je nastavena na hodnotu nula, pokud hodnota je úspěšně načtena, nebo nenulovou Pokud dojde k chybě. Pokud tento parametr je nastaven na hodnotu NULL, nejsou hlášeny chyby.

### <a name="return-value"></a>Návratová hodnota

První verze vrací aktuální pozici 16 bitů v nižší řád slova. Vyšší řád slova je nenulová, pokud došlo k chybě.

Druhá verze vrátí pozici 32-bit.

### <a name="remarks"></a>Poznámky

Po zpracování vrácená hodnota, ovládací prvek aktualizuje aktuální pozici založené na titulek asociovaného okna. Ovládací prvek vrátí chybu, pokud neexistuje žádný časový interval kamaráda nebo pokud titulek určuje neplatné nebo mimo rozsah hodnoty.

##  <a name="getrange"></a>  CSpinButtonCtrl::GetRange

Načte horní a dolní mez (oblast) pro ovládací prvek číselníku.

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

*lower*<br/>
Odkaz na celé číslo, které přijímá dolní mez pro ovládací prvek.

*upper*<br/>
Odkaz na celé číslo, které přijímá horní mez pro ovládací prvek.

### <a name="return-value"></a>Návratová hodnota

První verze vrací hodnotu 32-bit obsahující horní a dolní limity. Horní mez pro ovládací prvek je nižší řád slova a vyšší řád slova je dolní mez.

### <a name="remarks"></a>Poznámky

Členská funkce `GetRange32` načte rozsah tlačítko číselníku jako 32bitové celé číslo.

##  <a name="setaccel"></a>  CSpinButtonCtrl::SetAccel

Nastaví zrychlení pro ovládací prvek číselníku.

```
BOOL SetAccel(
    int nAccel,
    UDACCEL* pAccel);
```

### <a name="parameters"></a>Parametry

*nAccel*<br/>
Počet [UDACCEL](/windows/desktop/api/commctrl/ns-commctrl-_udaccel) struktury určené *pAccel*.

*pAccel*<br/>
Ukazatel na pole UDACCEL struktur, které obsahují informace o zrychlení. Prvky mají být řazeny ve vzestupném pořadí podle `nSec` člena.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

##  <a name="setbase"></a>  CSpinButtonCtrl::SetBase

Nastaví základ pro ovládací prvek číselníku.

```
int SetBase(int nBase);
```

### <a name="parameters"></a>Parametry

*nBase*<br/>
Nové základní hodnotu ovládacího prvku. Může být pro desetinné číslo 10 nebo 16 pro šestnáctkové číslo.

### <a name="return-value"></a>Návratová hodnota

Předchozí základní hodnoty v případě úspěchu, nebo nula, pokud je zadána neplatná základna.

### <a name="remarks"></a>Poznámky

Základní hodnota určuje, zda asociovaného okna zobrazuje čísel v desítkové nebo šestnáctkové číslice. Šestnáctková čísla jsou vždycky bez znaménka; desetinná čísla jsou podepsané.

##  <a name="setbuddy"></a>  CSpinButtonCtrl::SetBuddy

Nastaví asociovaného okna pro ovládací prvek číselníku.

```
CWnd* SetBuddy(CWnd* pWndBuddy);
```

### <a name="parameters"></a>Parametry

*pWndBuddy*<br/>
Ukazatel na novou asociovaného okna.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na předchozí asociovaného okna.

### <a name="remarks"></a>Poznámky

Ovládací prvek typu číselník je téměř vždy další okno, jako je například ovládací prvek úprav, zobrazující nějaký obsah. Toto okno se nazývá "kamarádské" číselníku.

##  <a name="setpos"></a>  CSpinButtonCtrl::SetPos

Nastaví aktuální pozici pro ovládací prvek číselníku.

```
int SetPos(int nPos);
int SetPos32(int nPos);
```

### <a name="parameters"></a>Parametry

*nPos*<br/>
Nové pozice ovládacího prvku. Tato hodnota musí být v rozsahu určeném horní a dolní limity pro ovládací prvek.

### <a name="return-value"></a>Návratová hodnota

Předchozí pozice (16 bitů přesnosti pro `SetPos`, 32 bitů přesnosti pro `SetPos32`).

### <a name="remarks"></a>Poznámky

`SetPos32` Nastaví pozici 32-bit.

##  <a name="setrange"></a>  CSpinButtonCtrl::SetRange

Nastaví horní a dolní mez (oblast) pro ovládací prvek číselníku.

```
void SetRange(
    short nLower,
    short nUpper);

void SetRange32(
    int nLower,
    int nUpper);
```

### <a name="parameters"></a>Parametry

*nLower* a *nUpper*<br/>
Horní a dolní limity pro ovládací prvek. Pro `SetRange`, ani jedno z těchto omezení může být větší než UD_MAXVAL nebo menší než UD_MINVAL; navíc rozdíl mezi dvě omezení nemůže být delší než UD_MAXVAL. `SetRange32` umístí bez omezení na omezení; použijte libovolný celých čísel.

### <a name="remarks"></a>Poznámky

Členská funkce `SetRange32` Nastaví rozsah 32bitové otočný ovládací prvek tlačítko.

> [!NOTE]
>  Výchozí rozsah pro číselníku je nastavena na hodnotu 100 minimální a maximální doba, nastavit na nulu (0). Vzhledem k tomu, že maximální hodnota je menší než minimální hodnota, kliknutím na šipku nahoru nižší pozici a kliknutím na šipku dolů zvýší ho. Použití `CSpinButtonCtrl::SetRange` upravit tyto hodnoty.

## <a name="see-also"></a>Viz také:

[Ukázka CMNCTRL2 knihovny MFC](../../visual-cpp-samples.md)<br/>
[CWnd – třída](../../mfc/reference/cwnd-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CSliderCtrl – třída](../../mfc/reference/csliderctrl-class.md)
