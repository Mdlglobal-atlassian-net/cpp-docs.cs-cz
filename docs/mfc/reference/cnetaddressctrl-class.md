---
title: CNetAddressCtrl – třída
ms.date: 11/19/2018
f1_keywords:
- CNetAddressCtrl
- AFXCMN/CNetAddressCtrl
- AFXCMN/CNetAddressCtrl::CNetAddressCtrl
- AFXCMN/CNetAddressCtrl::Create
- AFXCMN/CNetAddressCtrl::CreateEx
- AFXCMN/CNetAddressCtrl::DisplayErrorTip
- AFXCMN/CNetAddressCtrl::GetAddress
- AFXCMN/CNetAddressCtrl::GetAllowType
- AFXCMN/CNetAddressCtrl::SetAllowType
helpviewer_keywords:
- CNetAddressCtrl [MFC], CNetAddressCtrl
- CNetAddressCtrl [MFC], Create
- CNetAddressCtrl [MFC], CreateEx
- CNetAddressCtrl [MFC], DisplayErrorTip
- CNetAddressCtrl [MFC], GetAddress
- CNetAddressCtrl [MFC], GetAllowType
- CNetAddressCtrl [MFC], SetAllowType
ms.assetid: cb4c6aca-3f49-4b52-b76c-65f57096155b
ms.openlocfilehash: 5e485c22bcc4bf35f61226d84345102052689f89
ms.sourcegitcommit: 389c559918d9bfaf303d262ee5430d787a662e92
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2019
ms.locfileid: "69504537"
---
# <a name="cnetaddressctrl-class"></a>CNetAddressCtrl – třída

`CNetAddressCtrl` Třída představuje ovládací prvek síťové adresy, který můžete použít k zadání a ověření formátu adres IPv4, IPv6 a názvů DNS.

## <a name="syntax"></a>Syntaxe

```
class CNetAddressCtrl : public CEdit
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CNetAddressCtrl::CNetAddressCtrl](#cnetaddressctrl)|`CNetAddressCtrl` Vytvoří objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CNetAddressCtrl::Create](#create)|Vytvoří ovládací prvek síťové adresy se zadanými styly a připojí ho k aktuálnímu `CNetAddressCtrl` objektu.|
|[CNetAddressCtrl::CreateEx](#createex)|Vytvoří ovládací prvek síťové adresy se zadanými rozšířenými styly a připojí ho k aktuálnímu `CNetAddressCtrl` objektu.|
|[CNetAddressCtrl::DisplayErrorTip](#displayerrortip)|Pokud uživatel zadá nepodporovanou síťovou adresu v aktuálním ovládacím prvku síťové adresy, zobrazí se tip s chybovou bublinou.|
|[CNetAddressCtrl::GetAddress](#getaddress)|Načte ověřenou a analyzovanou reprezentaci síťové adresy přidružené k aktuálnímu ovládacímu prvku síťové adresy.|
|[CNetAddressCtrl::GetAllowType](#getallowtype)|Načte typ síťové adresy, kterou může aktuální ovládací prvek síťové adresy podporovat.|
|[CNetAddressCtrl::SetAllowType](#setallowtype)|Nastaví typ síťové adresy, který může podporovat aktuální ovládací prvek adresa sítě.|

## <a name="remarks"></a>Poznámky

Ovládací prvek síťová adresa ověří, zda formát adresy, kterou uživatel zadal, je správný. Ovládací prvek se ve skutečnosti nepřipojí k síťové adrese. Metoda [CNetAddressCtrl –:: SetAllowType](#setallowtype) Určuje jeden nebo více typů adres, které může metoda [CNetAddressCtrl –:: GetAddress](#getaddress) analyzovat a ověřit. Adresa může být ve formátu IPv4, IPv6 nebo pojmenované adresy pro cíl serveru, sítě, hostitele nebo zprávy všesměrového vysílání. Pokud se jedná o nesprávný formát adresy, můžete pomocí metody [CNetAddressCtrl –::D isplayerrortip](#displayerrortip) zobrazit okno se zprávou s popisem, které graficky odkazuje na textové pole ovládacího prvku síťová adresa a zobrazí se předdefinovaná chybová zpráva.

Třída je odvozena od třídy [CEdit.](../../mfc/reference/cedit-class.md) `CNetAddressCtrl` V důsledku toho poskytuje řízení síťových adres přístup ke všem zprávám ovládacího prvku Windows Edit.

Následující obrázek znázorňuje dialog, který obsahuje ovládací prvek síťové adresy. Textové pole (1) pro ovládací prvek síťová adresa obsahuje neplatnou síťovou adresu. Zpráva s popisem (2) se zobrazí, pokud není síťová adresa platná.

![Dialogové okno s ovládacím prvkem síťových adres a informačním] popisem. (../../mfc/reference/media/cnetaddctrl.png "Dialogové okno s ovládacím prvkem síťových adres a informačním") popisem.

## <a name="example"></a>Příklad

Následující příklad kódu je část dialogu, který ověřuje síťovou adresu. Obslužné rutiny událostí pro tři přepínače určují, že síťová adresa může být jedním ze tří typů adres. Uživatel zadá adresu do textového pole ovládacího prvku sítě a potom stisknutím tlačítka adresu ověří. Pokud je adresa platná, zobrazí se zpráva o úspěchu. v opačném případě se zobrazí předdefinovaná chybová zpráva s popisem.

[!code-cpp[NVC_MFC_CNetAddressCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cnetaddressctrl-class_1.cpp)]

## <a name="example"></a>Příklad

Následující příklad kódu ze souboru hlaviček dialogového okna definuje proměnné [NC_ADDRESS](/windows/win32/api/shellapi/ns-shellapi-nc_address) a [NET_ADDRESS_INFO](/windows/win32/shell/hkey-type) , které jsou vyžadovány metodou [CNetAddressCtrl –:: GetAddress](#getaddress) .

[!code-cpp[NVC_MFC_CNetAddressCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cnetaddressctrl-class_2.h)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CEdit](../../mfc/reference/cedit-class.md)

`CNetAddressCtrl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxcmn. h

