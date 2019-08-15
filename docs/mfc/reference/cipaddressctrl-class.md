---
title: CIPAddressCtrl – třída
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
ms.openlocfilehash: fe8e3109b110c27ab32dc1a4f9a132f1e1c18638
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505819"
---
# <a name="cipaddressctrl-class"></a>CIPAddressCtrl – třída

Poskytuje funkce pro běžný ovládací prvek IP adres Windows.

## <a name="syntax"></a>Syntaxe

```
class CIPAddressCtrl : public CWnd
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CIPAddressCtrl::CIPAddressCtrl](#cipaddressctrl)|`CIPAddressCtrl` Vytvoří objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CIPAddressCtrl::ClearAddress](#clearaddress)|Vymaže obsah ovládacího prvku IP adresa.|
|[CIPAddressCtrl::Create](#create)|Vytvoří ovládací prvek IP adresa a připojí ho k `CIPAddressCtrl` objektu.|
|[CIPAddressCtrl::CreateEx](#createex)|Vytvoří ovládací prvek IP adresa se zadanými rozšířenými styly Windows a připojí ho k `CIPAddressCtrl` objektu.|
|[CIPAddressCtrl::GetAddress](#getaddress)|Načte hodnoty adres pro všechna čtyři pole v ovládacím prvku IP adresa.|
|[CIPAddressCtrl::IsBlank](#isblank)|Určuje, zda jsou všechna pole v ovládacím prvku IP adresa prázdná.|
|[CIPAddressCtrl::SetAddress](#setaddress)|Nastaví hodnoty adres pro všechna čtyři pole v ovládacím prvku IP adresa.|
|[CIPAddressCtrl::SetFieldFocus](#setfieldfocus)|Nastaví fokus klávesnice na zadané pole v ovládacím prvku IP adresa.|
|[CIPAddressCtrl::SetFieldRange](#setfieldrange)|Nastaví rozsah v určeném poli v ovládacím prvku IP adresa.|

## <a name="remarks"></a>Poznámky

Ovládací prvek IP adresa, ovládací prvek podobný ovládacímu prvku pro úpravy, umožňuje zadat a manipulovat s numerickou adresou ve formátu Internet Protocol (IP).

Tento ovládací prvek (a `CIPAddressCtrl` třída) je k dispozici pouze pro programy, které jsou spuštěny v aplikaci Microsoft Internet Explorer 4,0 a novější. Budou taky dostupné v budoucích verzích Windows a Windows NT.

Obecnější informace o ovládacím prvku IP adresa najdete v tématu [ovládací prvky IP adresy](/windows/win32/Controls/ip-address-controls) v Windows SDK.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CIPAddressCtrl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxcmn. h

##  <a name="cipaddressctrl"></a>CIPAddressCtrl::CIPAddressCtrl

`CIPAddressCtrl` Vytvoří objekt.

```
CIPAddressCtrl();
```

##  <a name="clearaddress"></a>  CIPAddressCtrl::ClearAddress

Vymaže obsah ovládacího prvku IP adresa.

```
void ClearAddress();
```

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [IPM_CLEARADDRESS](/windows/win32/Controls/ipm-clearaddress), jak je popsáno v Windows SDK.

##  <a name="create"></a>  CIPAddressCtrl::Create

Vytvoří ovládací prvek IP adresa a připojí ho k `CIPAddressCtrl` objektu.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*dwStyle*<br/>
Styl ovládacího prvku IP adresa. Použijte kombinaci stylů oken. Musíte zahrnout styl WS_CHILD, protože ovládací prvek musí být podřízené okno. Seznam stylů Windows najdete v části [CreateWindow](/windows/win32/api/winuser/nf-winuser-createwindoww) v Windows SDK.

*OBD*<br/>
Odkaz na velikost a pozici ovládacího prvku IP adresa. Může to být buď objekt [CRect](../../atl-mfc-shared/reference/crect-class.md) , nebo struktura [Rect](/previous-versions/dd162897\(v=vs.85\)) .

*pParentWnd*<br/>
Ukazatel na nadřazené okno ovládacího prvku IP adresa. Nesmí mít hodnotu NULL.

*nID*<br/>
ID ovládacího prvku IP adresa.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byla inicializace úspěšná; v opačném případě 0.

### <a name="remarks"></a>Poznámky

`CIPAddressCtrl` Vytvoříte objekt ve dvou krocích.

1. Zavolejte konstruktor, který vytvoří `CIPAddressCtrl` objekt.

1. Zavolejte `Create`, čímž se vytvoří ovládací prvek IP adresa.

Chcete-li použít rozšířené styly systému Windows s ovládacím prvkem, zavolejte [CreateEx](#createex) místo `Create`.

##  <a name="createex"></a>  CIPAddressCtrl::CreateEx

Voláním této funkce vytvořte ovládací prvek (podřízené okno) a přidružte jej `CIPAddressCtrl` k objektu.

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
Styl ovládacího prvku IP adresa. Použijte kombinaci stylů oken. Musíte zahrnout styl WS_CHILD, protože ovládací prvek musí být podřízené okno. Seznam stylů Windows najdete v části [CreateWindow](/windows/win32/api/winuser/nf-winuser-createwindoww) v Windows SDK.

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

##  <a name="getaddress"></a>  CIPAddressCtrl::GetAddress

Načte hodnoty adres pro všechna čtyři pole v ovládacím prvku IP adresa.

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
Odkaz na hodnotu pole 0 ze zkomprimované IP adresy.

*nField1*<br/>
Odkaz na hodnotu pole 1 z komprimované IP adresy.

*nField2*<br/>
Odkaz na hodnotu pole 2 z komprimované IP adresy.

*nField3*<br/>
Odkaz na hodnotu pole 3 z komprimované IP adresy.

*dwAddress*<br/>
Odkaz na adresu hodnoty DWORD, která obdrží IP adresu. Viz **poznámky** pro tabulku, která ukazuje, jak je vyplněný *dwAddress* .

### <a name="return-value"></a>Návratová hodnota

Počet neprázdných polí v ovládacím prvku IP adresa.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [IPM_GETADDRESS](/windows/win32/Controls/ipm-getaddress), jak je popsáno v Windows SDK. V prvním prototypu výše se čísla v polích 0 až 3 v ovládacím prvku přečtou zleva doprava a naplní čtyři parametry. Ve druhém prototypu výše se *dwAddress* vyplní následujícím způsobem.

|Pole|Bity obsahující hodnotu pole|
|-----------|-------------------------------------|
|0|24 až 31|
|1|16 až 23|
|2|8 až 15|
|3|0 až 7|

##  <a name="isblank"></a>  CIPAddressCtrl::IsBlank

Určuje, zda jsou všechna pole v ovládacím prvku IP adresa prázdná.

```
BOOL IsBlank() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud jsou všechna pole řízení IP adres prázdná; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [IPM_ISBLANK](/windows/win32/Controls/ipm-isblank), jak je popsáno v Windows SDK.

