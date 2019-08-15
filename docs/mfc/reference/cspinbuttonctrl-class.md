---
title: Atributu CSpinButtonCtrl – třída
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
ms.openlocfilehash: c167745eed45b7081e62a2c3be225a33e7ee0520
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502445"
---
# <a name="cspinbuttonctrl-class"></a>Atributu CSpinButtonCtrl – třída

Poskytuje funkce obecného ovládacího prvku číselníku pro Windows.

## <a name="syntax"></a>Syntaxe

```
class CSpinButtonCtrl : public CWnd
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CSpinButtonCtrl::CSpinButtonCtrl](#cspinbuttonctrl)|`CSpinButtonCtrl` Vytvoří objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CSpinButtonCtrl::Create](#create)|Vytvoří ovládací prvek číselníku a připojí ho k `CSpinButtonCtrl` objektu.|
|[CSpinButtonCtrl::CreateEx](#createex)|Vytvoří ovládací prvek číselníku se zadanými rozšířenými styly Windows a připojí ho k `CSpinButtonCtrl` objektu.|
|[CSpinButtonCtrl::GetAccel](#getaccel)|Načte informace o akceleraci pro ovládací prvek číselníku.|
|[CSpinButtonCtrl::GetBase](#getbase)|Načte aktuální základ ovládacího prvku číselníku.|
|[CSpinButtonCtrl::GetBuddy](#getbuddy)|Načte ukazatel na aktuální kamarád okno.|
|[CSpinButtonCtrl::GetPos](#getpos)|Načte aktuální pozici ovládacího prvku číselníku.|
|[CSpinButtonCtrl::GetRange](#getrange)|Načte horní a dolní meze (rozsah) pro ovládací prvek číselníku.|
|[CSpinButtonCtrl::SetAccel](#setaccel)|Nastaví zrychlení pro ovládací prvek číselníku.|
|[CSpinButtonCtrl::SetBase](#setbase)|Nastaví základ pro ovládací prvek číselníku.|
|[CSpinButtonCtrl::SetBuddy](#setbuddy)|Nastaví kamarád okno pro ovládací prvek číselníku.|
|[CSpinButtonCtrl::SetPos](#setpos)|Nastaví aktuální pozici ovládacího prvku.|
|[CSpinButtonCtrl::SetRange](#setrange)|Nastaví horní a dolní meze (rozsah) pro ovládací prvek číselníku.|

## <a name="remarks"></a>Poznámky

"Ovládací prvek číselníku" (označovaný také jako ovládací prvek rozevíracího seznamu) je dvojice tlačítek se šipkami, na které může uživatel kliknout na zvýšení nebo snížení hodnoty, jako je například pozice posunutí nebo číslo zobrazené v doprovodném ovládacím prvku. Hodnota přidružená k ovládacímu prvku číselníku se nazývá aktuální pozice. Ovládací prvek číselníku se nejčastěji používá u doprovodného ovládacího prvku, který se nazývá "přítel okno".

Tento ovládací prvek (a `CSpinButtonCtrl` třída) je k dispozici pouze pro programy, které jsou spuštěny v systémech Windows 95/98 a Windows NT verze 3,51 a novější.

Uživateli se ovládací prvek číselníku a jeho přítelní okno často podobají jednomu ovládacímu prvku. Můžete určit, že ovládací prvek číselníku se automaticky umístí vedle jeho kamarádho okna a automaticky nastaví titulek okna pro kamarády na aktuální pozici. Pomocí ovládacího prvku číselník můžete v ovládacím prvku pro úpravy vyzvat uživatele k zadání číselného vstupu.

Kliknutím na šipku nahoru přesunete aktuální pozici směrem k maximálnímu počtu a kliknutím na šipku dolů přesunete aktuální pozici směrem k minimálnímu umístění. Ve výchozím nastavení je minimum 100 a maximum je 0. Pokaždé, když je minimální nastavení větší než maximální nastavení (například při použití výchozího nastavení), kliknutím na šipku nahoru snížíte hodnotu pozice a kliknete na šipku dolů.

Ovládací prvek číselníku bez okna s kamarádem funguje jako řazení zjednodušeného posuvníku. Například ovládací prvek karta někdy zobrazí ovládací prvek číselníku, který uživateli umožňuje přejít na další karty v zobrazení.

Další informace o použití `CSpinButtonCtrl`naleznete v tématu [Controls](../../mfc/controls-mfc.md) and [using atributu CSpinButtonCtrl](../../mfc/using-cspinbuttonctrl.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CSpinButtonCtrl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxcmn. h

##  <a name="create"></a>Atributu CSpinButtonCtrl:: Create

Vytvoří ovládací prvek číselníku a připojí ho k `CSpinButtonCtrl` objektu..

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*dwStyle*<br/>
Určuje styl ovládacího prvku číselníku. Použijte libovolnou kombinaci stylů ovládacího prvku číselník pro ovládací prvek. Tyto styly jsou popsány v následujících [stylech ovládacích prvků](/windows/win32/Controls/up-down-control-styles) v Windows SDK.

*OBD*<br/>
Určuje velikost a polohu ovládacího prvku číselníku. Může to být buď objekt [CRect](../../atl-mfc-shared/reference/crect-class.md) , nebo struktura [Rect](/previous-versions/dd162897\(v=vs.85\))

*pParentWnd*<br/>
Ukazatel na nadřazené okno ovládacího prvku tlačítko, obvykle a `CDialog`. Nesmí mít hodnotu NULL.

*nID*<br/>
Určuje ID ovládacího prvku číselníku.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byla inicializace úspěšná; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Nejprve vytvoříte `Create` `CSpinButtonCtrl` objekt ve dvou krocích, zavoláte konstruktor a potom zavoláte, čímž se vytvoří ovládací prvek číselníku a připojí se k objektu. `CSpinButtonCtrl`

Chcete-li vytvořit ovládací prvek číselníku s rozšířenými styly oken, zavolejte [atributu CSpinButtonCtrl:: CreateEx](#createex) namísto `Create`.

##  <a name="createex"></a>Atributu CSpinButtonCtrl:: CreateEx

Vytvoří ovládací prvek (podřízené okno) a přidruží ho k `CSpinButtonCtrl` objektu.

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
Určuje styl ovládacího prvku číselníku. Použijte libovolnou kombinaci stylů ovládacího prvku číselník pro ovládací prvek. Tyto styly jsou popsány v následujících [stylech ovládacích prvků](/windows/win32/Controls/up-down-control-styles) v Windows SDK.

*OBD*<br/>
Odkaz na strukturu [Rect](/previous-versions/dd162897\(v=vs.85\)) popisující velikost a umístění okna, které má být vytvořeno, v souřadnicích klienta *pParentWnd*.

*pParentWnd*<br/>
Ukazatel na okno, které je nadřazený ovládacímu prvku.

*nID*<br/>
ID podřízeného okna ovládacího prvku

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Použijte `CreateEx` místo příkaz [vytvořit](#create) pro použití rozšířených stylů Windows, které jsou určené WS_EX_ rozšířeným stylem Windows.

##  <a name="cspinbuttonctrl"></a>Atributu CSpinButtonCtrl:: atributu CSpinButtonCtrl

`CSpinButtonCtrl` Vytvoří objekt.

```
CSpinButtonCtrl();
```

##  <a name="getaccel"></a>Atributu CSpinButtonCtrl:: GetAccel

Načte informace o akceleraci pro ovládací prvek číselníku.

```
UINT GetAccel(
    int nAccel,
    UDACCEL* pAccel) const;