Tato třída je podporována v systému Windows Vista a novějších.

Další požadavky pro tuto třídu jsou popsány v tématu [požadavky na sestavení pro běžné ovládací prvky systému Windows Vista](../../mfc/build-requirements-for-windows-vista-common-controls.md).

##  <a name="cnetaddressctrl"></a>  CNetAddressCtrl::CNetAddressCtrl

`CNetAddressCtrl` Vytvoří objekt.

```
CNetAddressCtrl();
```

### <a name="remarks"></a>Poznámky

K vytvoření síťového ovládacího prvku a `CNetAddressCtrl` jeho připojení k objektu použijte metodu [CNetAddressCtrl –:: Create](#create) nebo [CNetAddressCtrl –:: CreateEx](#createex) .

##  <a name="create"></a>  CNetAddressCtrl::Create

Vytvoří ovládací prvek síťové adresy se zadanými styly a připojí ho k aktuálnímu `CNetAddressCtrl` objektu.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*dwStyle*|pro Bitová kombinace stylů, která se má použít pro ovládací prvek Další informace najdete v tématu [Úprava stylů](../../mfc/reference/styles-used-by-mfc.md#edit-styles).|
|*OBD*|pro Odkaz na strukturu [Rect](/previous-versions/dd162897\(v=vs.85\)) , která obsahuje pozici a velikost ovládacího prvku.|
|*pParentWnd*|pro Ukazatel bez hodnoty null na objekt [CWnd](../../mfc/reference/cwnd-class.md) , který je nadřazeným oknem ovládacího prvku.|
|*nID*|pro ID ovládacího prvku|

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je tato metoda úspěšná; v opačném případě FALSE.

##  <a name="createex"></a>  CNetAddressCtrl::CreateEx

Vytvoří ovládací prvek síťové adresy se zadanými rozšířenými styly a připojí ho k aktuálnímu `CNetAddressCtrl` objektu.

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*dwExStyle*|pro Bitová kombinace (nebo) rozšířených stylů, které mají být použity pro ovládací prvek. Další informace najdete v parametru *dwExStyle* funkce [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) .|
|*dwStyle*|pro Bitových kombinací (nebo) stylů, které mají být použity pro ovládací prvek. Další informace najdete v tématu [Úprava stylů](../../mfc/reference/styles-used-by-mfc.md#edit-styles).|
|*OBD*|pro Odkaz na strukturu [Rect](/previous-versions/dd162897\(v=vs.85\)) , která obsahuje pozici a velikost ovládacího prvku.|
|*pParentWnd*|pro Ukazatel bez hodnoty null na objekt [CWnd](../../mfc/reference/cwnd-class.md) , který je nadřazeným oknem ovládacího prvku.|
|*nID*|pro ID ovládacího prvku|

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je tato metoda úspěšná; v opačném případě FALSE.

##  <a name="displayerrortip"></a>  CNetAddressCtrl::DisplayErrorTip

Zobrazí chybovou zprávu v tipu bubliny, která je přidružená k aktuálnímu ovládacímu prvku síťové adresy.

```
HRESULT DisplayErrorTip();
```

### <a name="return-value"></a>Návratová hodnota

Hodnota `S_OK` , pokud je tato metoda úspěšná. v opačném případě kód chyby.

### <a name="remarks"></a>Poznámky

Pomocí metody [CNetAddressCtrl –:: SetAllowType](#setallowtype) určete typy adres, které může podporovat aktuální ovládací prvek adresa sítě. Pomocí metody [CNetAddressCtrl –:: GetAddress](#getaddress) můžete ověřit a analyzovat síťovou adresu, kterou uživatel zadá. Použijte metodu [CNetAddressCtrl –::D isplayerrortip](#displayerrortip) pro zobrazení informační zprávy o chybě, pokud metoda [CNetAddressCtrl –:: GetAddress](#getaddress) není úspěšná.

Tato zpráva vyvolá makro [NetAddr_DisplayErrorTip](/windows/win32/api/shellapi/nf-shellapi-netaddr_displayerrortip) , které je popsáno v Windows SDK. Toto makro odešle `NCM_DISPLAYERRORTIP` zprávu.

##  <a name="getaddress"></a>  CNetAddressCtrl::GetAddress

Načte ověřenou a analyzovanou reprezentaci síťové adresy, která je přidružena k aktuálnímu ovládacímu prvku síťové adresy.

```
HRESULT GetAddress(PNC_ADDRESS pAddress) const;
```

### <a name="parameters"></a>Parametry

*pAddress*<br/>
[in, out] Ukazatel na strukturu [NC_ADDRESS](/windows/win32/api/shellapi/ns-shellapi-nc_address) .  Nastavte člena *pAddrInfo* této struktury na adresu struktury [NET_ADDRESS_INFO](/windows/win32/shell/hkey-type) před voláním metody GetAddress.

### <a name="return-value"></a>Návratová hodnota

Hodnota S_OK, pokud je tato metoda úspěšná; v opačném případě kód chyby modelu COM. Další informace o možných kódech chyb naleznete v části vrácená hodnota v makru [NetAddr_GetAddress](/windows/win32/api/shellapi/nf-shellapi-netaddr_getaddress) .

### <a name="remarks"></a>Poznámky

Pokud je tato metoda úspěšná, struktura [NET_ADDRESS_INFO](/windows/win32/shell/hkey-type) obsahuje další informace o síťové adrese.

Pomocí metody [CNetAddressCtrl –:: SetAllowType](#setallowtype) určete typy adres, které může podporovat aktuální ovládací prvek síťové adresy. Pomocí metody [CNetAddressCtrl –:: GetAddress](#getaddress) můžete ověřit a analyzovat síťovou adresu, kterou uživatel zadá. Použijte metodu [CNetAddressCtrl –::D isplayerrortip](#displayerrortip) pro zobrazení informační zprávy o chybě, pokud metoda [CNetAddressCtrl –:: GetAddress](#getaddress) není úspěšná.

Tato metoda vyvolá makro [NetAddr_GetAddress](/windows/win32/api/shellapi/nf-shellapi-netaddr_getaddress) , které je popsáno v Windows SDK. Toto makro odešle zprávu NCM_GETADDRESS.

##  <a name="getallowtype"></a>  CNetAddressCtrl::GetAllowType

Načte typ síťové adresy, kterou může aktuální ovládací prvek síťové adresy podporovat.

```
DWORD GetAllowType() const;
```

### <a name="return-value"></a>Návratová hodnota

Bitových kombinací (nebo) příznaků, které určují typy adres, které může podporovat ovládací prvek síťové adresy. Další informace najdete v tématu [NET_STRING](/windows/win32/shell/net-string).

### <a name="remarks"></a>Poznámky

Tato zpráva vyvolá makro [NetAddr_GetAllowType](/windows/win32/api/shellapi/nf-shellapi-netaddr_getallowtype) , které je popsáno v Windows SDK. Toto makro odešle zprávu NCM_GETALLOWTYPE.

##  <a name="setallowtype"></a>  CNetAddressCtrl::SetAllowType

Nastaví typ síťové adresy, který může podporovat aktuální ovládací prvek adresa sítě.

```
HRESULT SetAllowType(DWORD dwAddrMask);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*dwAddrMask*|pro Bitových kombinací (nebo) příznaků, které určují typy adres, které může podporovat ovládací prvek síťové adresy. Další informace najdete v tématu [NET_STRING](/windows/win32/shell/net-string).|

### <a name="return-value"></a>Návratová hodnota

S_OK, pokud je tato metoda úspěšná; v opačném případě kód chyby modelu COM.

### <a name="remarks"></a>Poznámky

Pomocí metody [CNetAddressCtrl –:: SetAllowType](#setallowtype) určete typy adres, které může podporovat aktuální ovládací prvek adresa sítě. Pomocí metody [CNetAddressCtrl –:: GetAddress](#getaddress) můžete ověřit a analyzovat síťovou adresu, kterou uživatel zadá. Použijte metodu [CNetAddressCtrl –::D isplayerrortip](#displayerrortip) pro zobrazení informační zprávy o chybě, pokud metoda [CNetAddressCtrl –:: GetAddress](#getaddress) není úspěšná.

Tato zpráva vyvolá makro [NetAddr_SetAllowType](/windows/win32/api/shellapi/nf-shellapi-netaddr_setallowtype) , které je popsáno v Windows SDK. Toto makro odešle zprávu NCM_SETALLOWTYPE.

## <a name="see-also"></a>Viz také:

[CNetAddressCtrl – třída](../../mfc/reference/cnetaddressctrl-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CEdit – třída](../../mfc/reference/cedit-class.md)
