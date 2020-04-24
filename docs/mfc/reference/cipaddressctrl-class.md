---
title: Třída CIPAddressCtrl
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
ms.openlocfilehash: 0613dea766b022acf140a82bb4b01784793c2589
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754960"
---
# <a name="cipaddressctrl-class"></a>Třída CIPAddressCtrl

Poskytuje funkce společného ovládacího prvku adresy IP systému Windows.

## <a name="syntax"></a>Syntaxe

```
class CIPAddressCtrl : public CWnd
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CIPAddressCtrl::CIPAddressCtrl](#cipaddressctrl)|Vytvoří `CIPAddressCtrl` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CIPAddressCtrl::Vymazat adresu](#clearaddress)|Vymaže obsah ovládacího prvku IP address.|
|[CIPAddressCtrl::Vytvořit](#create)|Vytvoří ovládací prvek IP adresy a `CIPAddressCtrl` připojí jej k objektu.|
|[CIPAddressCtrl::CreateEx](#createex)|Vytvoří ovládací prvek IP Address se zadanými rozšířenými styly systému Windows a připojí jej k objektu. `CIPAddressCtrl`|
|[CIPAddressCtrl::GetAddress](#getaddress)|Načte hodnoty adres pro všechna čtyři pole v ovládacím prvku IP address.|
|[CIPAddressCtrl::isblank](#isblank)|Určuje, zda jsou všechna pole v ovládacím prvku IP adresy prázdná.|
|[CIPAddressCtrl::SetAddress](#setaddress)|Nastaví hodnoty adres pro všechna čtyři pole v ovládacím prvku IP Address Control.|
|[CIPAddressCtrl::SetFieldFocus](#setfieldfocus)|Nastaví fokus klávesnice na zadané pole v ovládacím prvku IP Address Control.|
|[CIPAddressCtrl::SetFieldRange](#setfieldrange)|Nastaví rozsah v zadaném poli v ovládacím prvku IP address.|

## <a name="remarks"></a>Poznámky

Ovládací prvek IP Adresa, ovládací prvek podobný editačnímu ovládacímu prvku, umožňuje zadat a manipulovat s ní ve formátu IP protokolu .

Tento ovládací prvek `CIPAddressCtrl` (a tedy třída) je k dispozici pouze pro programy spuštěné v aplikaci Microsoft Internet Explorer 4.0 a novější. Budou také k dispozici v budoucích verzích systému Windows a Windows NT.

Obecnější informace o ovládacím prvku IP address naleznete v tématu [Ovládací prvky IP adres](/windows/win32/Controls/ip-address-controls) v sadě Windows SDK.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

`CIPAddressCtrl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxcmn.h

## <a name="cipaddressctrlcipaddressctrl"></a><a name="cipaddressctrl"></a>CIPAddressCtrl::CIPAddressCtrl

Vytvoří `CIPAddressCtrl` objekt.

```
CIPAddressCtrl();
```

## <a name="cipaddressctrlclearaddress"></a><a name="clearaddress"></a>CIPAddressCtrl::Vymazat adresu

Vymaže obsah ovládacího prvku IP address.

```cpp
void ClearAddress();
```

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování [IPM_CLEARADDRESS](/windows/win32/Controls/ipm-clearaddress)zprávy Win32 , jak je popsáno v sadě Windows SDK.

## <a name="cipaddressctrlcreate"></a><a name="create"></a>CIPAddressCtrl::Vytvořit

Vytvoří ovládací prvek IP adresy a `CIPAddressCtrl` připojí jej k objektu.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*dwStyl*<br/>
Styl ovládacího prvku IP adresa. Použijte kombinaci stylů oken. Je nutné zahrnout styl WS_CHILD, protože ovládací prvek musí být podřízeným oknem. Seznam stylů oken najdete v tématu [CreateWindow](/windows/win32/api/winuser/nf-winuser-createwindoww) v sadě Windows SDK.

*Rect*<br/>
Odkaz na velikost a umístění ovládacího prvku IP adresy. Může to být buď [CRect](../../atl-mfc-shared/reference/crect-class.md) objekt nebo [RECT](/windows/win32/api/windef/ns-windef-rect) struktury.

*pParentWnd*<br/>
Ukazatel na nadřazené okno ovládacího prvku IP. Nesmí být null.

*Nid*<br/>
ID ovládacího prvku IP adres.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byla inicializace úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Objekt vytvoříte ve `CIPAddressCtrl` dvou krocích.

1. Volání konstruktoru, který `CIPAddressCtrl` vytvoří objekt.

1. Volání `Create`, které vytvoří ovládací prvek IP adresy.

