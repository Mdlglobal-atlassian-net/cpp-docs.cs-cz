---
title: Rozhraní IAxWinAmbientDispatch
ms.date: 11/04/2016
f1_keywords:
- IAxWinAmbientDispatch
- ATLIFACE/ATL::IAxWinAmbientDispatch
- ATLIFACE/ATL::get_AllowContextMenu
- ATLIFACE/ATL::get_AllowShowUI
- ATLIFACE/ATL::get_AllowWindowlessActivation
- ATLIFACE/ATL::get_BackColor
- ATLIFACE/ATL::get_DisplayAsDefault
- ATLIFACE/ATL::get_DocHostDoubleClickFlags
- ATLIFACE/ATL::get_DocHostFlags
- ATLIFACE/ATL::get_Font
- ATLIFACE/ATL::get_ForeColor
- ATLIFACE/ATL::get_LocaleID
- ATLIFACE/ATL::get_MessageReflect
- ATLIFACE/ATL::get_OptionKeyPath
- ATLIFACE/ATL::get_ShowGrabHandles
- ATLIFACE/ATL::get_ShowHatching
- ATLIFACE/ATL::get_UserMode
- ATLIFACE/ATL::put_AllowContextMenu
- ATLIFACE/ATL::put_AllowShowUI
- ATLIFACE/ATL::put_AllowWindowlessActivation
- ATLIFACE/ATL::put_BackColor
- ATLIFACE/ATL::put_DisplayAsDefault
- ATLIFACE/ATL::put_DocHostDoubleClickFlags
- ATLIFACE/ATL::put_DocHostFlags
- ATLIFACE/ATL::put_Font
- ATLIFACE/ATL::put_ForeColor
- ATLIFACE/ATL::put_LocaleID
- ATLIFACE/ATL::put_MessageReflect
- ATLIFACE/ATL::put_OptionKeyPath
- ATLIFACE/ATL::put_UserMode
helpviewer_keywords:
- IAxWinAmbientDispatch interface
ms.assetid: 55ba6f7b-7a3c-4792-ae47-c8a84b683ca9
ms.openlocfilehash: 6a4f5322d957b1e978bd123db3b4796be6b300da
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330012"
---
# <a name="iaxwinambientdispatch-interface"></a>Rozhraní IAxWinAmbientDispatch

Toto rozhraní poskytuje metody pro určení charakteristiky hostovaného ovládacího prvku nebo kontejneru.

