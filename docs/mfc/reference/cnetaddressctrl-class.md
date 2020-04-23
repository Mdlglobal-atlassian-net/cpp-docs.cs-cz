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
ms.openlocfilehash: c6f391966ef6657363e8f23e5666a57a935b08e1
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752784"
---
# <a name="cnetaddressctrl-class"></a>CNetAddressCtrl – třída

Třída `CNetAddressCtrl` představuje ovládací prvek síťové adresy, který můžete použít k zadání a ověření formátu IPv4, IPv6 a pojmenovaných adres DNS.

## <a name="syntax"></a>Syntaxe

```
class CNetAddressCtrl : public CEdit
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CNetAddressCtrl::CNetAddressCtrl](#cnetaddressctrl)|Vytvoří `CNetAddressCtrl` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CNetAddressCtrl::Vytvořit](#create)|Vytvoří ovládací prvek síťové adresy se zadanými `CNetAddressCtrl` styly a připojí jej k aktuálnímu objektu.|
|[CNetAddressCtrl::CreateEx](#createex)|Vytvoří ovládací prvek síťové adresy se zadanými `CNetAddressCtrl` rozšířenými styly a připojí jej k aktuálnímu objektu.|
|[CNetAddressCtrl::D](#displayerrortip)|Zobrazí tip bubliny chyby, když uživatel zadá nepodporovanou síťovou adresu do aktuálního ovládacího prvku síťové adresy.|
|[CNetAddressCtrl::GetAddress](#getaddress)|Načte ověřenou a analyzosovovku síťové adresy přidružené k aktuálnímu ovládacímu prvku síťové adresy.|
|[CNetAddressCtrl::GetAllowType](#getallowtype)|Načte typ síťové adresy, který může podporovat aktuální ovládací prvek síťové adresy.|
|[CNetAddressCtrl::SetAllowType](#setallowtype)|Nastaví typ síťové adresy, kterou může podporovat aktuální ovládací prvek síťové adresy.|

## <a name="remarks"></a>Poznámky

Ovládací prvek síťové adresy ověří, zda je formát adresy, kterou uživatel zadá, správný. Ovládací prvek se ve skutečnosti nepřipojí k síťové adrese. Metoda [CNetAddressCtrl::SetAllowType](#setallowtype) určuje jeden nebo více typů adres, které může metoda [CNetAddressCtrl::GetAddress](#getaddress) analyzovat a ověřit. Adresa může mít podobu adresy IPv4, IPv6 nebo pojmenované adresy serveru, sítě, hostitele nebo cíle zprávy všesměrového vysílání. Pokud je formát adresy nesprávný, můžete použít metodu [CNetAddressCtrl::DisplayErrorTip](#displayerrortip) k zobrazení informačního okna se zprávou, které graficky odkazuje na textové pole ovládacího prvku síťové adresy a zobrazí předdefinovanou chybovou zprávu.

Třída `CNetAddressCtrl` je odvozena z třídy [CEdit.](../../mfc/reference/cedit-class.md) V důsledku toho poskytuje řízení síťových adres přístup ke všem zprávám ovládacího prvku pro úpravy systému Windows.

Následující obrázek znázorňuje dialogové okno, které obsahuje ovládací prvek síťové adresy. Textové pole (1) pro ovládací prvek síťové adresy obsahuje neplatnou síťovou adresu. Pokud je síťová adresa neplatná, zobrazí se informační zpráva (2).

![Dialog s ovládacím prvkem síťové adresy a informačním tipem.](../../mfc/reference/media/cnetaddctrl.png "Dialog s ovládacím prvkem síťové adresy a informačním tipem.")

## <a name="example"></a>Příklad

Následující příklad kódu je část dialogového okna, která ověřuje síťovou adresu. Obslužné rutiny událostí pro tři přepínací tlačítka určují, že síťová adresa může být jedním ze tří typů adres. Uživatel zadá adresu do textového pole síťového ovládacího prvku a stisknutím tlačítka adresu ověří. Pokud je adresa platná, zobrazí se zpráva o úspěchu. v opačném případě se zobrazí předdefinovaná chybová zpráva s informačním a informačním rozhraním.

[!code-cpp[NVC_MFC_CNetAddressCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cnetaddressctrl-class_1.cpp)]

## <a name="example"></a>Příklad

Následující příklad kódu ze souboru záhlaví dialogového okna definuje proměnné [NC_ADDRESS](/windows/win32/api/shellapi/ns-shellapi-nc_address) a [NET_ADDRESS_INFO,](/windows/win32/shell/hkey-type) které jsou vyžadovány metodou [CNetAddressCtrl::GetAddress.](#getaddress)

[!code-cpp[NVC_MFC_CNetAddressCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cnetaddressctrl-class_2.h)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[CEditovat](../../mfc/reference/cedit-class.md)

`CNetAddressCtrl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxcmn.h

