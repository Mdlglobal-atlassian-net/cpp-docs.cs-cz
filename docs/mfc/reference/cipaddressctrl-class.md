---
title: Cipaddressctrl – třída
ms.date: 11/04/2016
f1_keywords:
- CIPAddressCtrl
- AFXCMN/CIPAddressCtrl
- AFXCMN/CIPAddressCtrl::CIPAddressCtrl
- AFXCMN/CIPAddressCtrl::ClearAddress
- AFXCMN/CIPAddressCtrl::Create
- AFXCMN/CIPAddressCtrl::CreateEx
- AFXCMN/CIPAddressCtrl::GetAddress
- AFXCMN/CIPAddressCtrl::IsBlank
- AFXCMN/CIPAddressCtrl::SetAddress
- AFXCMN/CIPAddressCtrl::SetFieldFocus
- AFXCMN/CIPAddressCtrl::SetFieldRange
helpviewer_keywords:
- CIPAddressCtrl [MFC], CIPAddressCtrl
- CIPAddressCtrl [MFC], ClearAddress
- CIPAddressCtrl [MFC], Create
- CIPAddressCtrl [MFC], CreateEx
- CIPAddressCtrl [MFC], GetAddress
- CIPAddressCtrl [MFC], IsBlank
- CIPAddressCtrl [MFC], SetAddress
- CIPAddressCtrl [MFC], SetFieldFocus
- CIPAddressCtrl [MFC], SetFieldRange
ms.assetid: 9764d2f4-cb14-4ba8-b799-7f57a55a47c6
ms.openlocfilehash: fe5503eb78954bf39a135cd0e4acda6c37fc5fa9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50568698"
---
# <a name="cipaddressctrl-class"></a>Cipaddressctrl – třída

Poskytuje funkce pro Windows běžný ovládací prvek adresy IP.

## <a name="syntax"></a>Syntaxe