> [!IMPORTANT]
> Tuto třídu a její členy nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
interface IAxWinAmbientDispatch : IDispatch
```

## <a name="members"></a>Členové

### <a name="methods"></a>Metody

|||
|-|-|
|[get_AllowContextMenu](#get_allowcontextmenu)|Vlastnost `AllowContextMenu` určuje, zda je hostovanému ovládacímu prvku povoleno zobrazit vlastní kontextovou nabídku.|
|[get_AllowShowUI](#get_allowshowui)|Vlastnost `AllowShowUI` určuje, zda je hostovanému ovládacímu prvku povoleno zobrazit vlastní uživatelské rozhraní.|
|[get_AllowWindowlessActivation](#get_allowwindowlessactivation)|Vlastnost `AllowWindowlessActivation` určuje, zda kontejner povolí aktivaci bez oken.|
|[get_BackColor](#get_backcolor)|Vlastnost `BackColor` určuje barvu okolního pozadí kontejneru.|
|[get_DisplayAsDefault](#get_displayasdefault)|`DisplayAsDefault`je vlastnost okolí, která umožňuje ovládacímu prvku zjistit, zda se jedná o výchozí ovládací prvek.|
|[get_DocHostDoubleClickFlags](#get_dochostdoubleclickflags)|Vlastnost `DocHostDoubleClickFlags` určuje operaci, která by měla probíhat v reakci na poklepání.|
|[get_DocHostFlags](#get_dochostflags)|Vlastnost `DocHostFlags` určuje možnosti uživatelského rozhraní objektu hostitele.|
|[get_Font](#get_font)|Vlastnost `Font` určuje okolní písmo kontejneru.|
|[get_ForeColor](#get_forecolor)|Vlastnost `ForeColor` určuje barvu okolí popředí kontejneru.|
|[get_LocaleID](#get_localeid)|Vlastnost `LocaleID` určuje ID okolního národního prostředí kontejneru.|
|[get_MessageReflect](#get_messagereflect)|Ambient `MessageReflect` vlastnost určuje, zda kontejner bude odrážet zprávy hostovaného ovládacího prvku.|
|[get_OptionKeyPath](#get_optionkeypath)|Vlastnost `OptionKeyPath` určuje cestu klíče registru k uživatelským nastavením.|
|[get_ShowGrabHandles](#get_showgrabhandles)|Ambient `ShowGrabHandles` vlastnost umožňuje ovládacíprvek zjistit, zda by měl kreslit sám s úchyty.|
|[get_ShowHatching](#get_showhatching)|Ambient `ShowHatching` vlastnost umožňuje ovládacíprvek zjistit, zda by měl kreslit sám šrafované.|
|[get_UserMode](#get_usermode)|Vlastnost `UserMode` určuje okolní uživatelský režim kontejneru.|
|[put_AllowContextMenu](#put_allowcontextmenu)|Vlastnost `AllowContextMenu` určuje, zda je hostovanému ovládacímu prvku povoleno zobrazit vlastní kontextovou nabídku.|
|[put_AllowShowUI](#put_allowshowui)|Vlastnost `AllowShowUI` určuje, zda je hostovanému ovládacímu prvku povoleno zobrazit vlastní uživatelské rozhraní.|
|[put_AllowWindowlessActivation](#put_allowwindowlessactivation)|Vlastnost `AllowWindowlessActivation` určuje, zda kontejner povolí aktivaci bez oken.|
|[put_BackColor](#put_backcolor)|Vlastnost `BackColor` určuje barvu okolního pozadí kontejneru.|
|[put_DisplayAsDefault](#put_displayasdefault)|`DisplayAsDefault`je vlastnost okolí, která umožňuje ovládacímu prvku zjistit, zda se jedná o výchozí ovládací prvek.|
|[put_DocHostDoubleClickFlags](#put_dochostdoubleclickflags)|Vlastnost `DocHostDoubleClickFlags` určuje operaci, která by měla probíhat v reakci na poklepání.|
|[put_DocHostFlags](#put_dochostflags)|Vlastnost `DocHostFlags` určuje možnosti uživatelského rozhraní objektu hostitele.|
|[put_Font](#put_font)|Vlastnost `Font` určuje okolní písmo kontejneru.|
|[put_ForeColor](#put_forecolor)|Vlastnost `ForeColor` určuje barvu okolí popředí kontejneru.|
|[put_LocaleID](#put_localeid)|Vlastnost `LocaleID` určuje ID okolního národního prostředí kontejneru.|
|[put_MessageReflect](#put_messagereflect)|Ambient `MessageReflect` vlastnost určuje, zda kontejner bude odrážet zprávy hostovaného ovládacího prvku.|
|[put_OptionKeyPath](#put_optionkeypath)|Vlastnost `OptionKeyPath` určuje cestu klíče registru k uživatelským nastavením.|
|[put_UserMode](#put_usermode)|Vlastnost `UserMode` určuje okolní uživatelský režim kontejneru.|

## <a name="remarks"></a>Poznámky

Toto rozhraní je vystaveno ovládacím objektům ActiveX společnosti ATL. Volání metody v tomto rozhraní nastavit vlastnosti okolí, které jsou k dispozici hostované hospo- ovládacího prvku nebo určit další aspekty chování kontejneru. Chcete-li doplnit `IAxWinAmbientDispatch`vlastnosti poskytované uživatelem , použijte [IAxWinAmbientDispatchEx](../../atl/reference/iaxwinambientdispatchex-interface.md).

<xref:System.Windows.Forms.AxHost>se pokusí načíst `IAxWinAmbientDispatch` informace `IAxWinAmbientDispatchEx` o typu a z typelib, který obsahuje kód.

Pokud odkazujete na soubor ATL90.dll, **AXHost** načte informace o typu z typelib v dll.

Další podrobnosti najdete v [tématu Hostování ovládacích prvků ActiveX pomocí služby ATL AXHost.](../../atl/hosting-activex-controls-using-atl-axhost.md)

## <a name="requirements"></a>Požadavky

Definice tohoto rozhraní je k dispozici v několika formách, jak je znázorněno v následující tabulce.

|Typ definice|File|
|---------------------|----------|
|Idl|atliface.idl|
|Knihovna typů|Soubor ATL.dll|
|C++|atliface.h (také součástí ATLBase.h)|

## <a name="iaxwinambientdispatchget_allowcontextmenu"></a><a name="get_allowcontextmenu"></a>IAxWinAmbientDispatch::get_AllowContextMenu

Vlastnost `AllowContextMenu` určuje, zda je hostovanému ovládacímu prvku povoleno zobrazit vlastní kontextovou nabídku.

```
STDMETHOD(get_AllowContextMenu)(VARIANT_BOOL* pbAllowContextMenu);
```

### <a name="parameters"></a>Parametry

*PbAllowContextMenu*<br/>
[out] Adresa proměnné pro příjem aktuální hodnoty této vlastnosti.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Implementace objektu hostitele knihovny ATL používá VARIANT_TRUE jako výchozí hodnotu této vlastnosti.

## <a name="iaxwinambientdispatchget_allowshowui"></a><a name="get_allowshowui"></a>IAxWinAmbientDispatch::get_AllowShowUI

Vlastnost `AllowShowUI` určuje, zda je hostovanému ovládacímu prvku povoleno zobrazit vlastní uživatelské rozhraní.

```
STDMETHOD(get_AllowShowUI)(VARIANT_BOOL* pbAllowShowUI);
```

### <a name="parameters"></a>Parametry

*pbAllowShowUI*<br/>
[out] Adresa proměnné pro příjem aktuální hodnoty této vlastnosti.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Implementace objektu hostitele knihovny ATL používá VARIANT_FALSE jako výchozí hodnotu této vlastnosti.

## <a name="iaxwinambientdispatchget_allowwindowlessactivation"></a><a name="get_allowwindowlessactivation"></a>IAxWinAmbientDispatch::get_AllowWindowlessActivation

Vlastnost `AllowWindowlessActivation` určuje, zda kontejner povolí aktivaci bez oken.

```
STDMETHOD(get_AllowWindowlessActivation)(VARIANT_BOOL* pbAllowWindowless);
```

### <a name="parameters"></a>Parametry

*pbAllowWindowless*<br/>
[out] Adresa proměnné pro příjem aktuální hodnoty této vlastnosti.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Implementace objektu hostitele knihovny ATL používá VARIANT_TRUE jako výchozí hodnotu této vlastnosti.

## <a name="iaxwinambientdispatchget_backcolor"></a><a name="get_backcolor"></a>IAxWinAmbientDispatch::get_BackColor

Vlastnost `BackColor` určuje barvu okolního pozadí kontejneru.

```
STDMETHOD(get_BackColor)(OLE_COLOR* pclrBackground);
```

### <a name="parameters"></a>Parametry

*pclrPozadí*<br/>
[out] Adresa proměnné pro příjem aktuální hodnoty této vlastnosti.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Implementace objektu hostitele knihovny ATL používá jako výchozí hodnotu této vlastnosti COLOR_BTNFACE nebo COLOR_WINDOW (v závislosti na tom, zda je nadřazená hodnota okna hostitele dialogem či nikoli).

## <a name="iaxwinambientdispatchget_displayasdefault"></a><a name="get_displayasdefault"></a>IAxWinAmbientDispatch::get_DisplayAsDefault

`DisplayAsDefault`je vlastnost okolí, která umožňuje ovládacímu prvku zjistit, zda se jedná o výchozí ovládací prvek.

```
STDMETHOD(get_DisplayAsDefault)(VARIANT_BOOL* pbDisplayAsDefault);
```

### <a name="parameters"></a>Parametry

*pbDisplayAsVýchozí*<br/>
[out] Adresa proměnné pro příjem aktuální hodnoty této vlastnosti.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Implementace objektu hostitele knihovny ATL používá VARIANT_FALSE jako výchozí hodnotu této vlastnosti.

## <a name="iaxwinambientdispatchget_dochostdoubleclickflags"></a><a name="get_dochostdoubleclickflags"></a>IAxWinAmbientDispatch::get_DocHostDoubleClickFlags

Vlastnost `DocHostDoubleClickFlags` určuje operaci, která by měla probíhat v reakci na poklepání.

```
STDMETHOD(get_DocHostDoubleClickFlags)(DWORD* pdwDocHostDoubleClickFlags);
```

### <a name="parameters"></a>Parametry

*pdwDocHostDoubleClickFlags*<br/>
[out] Adresa proměnné pro příjem aktuální hodnoty této vlastnosti.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Implementace objektu hostitele knihovny ATL používá DOCHOSTUIDBLCLK_DEFAULT jako výchozí hodnotu této vlastnosti.

## <a name="iaxwinambientdispatchget_dochostflags"></a><a name="get_dochostflags"></a>IAxWinAmbientDispatch::get_DocHostFlags

Vlastnost `DocHostFlags` určuje možnosti uživatelského rozhraní objektu hostitele.

```
STDMETHOD(get_DocHostFlags)(DWORD* pdwDocHostFlags);
```

### <a name="parameters"></a>Parametry

*pdwDocHostPříznaky*<br/>
[out] Adresa proměnné pro příjem aktuální hodnoty této vlastnosti.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Implementace objektu hostitele knihovny ATL používá DOCHOSTUIFLAG_NO3DBORDER jako výchozí hodnotu této vlastnosti.

## <a name="iaxwinambientdispatchget_font"></a><a name="get_font"></a>IAxWinAmbientDispatch::get_Font

Vlastnost `Font` určuje okolní písmo kontejneru.

```
STDMETHOD(get_Font)(IFontDisp** pFont);
```

### <a name="parameters"></a>Parametry

*písmo*<br/>
[out] Adresa ukazatele `IFontDisp` rozhraní slouží k příjmu aktuální hodnotu této vlastnosti.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Implementace objektu hostitele knihovny ATL používá jako výchozí hodnotu této vlastnosti výchozí písmo GUI nebo systémové písmo.

## <a name="iaxwinambientdispatchget_forecolor"></a><a name="get_forecolor"></a>IAxWinAmbientDispatch::get_ForeColor

Vlastnost `ForeColor` určuje barvu okolí popředí kontejneru.

```
STDMETHOD(get_ForeColor)(OLE_COLOR* pclrForeground);
```

### <a name="parameters"></a>Parametry

*pclrForeground*<br/>
[out] Adresa proměnné pro příjem aktuální hodnoty této vlastnosti.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Implementace objektu hostitele knihovny ATL používá jako výchozí hodnotu této vlastnosti barvu textu systémového okna.

## <a name="iaxwinambientdispatchget_localeid"></a><a name="get_localeid"></a>IAxWinAmbientDispatch::get_LocaleID

Vlastnost `LocaleID` určuje ID okolního národního prostředí kontejneru.

```
STDMETHOD(get_LocaleID)(LCID* plcidLocaleID);
```

### <a name="parameters"></a>Parametry

*plcidLocaleID*<br/>
[out] Adresa proměnné pro příjem aktuální hodnoty této vlastnosti.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Implementace objektu hostitele knihovny ATL používá jako výchozí hodnotu této vlastnosti výchozí národní prostředí uživatele.

Pomocí této metody můžete zjistit ambient LocalID, to znamená LocaleID programu, ve které je váš ovládací prvek používán. Jakmile znáte LocaleID, můžete volat kód pro načtení titulků specifických pro národní prostředí, text chybové zprávy a tak dále ze souboru prostředků nebo satelitní dll.

## <a name="iaxwinambientdispatchget_messagereflect"></a><a name="get_messagereflect"></a>IAxWinAmbientDispatch::get_MessageReflect

Ambient `MessageReflect` vlastnost určuje, zda kontejner bude odrážet zprávy hostovaného ovládacího prvku.

```
STDMETHOD(get_MessageReflect)(VARIANT_BOOL* pbMessageReflect);
```

### <a name="parameters"></a>Parametry

*pbMessageReflect*<br/>
[out] Adresa proměnné pro příjem aktuální hodnoty této vlastnosti.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Implementace objektu hostitele knihovny ATL používá VARIANT_TRUE jako výchozí hodnotu této vlastnosti.

## <a name="iaxwinambientdispatchget_optionkeypath"></a><a name="get_optionkeypath"></a>IAxWinAmbientDispatch::get_OptionKeyPath

Vlastnost `OptionKeyPath` určuje cestu klíče registru k uživatelským nastavením.

```
STDMETHOD(get_OptionKeyPath)(BSTR* pbstrOptionKeyPath);
```

### <a name="parameters"></a>Parametry

*cesta pbstrOptionKeyPath*<br/>
[out] Adresa proměnné pro příjem aktuální hodnoty této vlastnosti.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

## <a name="iaxwinambientdispatchget_showgrabhandles"></a><a name="get_showgrabhandles"></a>IAxWinAmbientDispatch::get_ShowGrabHandles

Ambient `ShowGrabHandles` vlastnost umožňuje ovládacíprvek zjistit, zda by měl kreslit sám s úchyty.

```
STDMETHOD(get_ShowGrabHandles)(VARIANT_BOOL* pbShowGrabHandles);
```

### <a name="parameters"></a>Parametry

*pbShowGrabHandles*<br/>
[out] Adresa proměnné pro příjem aktuální hodnoty této vlastnosti.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Implementace objektu hostitele knihovny ATL vždy vrátí VARIANT_FALSE jako hodnotu této vlastnosti.

## <a name="iaxwinambientdispatchget_showhatching"></a><a name="get_showhatching"></a>IAxWinAmbientDispatch::get_ShowHatching

Ambient `ShowHatching` vlastnost umožňuje ovládacíprvek zjistit, zda by měl kreslit sám šrafované.

```
STDMETHOD(get_ShowHatching)(VARIANT_BOOL* pbShowHatching);
```

### <a name="parameters"></a>Parametry

*pbShowVyšlování*<br/>
[out] Adresa proměnné pro příjem aktuální hodnoty této vlastnosti.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Implementace objektu hostitele knihovny ATL vždy vrátí VARIANT_FALSE jako hodnotu této vlastnosti.

## <a name="iaxwinambientdispatchget_usermode"></a><a name="get_usermode"></a>IAxWinAmbientDispatch::get_UserMode

Vlastnost `UserMode` určuje okolní uživatelský režim kontejneru.

```
STDMETHOD(get_UserMode)(VARIANT_BOOL* pbUserMode);
```

### <a name="parameters"></a>Parametry

*režim pbUserMode*<br/>
[out] Adresa proměnné pro příjem aktuální hodnoty této vlastnosti.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Implementace objektu hostitele knihovny ATL používá VARIANT_TRUE jako výchozí hodnotu této vlastnosti.

## <a name="iaxwinambientdispatchput_allowcontextmenu"></a><a name="put_allowcontextmenu"></a>IAxWinAmbientDispatch::put_AllowContextMenu

Vlastnost `AllowContextMenu` určuje, zda je hostovanému ovládacímu prvku povoleno zobrazit vlastní kontextovou nabídku.

```
STDMETHOD(put_AllowContextMenu)(VARIANT_BOOL bAllowContextMenu);
```

### <a name="parameters"></a>Parametry

*bAllowContextMenu*<br/>
[v] Nová hodnota této vlastnosti.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Implementace objektu hostitele knihovny ATL používá VARIANT_TRUE jako výchozí hodnotu této vlastnosti.

## <a name="iaxwinambientdispatchput_allowshowui"></a><a name="put_allowshowui"></a>IAxWinAmbientDispatch::put_AllowShowUI

Vlastnost `AllowShowUI` určuje, zda je hostovanému ovládacímu prvku povoleno zobrazit vlastní uživatelské rozhraní.

```
STDMETHOD(put_AllowShowUI)(VARIANT_BOOL bAllowShowUI);
```

### <a name="parameters"></a>Parametry

*bAllowShowUI*<br/>
[v] Nová hodnota této vlastnosti.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Implementace objektu hostitele knihovny ATL používá VARIANT_FALSE jako výchozí hodnotu této vlastnosti.

## <a name="iaxwinambientdispatchput_allowwindowlessactivation"></a><a name="put_allowwindowlessactivation"></a>IAxWinAmbientDispatch::put_AllowAktivace bezoken

Vlastnost `AllowWindowlessActivation` určuje, zda kontejner povolí aktivaci bez oken.

```
STDMETHOD(put_AllowWindowlessActivation)(VARIANT_BOOL bAllowWindowless);
```

### <a name="parameters"></a>Parametry

*bAllowWindowless*<br/>
[v] Nová hodnota této vlastnosti.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Implementace objektu hostitele knihovny ATL používá VARIANT_TRUE jako výchozí hodnotu této vlastnosti.

## <a name="iaxwinambientdispatchput_backcolor"></a><a name="put_backcolor"></a>IAxWinAmbientDispatch::put_BackColor

Vlastnost `BackColor` určuje barvu okolního pozadí kontejneru.

```
STDMETHOD(put_BackColor)(OLE_COLOR clrBackground);
```

### <a name="parameters"></a>Parametry

*clrPozadí*<br/>
[v] Nová hodnota této vlastnosti.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Implementace objektu hostitele knihovny ATL používá jako výchozí hodnotu této vlastnosti COLOR_BTNFACE nebo COLOR_WINDOW (v závislosti na tom, zda je nadřazená hodnota okna hostitele dialogem či nikoli).

## <a name="iaxwinambientdispatchput_displayasdefault"></a><a name="put_displayasdefault"></a>IAxWinAmbientDispatch::put_DisplayAsVýchozí

`DisplayAsDefault`je vlastnost okolí, která umožňuje ovládacímu prvku zjistit, zda se jedná o výchozí ovládací prvek.

```
STDMETHOD(put_DisplayAsDefault)(VARIANT_BOOL bDisplayAsDefault);
```

### <a name="parameters"></a>Parametry

*bDisplayAsVýchozí*<br/>
[v] Nová hodnota této vlastnosti.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Implementace objektu hostitele knihovny ATL používá VARIANT_FALSE jako výchozí hodnotu této vlastnosti.

## <a name="iaxwinambientdispatchput_dochostdoubleclickflags"></a><a name="put_dochostdoubleclickflags"></a>IAxWinAmbientDispatch::put_DocHostDoubleClickFlags

Vlastnost `DocHostDoubleClickFlags` určuje operaci, která by měla probíhat v reakci na poklepání.

```
STDMETHOD(put_DocHostDoubleClickFlags)(DWORD dwDocHostDoubleClickFlags);
```

### <a name="parameters"></a>Parametry

*dwDocHostDoubleClickFlags*<br/>
[v] Nová hodnota této vlastnosti.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Implementace objektu hostitele knihovny ATL používá DOCHOSTUIDBLCLK_DEFAULT jako výchozí hodnotu této vlastnosti.

## <a name="iaxwinambientdispatchput_dochostflags"></a><a name="put_dochostflags"></a>IAxWinAmbientDispatch::put_DocHostFlags

Vlastnost `DocHostFlags` určuje možnosti uživatelského rozhraní objektu hostitele.

```
STDMETHOD(put_DocHostFlags)(DWORD dwDocHostFlags);
```

### <a name="parameters"></a>Parametry

*dwDocHostPříznaky*<br/>
[v] Nová hodnota této vlastnosti.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Implementace objektu hostitele knihovny ATL používá DOCHOSTUIFLAG_NO3DBORDER jako výchozí hodnotu této vlastnosti.

## <a name="iaxwinambientdispatchput_font"></a><a name="put_font"></a>IAxWinAmbientDispatch::put_Font

Vlastnost `Font` určuje okolní písmo kontejneru.

```
STDMETHOD(put_Font)(IFontDisp* pFont);
```

### <a name="parameters"></a>Parametry

*písmo*<br/>
[v] Nová hodnota této vlastnosti.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Implementace objektu hostitele knihovny ATL používá jako výchozí hodnotu této vlastnosti výchozí písmo GUI nebo systémové písmo.

## <a name="iaxwinambientdispatchput_forecolor"></a><a name="put_forecolor"></a>IAxWinAmbientDispatch::put_ForeColor

Vlastnost `ForeColor` určuje barvu okolí popředí kontejneru.

```
STDMETHOD(put_ForeColor)(OLE_COLOR clrForeground);
```

### <a name="parameters"></a>Parametry

*clrForeground*<br/>
[v] Nová hodnota této vlastnosti.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Implementace objektu hostitele knihovny ATL používá jako výchozí hodnotu této vlastnosti barvu textu systémového okna.

## <a name="iaxwinambientdispatchput_localeid"></a><a name="put_localeid"></a>IAxWinAmbientDispatch::put_LocaleID

Vlastnost `LocaleID` určuje ID okolního národního prostředí kontejneru.

```
STDMETHOD(put_LocaleID)(LCID lcidLocaleID);
```

### <a name="parameters"></a>Parametry

*id lokál*<br/>
[v] Nová hodnota této vlastnosti.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Implementace objektu hostitele knihovny ATL používá jako výchozí hodnotu této vlastnosti výchozí národní prostředí uživatele.

## <a name="iaxwinambientdispatchput_messagereflect"></a><a name="put_messagereflect"></a>IAxWinAmbientDispatch::put_MessageReflect

Ambient `MessageReflect` vlastnost určuje, zda kontejner bude odrážet zprávy hostovaného ovládacího prvku.

```
STDMETHOD(put_MessageReflect)(VARIANT_BOOL bMessageReflect);
```

### <a name="parameters"></a>Parametry

*bMessageReflect*<br/>
[v] Nová hodnota této vlastnosti.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Implementace objektu hostitele knihovny ATL používá VARIANT_TRUE jako výchozí hodnotu této vlastnosti.

## <a name="iaxwinambientdispatchput_optionkeypath"></a><a name="put_optionkeypath"></a>IAxWinAmbientDispatch::put_OptionKeyPath

Vlastnost `OptionKeyPath` určuje cestu klíče registru k uživatelským nastavením.

```
STDMETHOD(put_OptionKeyPath)(BSTR bstrOptionKeyPath);
```

### <a name="parameters"></a>Parametry

*bstrOptionKeyPath*<br/>
[v] Nová hodnota této vlastnosti.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

## <a name="iaxwinambientdispatchput_usermode"></a><a name="put_usermode"></a>IAxWinAmbientDispatch::put_UserMode

Vlastnost `UserMode` určuje okolní uživatelský režim kontejneru.

```
STDMETHOD(put_UserMode)(VARIANT_BOOL bUserMode);
```

### <a name="parameters"></a>Parametry

*bRežim uživatele*<br/>
[v] Nová hodnota této vlastnosti.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Implementace objektu hostitele knihovny ATL používá VARIANT_TRUE jako výchozí hodnotu této vlastnosti.

## <a name="see-also"></a>Viz také

[Rozhraní IAxWinAmbientDispatchEx](../../atl/reference/iaxwinambientdispatchex-interface.md)<br/>
[Rozhraní IAxWinHostWindow](../../atl/reference/iaxwinhostwindow-interface.md)<br/>
[CAxWindow::QueryHost](../../atl/reference/caxwindow-class.md#queryhost)<br/>
[AtlAxGetHost](composite-control-global-functions.md#atlaxgethost)