```

### <a name="parameters"></a>Parametry

*nAccel*<br/>
Počet elementů v poli určeném parametrem *pAccel*.

*pAccel*<br/>
Ukazatel na pole [UDACCEL](/windows/win32/api/commctrl/ns-commctrl-udaccel) struktury, které obdrží informace o akceleraci.

### <a name="return-value"></a>Návratová hodnota

Počet načtených struktur akcelerátoru

##  <a name="getbase"></a>Atributu CSpinButtonCtrl:: GetBase

Načte aktuální základ ovládacího prvku číselníku.

```
UINT GetBase() const;
```

### <a name="return-value"></a>Návratová hodnota

Aktuální základní hodnota.

##  <a name="getbuddy"></a>Atributu CSpinButtonCtrl:: getkamarád

Načte ukazatel na aktuální kamarád okno.

```
CWnd* GetBuddy() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na aktuální okno kamaráda.

##  <a name="getpos"></a>Atributu CSpinButtonCtrl:: GetPos

Načte aktuální pozici ovládacího prvku číselníku.

```
int GetPos() const;  int GetPos32(LPBOOL lpbError = NULL) const;
```

### <a name="parameters"></a>Parametry

*lpbError*<br/>
Ukazatel na logickou hodnotu, která je nastavena na hodnotu nula, pokud je hodnota úspěšně načtena nebo není nula, pokud dojde k chybě. Pokud je tento parametr nastaven na hodnotu NULL, chyby nejsou hlášeny.

### <a name="return-value"></a>Návratová hodnota

První verze vrátí 16bitové aktuální pozici v aplikaci s nízkým pořadím. Slovo s vysokým pořadím je nenulové, pokud došlo k chybě.

Druhá verze vrátí 32 bitovou pozici.

### <a name="remarks"></a>Poznámky

Když zpracovává vrácenou hodnotu, ovládací prvek aktualizuje svou aktuální polohu na základě titulku okna kamarád. Ovládací prvek vrátí chybu, pokud není k dispozici žádné okno pro kamarády, nebo pokud titulek určuje neplatnou nebo mimo rozsah hodnoty.