```
class CIPAddressCtrl : public CWnd
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CIPAddressCtrl::CIPAddressCtrl](#cipaddressctrl)|Vytvoří `CIPAddressCtrl` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CIPAddressCtrl::ClearAddress](#clearaddress)|Vymaže obsah ovládací prvek adresy IP.|
|[CIPAddressCtrl::Create](#create)|Vytvoří ovládací prvek adresy IP a připojí ho k `CIPAddressCtrl` objektu.|
|[CIPAddressCtrl::CreateEx](#createex)|Vytvoří ovládací prvek adresy IP se zadaným rozšířené styly Windows a připojí ho k `CIPAddressCtrl` objektu.|
|[CIPAddressCtrl::GetAddress](#getaddress)|Načte hodnoty adres pro všechny čtyři pole ve správě IP adres.|
|[CIPAddressCtrl::IsBlank](#isblank)|Určuje, zda všechna pole v ovládacím prvku IP adresa prázdná.|
|[CIPAddressCtrl::SetAddress](#setaddress)|Nastaví hodnoty adres pro všechny čtyři pole ve správě IP adres.|
|[CIPAddressCtrl::SetFieldFocus](#setfieldfocus)|Nastaví fokus klávesnice pro ovládací prvek adresy IP v zadaném poli.|
|[CIPAddressCtrl::SetFieldRange](#setfieldrange)|Nastaví rozsah v zadaném poli ve správě IP adres.|

## <a name="remarks"></a>Poznámky

Ovládací prvek adresy IP, ovládací prvek pro úpravy, podobně jako můžete zadat a manipulaci s číselnou adresu ve formátu Internet Protocol (IP).

Tento ovládací prvek (a tedy `CIPAddressCtrl` třídy) je dostupná jenom pro programy spuštěné v rámci aplikace Microsoft Internet Explorer 4.0 nebo novější. Také budou k dispozici v budoucích verzích Windows a Windows NT.

Další obecné informace o ovládací prvek adresy IP, naleznete v tématu [IP adresu řídí](/windows/desktop/Controls/ip-address-controls) v sadě Windows SDK.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CIPAddressCtrl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxcmn.h

##  <a name="cipaddressctrl"></a>  CIPAddressCtrl::CIPAddressCtrl

Vytvoří `CIPAddressCtrl` objektu.

```
CIPAddressCtrl();
```

##  <a name="clearaddress"></a>  CIPAddressCtrl::ClearAddress

Vymaže obsah ovládací prvek adresy IP.

```
void ClearAddress();
```

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [IPM_CLEARADDRESS](/windows/desktop/Controls/ipm-clearaddress), jak je popsáno v sadě Windows SDK.

##  <a name="create"></a>  CIPAddressCtrl::Create

Vytvoří ovládací prvek adresy IP a připojí ho k `CIPAddressCtrl` objektu.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*dwStyle*<br/>
Styl ovládací prvek adresy IP. Použijte kombinaci styly oken. WS_CHILD styl musí obsahovat, protože ovládací prvek musí být podřízené okno. Zobrazit [CreateWindow](/windows/desktop/api/winuser/nf-winuser-createwindowa) v sadě Windows SDK pro seznam windows styly.

*Rect*<br/>
Odkaz na ovládací prvek adresy IP velikost a umístění. Může být buď [crect –](../../atl-mfc-shared/reference/crect-class.md) objektu nebo [RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897) struktury.

*pParentWnd*<br/>
Ukazatel IP adresu nadřazené okno ovládacího prvku. Nesmí být NULL.

*nID*<br/>
ID ovládací prvek adresy IP.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud se inicializace byla úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Můžete vytvořit `CIPAddressCtrl` objektu ve dvou krocích.

1. Volání konstruktoru, který vytvoří `CIPAddressCtrl` objektu.

1. Volání `Create`, což vytvoří ovládací prvek adresy IP.

Pokud chcete použít rozšířené windows styly ovládacího prvku, zavolejte [CreateEx](#createex) místo `Create`.

##  <a name="createex"></a>  CIPAddressCtrl::CreateEx

Voláním této funkce vytvoření ovládacího prvku (podřízené okno) a přidružte jej k `CIPAddressCtrl` objektu.

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
Styl ovládací prvek adresy IP. Použijte kombinaci styly oken. WS_CHILD styl musí obsahovat, protože ovládací prvek musí být podřízené okno. Zobrazit [CreateWindow](/windows/desktop/api/winuser/nf-winuser-createwindowa) v sadě Windows SDK pro seznam windows styly.

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

##  <a name="getaddress"></a>  CIPAddressCtrl::GetAddress

Načte hodnoty adres pro všechny čtyři pole ve správě IP adres.

```
int GetAddress(
    BYTE& nField0,
    BYTE& nField1,
    BYTE& nField2,
    BYTE& nField3);

int GetAddress(DWORD& dwAddress);
```

### <a name="parameters"></a>Parametry

*nField0*<br/>
Odkaz na hodnotu pole 0 z komprimovat komprimovaný objekt IP adresy.

*nField1*<br/>
Odkaz na hodnotu pole 1 z komprimovat komprimovaný objekt IP adresy.

*nField2*<br/>
Odkaz na hodnotu pole 2 z komprimovat komprimovaný objekt IP adresy.

*nField3*<br/>
Odkaz na hodnotu pole 3 z komprimovat komprimovaný objekt IP adresy.

*dwAddress*<br/>
Odkaz na adresu hodnotu DWORD, která obdrží IP adresu. Zobrazit **poznámky** pro tabulku, která ukazuje, jak *dwAddress* zaplněný.

### <a name="return-value"></a>Návratová hodnota

Počet neprázdných polí ve správě IP adres.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [IPM_GETADDRESS](/windows/desktop/Controls/ipm-getaddress), jak je popsáno v sadě Windows SDK. V první prototypu výše uvedených čísel v polích 0 až 3 z ovládacího prvku, přečtěte si zleva doprava v uvedeném pořadí, naplnění čtyři parametry. V druhém prototypu výše *dwAddress* se vyplní následujícím způsobem.

|Pole|Služba BITS obsahující hodnotu pole|
|-----------|-------------------------------------|
|0|24 do 31.|
|1|16 až 23|
|2|8 až 15|
|3|0 až 7|

##  <a name="isblank"></a>  CIPAddressCtrl::IsBlank

Určuje, zda všechna pole v ovládacím prvku IP adresa prázdná.

```
BOOL IsBlank() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud všechna pole ovládací prvek adresy IP jsou prázdná. jinak 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [IPM_ISBLANK](/windows/desktop/Controls/ipm-isblank), jak je popsáno v sadě Windows SDK.