Pokud chcete použít rozšířené styly oken s ovládacím `Create`prvkem, zavolejte [CreateEx](#createex) místo .

## <a name="cipaddressctrlcreateex"></a><a name="createex"></a>CIPAddressCtrl::CreateEx

Volání této funkce vytvořit ovládací prvek (podřízené okno) a přidružit k objektu. `CIPAddressCtrl`

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
Styl ovládacího prvku IP adresa. Použijte kombinaci stylů oken. Je nutné zahrnout styl WS_CHILD, protože ovládací prvek musí být podřízeným oknem. Seznam stylů oken najdete v tématu [CreateWindow](/windows/win32/api/winuser/nf-winuser-createwindoww) v sadě Windows SDK.

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

## <a name="cipaddressctrlgetaddress"></a><a name="getaddress"></a>CIPAddressCtrl::GetAddress

Načte hodnoty adres pro všechna čtyři pole v ovládacím prvku IP address.

```
int GetAddress(
    BYTE& nField0,
    BYTE& nField1,
    BYTE& nField2,
    BYTE& nField3);

int GetAddress(DWORD& dwAddress);
```

### <a name="parameters"></a>Parametry

*nPole0*<br/>
Odkaz na hodnotu pole 0 z zabalené ip adresy.

*nPole1*<br/>
Odkaz na hodnotu pole 1 z zabalené IP adresy.

*nPole2*<br/>
Odkaz na hodnotu pole 2 z zabalené IP adresy.

*nPole3*<br/>
Odkaz na hodnotu pole 3 z zabalené IP adresy.

*adresa dw*<br/>
Odkaz na adresu hodnoty DWORD, která obdrží adresu IP. Viz **Poznámky** pro tabulku, která ukazuje, jak *je vyplněna dwAddress.*

### <a name="return-value"></a>Návratová hodnota

Počet neprázdných polí v ovládacím prvku IP Address Control.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [IPM_GETADDRESS](/windows/win32/Controls/ipm-getaddress), jak je popsáno v sadě Windows SDK. V prvním prototypu výše, čísla v polích 0 až 3 ovládacího prvku, čtení zleva doprava, respektive naplnit čtyři parametry. Ve druhém prototypu výše *dwAddress* je naplněn takto.

|Pole|Bity obsahující hodnotu pole|
|-----------|-------------------------------------|
|0|24 až 31|
|1|16 až 23|
|2|8 až 15|
|3|0 až 7|

## <a name="cipaddressctrlisblank"></a><a name="isblank"></a>CIPAddressCtrl::isblank

Určuje, zda jsou všechna pole v ovládacím prvku IP adresy prázdná.

```
BOOL IsBlank() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud jsou všechna pole řízení adresy IP prázdná; jinak 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování [zprávy](/windows/win32/Controls/ipm-isblank)Win32 IPM_ISBLANK , jak je popsáno v sadě Windows SDK.

## <a name="cipaddressctrlsetaddress"></a><a name="setaddress"></a>CIPAddressCtrl::SetAddress

Nastaví hodnoty adres pro všechna čtyři pole v ovládacím prvku IP Address Control.

```cpp
void SetAddress(
    BYTE nField0,
    BYTE nField1,
    BYTE nField2,
    BYTE nField3);

void SetAddress(DWORD dwAddress);
```

### <a name="parameters"></a>Parametry

*nPole0*<br/>
Hodnota pole 0 z zabalené IP adresy.

*nPole1*<br/>
Hodnota pole 1 z zabalené IP adresy.

*nPole2*<br/>
Hodnota pole 2 z zabalené IP adresy.

*nPole3*<br/>
Hodnota pole 3 z zabalené IP adresy.

*adresa dw*<br/>
Hodnota DWORD, která obsahuje novou ADRESU IP. Viz **Poznámky** pro tabulku, která ukazuje, jak je vyplněna hodnota DWORD.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování [IPM_SETADDRESS](/windows/win32/Controls/ipm-setaddress)zprávy Win32 , jak je popsáno v sadě Windows SDK. V prvním prototypu výše, čísla v polích 0 až 3 ovládacího prvku, čtení zleva doprava, respektive naplnit čtyři parametry. Ve druhém prototypu výše *dwAddress* je naplněn takto.

|Pole|Bity obsahující hodnotu pole|
|-----------|-------------------------------------|
|0|24 až 31|
|1|16 až 23|
|2|8 až 15|
|3|0 až 7|

## <a name="cipaddressctrlsetfieldfocus"></a><a name="setfieldfocus"></a>CIPAddressCtrl::SetFieldFocus

Nastaví fokus klávesnice na zadané pole v ovládacím prvku IP Address Control.

```cpp
void SetFieldFocus(WORD nField);
```

### <a name="parameters"></a>Parametry

*nPole*<br/>
Index pole založený na nule, na který by měl být nastaven fokus. Pokud je tato hodnota větší než počet polí, je fokus nastaven na první prázdné pole. Pokud nejsou všechna pole prázdná, je fokus nastaven na první pole.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování [IPM_SETFOCUS](/windows/win32/Controls/ipm-setfocus)zprávy Win32 , jak je popsáno v sadě Windows SDK.

## <a name="cipaddressctrlsetfieldrange"></a><a name="setfieldrange"></a>CIPAddressCtrl::SetFieldRange

Nastaví rozsah v zadaném poli v ovládacím prvku IP address.

```cpp
void SetFieldRange(
    int nField,
    BYTE nLower,
    BYTE nUpper);
```

### <a name="parameters"></a>Parametry

*nPole*<br/>
Index pole založený na nule, na který bude rozsah použit.

*nNižší*<br/>
Odkaz na celé číslo, které přijímá dolní limit zadaného pole v tomto řízení adres IP.

*nHorní*<br/>
Odkaz na celé číslo, které přijímá horní limit zadaného pole v tomto řízení adres IP.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování [IPM_SETRANGE](/windows/win32/Controls/ipm-setrange)zprávy Win32 , jak je popsáno v sadě Windows SDK. Pomocí dvou parametrů *nLower* a *nUpper*, k označení dolní a horní hranice pole namísto *wRange* parametr použitý se zprávou Win32.

## <a name="see-also"></a>Viz také

[CWnd – třída](../../mfc/reference/cwnd-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)