##  <a name="getrange"></a>Atributu CSpinButtonCtrl:: GetRange

Načte horní a dolní meze (rozsah) pro ovládací prvek číselníku.

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

*malým*<br/>
Odkaz na celé číslo, které obdrží dolní limit ovládacího prvku.

*upper*<br/>
Odkaz na celé číslo, které získá horní limit ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

První verze vrací hodnotu 32 obsahující horní a dolní meze. Slovo s nižším pořadím je horním limitem pro ovládací prvek a slovo s vyšším pořadím je dolní limit.

### <a name="remarks"></a>Poznámky

Členská funkce `GetRange32` Získá rozsah ovládacího prvku číselníku jako 32 celé číslo.

##  <a name="setaccel"></a>Atributu CSpinButtonCtrl:: SetAccel

Nastaví zrychlení pro ovládací prvek číselníku.

```
BOOL SetAccel(
    int nAccel,
    UDACCEL* pAccel);
```

### <a name="parameters"></a>Parametry

*nAccel*<br/>
Počet [UDACCEL](/windows/win32/api/commctrl/ns-commctrl-udaccel) struktur určených *pAccel*.

*pAccel*<br/>
Ukazatel na pole UDACCEL struktury, které obsahují informace o akceleraci. Prvky by měly být seřazeny vzestupně podle `nSec` členů.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

##  <a name="setbase"></a>Atributu CSpinButtonCtrl:: SetBase

Nastaví základ pro ovládací prvek číselníku.

```
int SetBase(int nBase);
```

### <a name="parameters"></a>Parametry

*nBase*<br/>
Nová základní hodnota pro ovládací prvek Pro šestnáctkové číslo může být desítkový nebo 16.

### <a name="return-value"></a>Návratová hodnota

Předchozí základní hodnota, je-li úspěšná, nebo nula, pokud je zadána neplatná základ.

### <a name="remarks"></a>Poznámky

Základní hodnota určuje, zda se v okně kamaráda zobrazují čísla v desítkové nebo šestnáctkové čísle. Šestnáctková čísla jsou vždycky bez znaménka; desetinná čísla jsou podepsaná.

##  <a name="setbuddy"></a>Atributu CSpinButtonCtrl:: SetBuddy

Nastaví kamarád okno pro ovládací prvek číselníku.

```
CWnd* SetBuddy(CWnd* pWndBuddy);
```

### <a name="parameters"></a>Parametry

*pWndBuddy*<br/>
Ukazatel na nové okno kamaráda.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na předchozí okno kamaráda.

### <a name="remarks"></a>Poznámky

Číselník je téměř vždy přidružen k jinému oknu, například k ovládacímu prvku pro úpravy, který zobrazuje nějaký obsah. Toto druhé okno se nazývá "kamarád" číselníku.

##  <a name="setpos"></a>Atributu CSpinButtonCtrl:: SetPos

Nastaví aktuální pozici ovládacího prvku číselníku.

```
int SetPos(int nPos);
int SetPos32(int nPos);
```

### <a name="parameters"></a>Parametry

*nPos*<br/>
Nová pozice ovládacího prvku Tato hodnota musí být v rozsahu určeném horním a dolním omezením ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Předchozí pozice (16bitová přesnost pro `SetPos`, 32-bit přesnosti pro `SetPos32`).

### <a name="remarks"></a>Poznámky

`SetPos32`Nastaví 32 bitovou pozici.

##  <a name="setrange"></a>Atributu CSpinButtonCtrl:: SetRange

Nastaví horní a dolní meze (rozsah) pro ovládací prvek číselníku.

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
Horní a dolní meze ovládacího prvku. `SetRange`V případě nemůže být žádná hodnota větší než UD_MAXVAL nebo menší než UD_MINVAL; rozdíl mezi dvěma omezeními nesmí překročit UD_MAXVAL. `SetRange32`neomezuje omezení; Použijte jakákoli celá čísla.

### <a name="remarks"></a>Poznámky

Členská funkce `SetRange32` nastavuje rozsah 32 pro ovládací prvek číselníku.

> [!NOTE]
>  Výchozí rozsah pro tlačítko číselníku má maximální hodnotu nula (0) a minimální hodnotu nastavenou na 100. Vzhledem k tomu, že maximální hodnota je menší než minimální hodnota, kliknutím na šipku nahoru zmenšete polohu a kliknutím na šipku dolů ji zvýšíte. Použijte `CSpinButtonCtrl::SetRange` k úpravě těchto hodnot.

## <a name="see-also"></a>Viz také:

[CMNCTRL2 Sample MFC](../../overview/visual-cpp-samples.md)<br/>
[CWnd – třída](../../mfc/reference/cwnd-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CSliderCtrl – třída](../../mfc/reference/csliderctrl-class.md)