Tato třída je podporována v systému Windows Vista a novějších.

Další požadavky pro tuto třídu jsou popsány v [části Požadavky na sestavení pro běžné ovládací prvky systému Windows Vista](../../mfc/build-requirements-for-windows-vista-common-controls.md).

## <a name="cnetaddressctrlcnetaddressctrl"></a><a name="cnetaddressctrl"></a>CNetAddressCtrl::CNetAddressCtrl

Vytvoří `CNetAddressCtrl` objekt.

```
CNetAddressCtrl();
```

### <a name="remarks"></a>Poznámky

Pomocí metody [CNetAddressCtrl::Create](#create) nebo [CNetAddressCtrl::CreateEx](#createex) vytvořte síťový ovládací `CNetAddressCtrl` prvek a připojte jej k objektu.

## <a name="cnetaddressctrlcreate"></a><a name="create"></a>CNetAddressCtrl::Vytvořit

Vytvoří ovládací prvek síťové adresy se zadanými `CNetAddressCtrl` styly a připojí jej k aktuálnímu objektu.

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
|*dwStyl*|[v] Bitová kombinace stylů, které mají být použity na ovládací prvek. Další informace naleznete v [tématu Úpravy stylů](../../mfc/reference/styles-used-by-mfc.md#edit-styles).|
|*Rect*|[v] Odkaz na [rect](/windows/win32/api/windef/ns-windef-rect) strukturu, která obsahuje umístění a velikost ovládacího prvku.|
|*pParentWnd*|[v] Nenulový ukazatel na [cwnd](../../mfc/reference/cwnd-class.md) objekt, který je nadřazené okno ovládacího prvku.|
|*Nid*|[v] ID ovládacího prvku.|

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je tato metoda úspěšná; jinak NEPRAVDA.

## <a name="cnetaddressctrlcreateex"></a><a name="createex"></a>CNetAddressCtrl::CreateEx

Vytvoří ovládací prvek síťové adresy se zadanými `CNetAddressCtrl` rozšířenými styly a připojí jej k aktuálnímu objektu.

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
|*dwExStyl*|[v] Bitová kombinace (OR) rozšířených stylů, které mají být použity na ovládací prvek. Další informace naleznete v parametru *dwExStyle* funkce [CreateWindowEx.](/windows/win32/api/winuser/nf-winuser-createwindowexw)|
|*dwStyl*|[v] Bitová kombinace (OR) stylů, které mají být použity na ovládací prvek. Další informace naleznete v [tématu Úpravy stylů](../../mfc/reference/styles-used-by-mfc.md#edit-styles).|
|*Rect*|[v] Odkaz na [rect](/windows/win32/api/windef/ns-windef-rect) strukturu, která obsahuje umístění a velikost ovládacího prvku.|
|*pParentWnd*|[v] Nenulový ukazatel na [cwnd](../../mfc/reference/cwnd-class.md) objekt, který je nadřazené okno ovládacího prvku.|
|*Nid*|[v] ID ovládacího prvku.|

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je tato metoda úspěšná; jinak NEPRAVDA.

## <a name="cnetaddressctrldisplayerrortip"></a><a name="displayerrortip"></a>CNetAddressCtrl::D

Zobrazí chybovou zprávu v tipu pozice, která je přidružena k aktuálnímu ovládacímu prvku síťové adresy.

```
HRESULT DisplayErrorTip();
```

### <a name="return-value"></a>Návratová hodnota

Hodnota, `S_OK` pokud je tato metoda úspěšná; v opačném případě kód chyby.

### <a name="remarks"></a>Poznámky

Pomocí metody [CNetAddressCtrl::SetAllowType](#setallowtype) určete typy adres, které může podporovat aktuální ovládací prvek síťové adresy. Pomocí metody [CNetAddressCtrl::GetAddress](#getaddress) ověřte a analyzujte síťovou adresu, kterou uživatel zadá. Pomocí metody [CNetAddressCtrl::DisplayErrorTip](#displayerrortip) zobrazte informační zprávu o chybové zprávě, pokud je metoda [CNetAddressCtrl::GetAddress](#getaddress) neúspěšná.

Tato zpráva vyvolá [NetAddr_DisplayErrorTip](/windows/win32/api/shellapi/nf-shellapi-netaddr_displayerrortip) makro, které je popsáno v sadě Windows SDK. To makro `NCM_DISPLAYERRORTIP` odešle zprávu.

## <a name="cnetaddressctrlgetaddress"></a><a name="getaddress"></a>CNetAddressCtrl::GetAddress

Načte ověřenou a analyzosovovku síťové adresy, která je přidružena k aktuálnímu ovládacímu prvku síťové adresy.

```
HRESULT GetAddress(PNC_ADDRESS pAddress) const;
```

### <a name="parameters"></a>Parametry

*pAdresa*<br/>
[dovnitř, ven] Ukazatel na [NC_ADDRESS](/windows/win32/api/shellapi/ns-shellapi-nc_address) strukturu.  Před voláním metody GetAddress nastavte člen *pAddrInfo* této struktury na adresu [NET_ADDRESS_INFO](/windows/win32/shell/hkey-type) struktury.

### <a name="return-value"></a>Návratová hodnota

Hodnota S_OK, pokud je tato metoda úspěšná; v opačném případě kód chyby com. Další informace o možných kódech chyb naleznete v části Vrácená hodnota [NetAddr_GetAddress](/windows/win32/api/shellapi/nf-shellapi-netaddr_getaddress) makra.

### <a name="remarks"></a>Poznámky

Pokud je tato metoda úspěšná, [NET_ADDRESS_INFO](/windows/win32/shell/hkey-type) struktura obsahuje další informace o síťové adrese.

Pomocí metody [CNetAddressCtrl::SetAllowType](#setallowtype) určete typy adres, které může podporovat aktuální ovládací prvek síťové adresy. Pomocí metody [CNetAddressCtrl::GetAddress](#getaddress) ověřte a analyzujte síťovou adresu, kterou uživatel zadá. Pomocí metody [CNetAddressCtrl::DisplayErrorTip](#displayerrortip) zobrazte informační zprávu o chybové zprávě, pokud je metoda [CNetAddressCtrl::GetAddress](#getaddress) neúspěšná.

Tato metoda vyvolá [NetAddr_GetAddress](/windows/win32/api/shellapi/nf-shellapi-netaddr_getaddress) makro, které je popsáno v sadě Windows SDK. Makro odešle zprávu NCM_GETADDRESS.

## <a name="cnetaddressctrlgetallowtype"></a><a name="getallowtype"></a>CNetAddressCtrl::GetAllowType

Načte typ síťové adresy, který může podporovat aktuální ovládací prvek síťové adresy.

```
DWORD GetAllowType() const;
```

### <a name="return-value"></a>Návratová hodnota

Bitová kombinace (OR) příznaků, která určuje typy adres, které může řídit síťovou adresou podporovat. Další informace naleznete [v tématu NET_STRING](/windows/win32/shell/net-string).

### <a name="remarks"></a>Poznámky

Tato zpráva vyvolá [makro NetAddr_GetAllowType,](/windows/win32/api/shellapi/nf-shellapi-netaddr_getallowtype) které je popsáno v sadě Windows SDK. Toto makro odešle zprávu NCM_GETALLOWTYPE.

## <a name="cnetaddressctrlsetallowtype"></a><a name="setallowtype"></a>CNetAddressCtrl::SetAllowType

Nastaví typ síťové adresy, kterou může podporovat aktuální ovládací prvek síťové adresy.

```
HRESULT SetAllowType(DWORD dwAddrMask);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*dwAddrMask*|[v] Bitová kombinace (OR) příznaků, která určuje typy adres, které může řídit síťovou adresou podporovat. Další informace naleznete [v tématu NET_STRING](/windows/win32/shell/net-string).|

### <a name="return-value"></a>Návratová hodnota

S_OK pokud je tato metoda úspěšná; v opačném případě kód chyby com.

### <a name="remarks"></a>Poznámky

Pomocí metody [CNetAddressCtrl::SetAllowType](#setallowtype) určete typy adres, které může podporovat aktuální ovládací prvek síťové adresy. Pomocí metody [CNetAddressCtrl::GetAddress](#getaddress) ověřte a analyzujte síťovou adresu, kterou uživatel zadá. Pomocí metody [CNetAddressCtrl::DisplayErrorTip](#displayerrortip) zobrazte informační zprávu o chybové zprávě, pokud je metoda [CNetAddressCtrl::GetAddress](#getaddress) neúspěšná.

Tato zpráva vyvolá [makro NetAddr_SetAllowType,](/windows/win32/api/shellapi/nf-shellapi-netaddr_setallowtype) které je popsáno v sadě Windows SDK. Makro odešle zprávu NCM_SETALLOWTYPE.

## <a name="see-also"></a>Viz také

[Třída CNetAddressCtrl](../../mfc/reference/cnetaddressctrl-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CEdit – třída](../../mfc/reference/cedit-class.md)