##  <a name="setaddress"></a>  CIPAddressCtrl::SetAddress

Nastaví hodnoty adres pro všechny čtyři pole ve správě IP adres.

```
void SetAddress(
    BYTE nField0,
    BYTE nField1,
    BYTE nField2,
    BYTE nField3);

void SetAddress(DWORD dwAddress);
```

### <a name="parameters"></a>Parametry

*nField0*<br/>
Hodnota pole 0 z komprimovat komprimovaný objekt IP adresy.

*nField1*<br/>
Hodnota pole 1 z komprimovat komprimovaný objekt IP adresy.

*nField2*<br/>
Hodnota pole 2 z komprimovat komprimovaný objekt IP adresy.

*nField3*<br/>
Hodnota pole 3 z komprimovat komprimovaný objekt IP adresy.

*dwAddress*<br/>
Hodnota DWORD, který obsahuje novou IP adresu. Zobrazit **poznámky** pro tabulku, která ukazuje, jak je vyplněné hodnoty DWORD.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [IPM_SETADDRESS](/windows/desktop/Controls/ipm-setaddress), jak je popsáno v sadě Windows SDK. V první prototypu výše uvedených čísel v polích 0 až 3 z ovládacího prvku, přečtěte si zleva doprava v uvedeném pořadí, naplnění čtyři parametry. V druhém prototypu výše *dwAddress* se vyplní následujícím způsobem.

|Pole|Služba BITS obsahující hodnotu pole|
|-----------|-------------------------------------|
|0|24 do 31.|
|1|16 až 23|
|2|8 až 15|
|3|0 až 7|

##  <a name="setfieldfocus"></a>  CIPAddressCtrl::SetFieldFocus

Nastaví fokus klávesnice pro ovládací prvek adresy IP v zadaném poli.

```
void SetFieldFocus(WORD nField);
```

### <a name="parameters"></a>Parametry

*nPole*<br/>
Index založený na nule pole, na kterou by měl nastavit fokus. Pokud je tato hodnota větší než počet polí, je nastaven fokus na první prázdné pole. Pokud všechna pole jsou prázdná, je nastaven fokus na první pole.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [IPM_SETFOCUS](/windows/desktop/Controls/ipm-setfocus), jak je popsáno v sadě Windows SDK.

##  <a name="setfieldrange"></a>  CIPAddressCtrl::SetFieldRange

Nastaví rozsah v zadaném poli ve správě IP adres.

```
void SetFieldRange(
    int nField,
    BYTE nLower,
    BYTE nUpper);
```

### <a name="parameters"></a>Parametry

*nPole*<br/>
Index založený na nule pole ke které se použijí rozsahu.

*nLower*<br/>
Odkaz na celé číslo, které přijímají dolní mez pole zadané v tomto ovládacím prvku IP adresu.

*nUpper*<br/>
Odkaz na celé číslo, které přijímají horní limit počtu určené pole v tomto ovládacím prvku IP adresu.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [IPM_SETRANGE](/windows/desktop/Controls/ipm-setrange), jak je popsáno v sadě Windows SDK. Použít dva parametry *nLower* a *nUpper*, pro indikaci horní a dolní mez pole, nikoli *wRange* parametr používaný s touto zprávou Win32.

## <a name="see-also"></a>Viz také

[CWnd – třída](../../mfc/reference/cwnd-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)