##  <a name="setaddress"></a>  CIPAddressCtrl::SetAddress

Nastaví hodnoty adres pro všechna čtyři pole v ovládacím prvku IP adresa.

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
Hodnota pole 0 z komprimované IP adresy.

*nField1*<br/>
Hodnota pole 1 z komprimované IP adresy.

*nField2*<br/>
Hodnota pole 2 z komprimované IP adresy.

*nField3*<br/>
Hodnota pole 3 z komprimované IP adresy.

*dwAddress*<br/>
Hodnota DWORD, která obsahuje novou IP adresu. Viz **poznámky** pro tabulku, která ukazuje, jak je hodnota DWORD vyplněna.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [IPM_SETADDRESS](/windows/win32/Controls/ipm-setaddress), jak je popsáno v Windows SDK. V prvním prototypu výše se čísla v polích 0 až 3 v ovládacím prvku přečtou zleva doprava a naplní čtyři parametry. Ve druhém prototypu výše se *dwAddress* vyplní následujícím způsobem.

|Pole|Bity obsahující hodnotu pole|
|-----------|-------------------------------------|
|0|24 až 31|
|1|16 až 23|
|2|8 až 15|
|3|0 až 7|

##  <a name="setfieldfocus"></a>CIPAddressCtrl::SetFieldFocus

Nastaví fokus klávesnice na zadané pole v ovládacím prvku IP adresa.

```
void SetFieldFocus(WORD nField);
```

### <a name="parameters"></a>Parametry

*nField*<br/>
Index pole založený na nule, na který má být nastaven fokus. Pokud je tato hodnota větší než počet polí, je fokus nastaven na první prázdné pole. Pokud jsou všechna pole neprázdná, je fokus nastaven na první pole.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [IPM_SETFOCUS](/windows/win32/Controls/ipm-setfocus), jak je popsáno v Windows SDK.

##  <a name="setfieldrange"></a>CIPAddressCtrl::SetFieldRange

Nastaví rozsah v určeném poli v ovládacím prvku IP adresa.

```
void SetFieldRange(
    int nField,
    BYTE nLower,
    BYTE nUpper);
```

### <a name="parameters"></a>Parametry

*nField*<br/>
Index pole založený na nule, pro který bude rozsah použit

*nLower*<br/>
Odkaz na celé číslo, které přijímá dolní limit zadaného pole v tomto ovládacím prvku IP adresa.

*nUpper*<br/>
Odkaz na celé číslo, které přijímá horní limit zadaného pole v tomto ovládacím prvku IP adresa.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [IPM_SETRANGE](/windows/win32/Controls/ipm-setrange), jak je popsáno v Windows SDK. Použijte dva parametry, *nLower* a *nUpper*, k označení dolní a horní meze pole namísto parametru *wRange* , který se používá ve zprávě Win32.

## <a name="see-also"></a>Viz také:

[CWnd – třída](../../mfc/reference/cwnd-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)
