---
title: Iaxwinambientdispatch – rozhraní
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
ms.openlocfilehash: f143b2c58159d1bb0812152c68d3c31153d4570d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50467428"
---
# <a name="iaxwinambientdispatch-interface"></a>Iaxwinambientdispatch – rozhraní

Toto rozhraní poskytuje metody pro zadání vlastnosti hostovaného ovládacího prvku nebo kontejneru.

> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
interface IAxWinAmbientDispatch : IDispatch
```

## <a name="members"></a>Členové

### <a name="methods"></a>Metody

|||
|-|-|
|[get_AllowContextMenu](#get_allowcontextmenu)|`AllowContextMenu` Vlastnost určuje, jestli hostované ovládací prvek se může zobrazit kontextovou nabídku.|
|[get_AllowShowUI](#get_allowshowui)|`AllowShowUI` Vlastnost určuje, jestli hostované ovládací prvek se může zobrazit vlastní uživatelské rozhraní.|
|[get_AllowWindowlessActivation](#get_allowwindowlessactivation)|`AllowWindowlessActivation` Vlastnost určuje, zda kontejner bude umožňovat aktivace bez oken.|
|[get_BackColor](#get_backcolor)|`BackColor` Vlastnost určuje barvu pozadí okolí kontejneru.|
|[get_DisplayAsDefault](#get_displayasdefault)|`DisplayAsDefault` se změní vlastnost ambient umožňující ovládacího prvku a zjistěte, pokud je výchozí ovládací prvek.|
|[get_DocHostDoubleClickFlags](#get_dochostdoubleclickflags)|`DocHostDoubleClickFlags` Vlastnost určuje operaci, která má být provedena v reakci na poklepání.|
|[get_DocHostFlags](#get_dochostflags)|`DocHostFlags` Vlastnost určuje možnosti uživatelského rozhraní objektu hostitele.|
|[get_Font](#get_font)|`Font` Vlastnost určuje okolí písmo kontejneru.|
|[get_ForeColor](#get_forecolor)|`ForeColor` Vlastnost určuje barvu popředí okolí kontejneru.|
|[get_LocaleID](#get_localeid)|`LocaleID` Vlastnost určuje ID národního prostředí okolí kontejneru.|
|[get_MessageReflect](#get_messagereflect)|`MessageReflect` Vedlejší vlastnost určuje, zda kontejner bude odrážet zprávy do hostovaného ovládacího prvku.|
|[get_OptionKeyPath](#get_optionkeypath)|`OptionKeyPath` Vlastnost určuje cestu ke klíči registru nastavení pro uživatele.|
|[get_ShowGrabHandles](#get_showgrabhandles)|`ShowGrabHandles` Vedlejší vlastnost umožňuje řídit a zjistěte, pokud ji by měl vykreslit s úchyty.|
|[get_ShowHatching](#get_showhatching)|`ShowHatching` Vedlejší vlastnost umožňuje zjistit, pokud ji by měl vykreslit zasílána ovládacího prvku.|
|[get_UserMode](#get_usermode)|`UserMode` Vlastnost určuje režim okolí uživatele kontejneru.|
|[put_AllowContextMenu](#put_allowcontextmenu)|`AllowContextMenu` Vlastnost určuje, jestli hostované ovládací prvek se může zobrazit kontextovou nabídku.|
|[put_AllowShowUI](#put_allowshowui)|`AllowShowUI` Vlastnost určuje, jestli hostované ovládací prvek se může zobrazit vlastní uživatelské rozhraní.|
|[put_AllowWindowlessActivation](#put_allowwindowlessactivation)|`AllowWindowlessActivation` Vlastnost určuje, zda kontejner bude umožňovat aktivace bez oken.|
|[put_BackColor](#put_backcolor)|`BackColor` Vlastnost určuje barvu pozadí okolí kontejneru.|
|[put_DisplayAsDefault](#put_displayasdefault)|`DisplayAsDefault` se změní vlastnost ambient umožňující ovládacího prvku a zjistěte, pokud je výchozí ovládací prvek.|
|[put_DocHostDoubleClickFlags](#put_dochostdoubleclickflags)|`DocHostDoubleClickFlags` Vlastnost určuje operaci, která má být provedena v reakci na poklepání.|
|[put_DocHostFlags](#put_dochostflags)|`DocHostFlags` Vlastnost určuje možnosti uživatelského rozhraní objektu hostitele.|
|[put_Font](#put_font)|`Font` Vlastnost určuje okolí písmo kontejneru.|
|[put_ForeColor](#put_forecolor)|`ForeColor` Vlastnost určuje barvu popředí okolí kontejneru.|
|[put_LocaleID](#put_localeid)|`LocaleID` Vlastnost určuje ID národního prostředí okolí kontejneru.|
|[put_MessageReflect](#put_messagereflect)|`MessageReflect` Vedlejší vlastnost určuje, zda kontejner bude odrážet zprávy do hostovaného ovládacího prvku.|
|[put_OptionKeyPath](#put_optionkeypath)|`OptionKeyPath` Vlastnost určuje cestu ke klíči registru nastavení pro uživatele.|
|[put_UserMode](#put_usermode)|`UserMode` Vlastnost určuje režim okolí uživatele kontejneru.|

## <a name="remarks"></a>Poznámky

Toto rozhraní je zveřejněný prostřednictvím ovládací prvek ActiveX knihovny ATL pro hostování objektů. Volání metody na tomto rozhraní pro nastavení k dispozici vedlejším vlastnostem hostovaného ovládacího prvku nebo další aspekty chování kontejneru. K doplnění vlastnosti poskytované třídou `IAxWinAmbientDispatch`, použijte [iaxwinambientdispatchex –](../../atl/reference/iaxwinambientdispatchex-interface.md).

[AXHost](https://msdn.microsoft.com/library/system.windows.forms.axhost.aspx) se pokusí načíst informace o typu o `IAxWinAmbientDispatch` a `IAxWinAmbientDispatchEx` z knihovny typů, která obsahuje kód.

Pokud se připojujete k ATL90.dll, **AXHost** načte informace o typu z knihovny typů v knihovně DLL.

Zobrazit [hostování ActiveX ovládacích prvků pomocí knihovny ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) další podrobnosti.

## <a name="requirements"></a>Požadavky

Definice toto rozhraní není k dispozici v různých formách, jak je znázorněno v následující tabulce.

|Typ definice|Soubor|
|---------------------|----------|
|IDL|atliface.IDL|
|Knihovny typů|ATL.|
|C++|atliface.h (také součástí ATLBase.h)|

##  <a name="get_allowcontextmenu"></a>  IAxWinAmbientDispatch::get_AllowContextMenu

`AllowContextMenu` Vlastnost určuje, jestli hostované ovládací prvek se může zobrazit kontextovou nabídku.

```
STDMETHOD(get_AllowContextMenu)(VARIANT_BOOL* pbAllowContextMenu);
```

### <a name="parameters"></a>Parametry

*pbAllowContextMenu*<br/>
[out] Adresa proměnné k získání aktuální hodnota této vlastnosti.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnoty HRESULT.

### <a name="remarks"></a>Poznámky

Implementace objektu ATL hostitele používá VARIANT_TRUE jako výchozí hodnota této vlastnosti.

##  <a name="get_allowshowui"></a>  IAxWinAmbientDispatch::get_AllowShowUI

`AllowShowUI` Vlastnost určuje, jestli hostované ovládací prvek se může zobrazit vlastní uživatelské rozhraní.

```
STDMETHOD(get_AllowShowUI)(VARIANT_BOOL* pbAllowShowUI);
```

### <a name="parameters"></a>Parametry

*pbAllowShowUI*<br/>
[out] Adresa proměnné k získání aktuální hodnota této vlastnosti.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnoty HRESULT.

### <a name="remarks"></a>Poznámky

Implementace objektu ATL hostitele používá VARIANT_FALSE jako výchozí hodnota této vlastnosti.

##  <a name="get_allowwindowlessactivation"></a>  IAxWinAmbientDispatch::get_AllowWindowlessActivation

`AllowWindowlessActivation` Vlastnost určuje, zda kontejner bude umožňovat aktivace bez oken.

```
STDMETHOD(get_AllowWindowlessActivation)(VARIANT_BOOL* pbAllowWindowless);
```

### <a name="parameters"></a>Parametry

*pbAllowWindowless*<br/>
[out] Adresa proměnné k získání aktuální hodnota této vlastnosti.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnoty HRESULT.

### <a name="remarks"></a>Poznámky

Implementace objektu ATL hostitele používá VARIANT_TRUE jako výchozí hodnota této vlastnosti.

##  <a name="get_backcolor"></a>  IAxWinAmbientDispatch::get_BackColor

`BackColor` Vlastnost určuje barvu pozadí okolí kontejneru.

```
STDMETHOD(get_BackColor)(OLE_COLOR* pclrBackground);
```

### <a name="parameters"></a>Parametry

*pclrBackground*<br/>
[out] Adresa proměnné k získání aktuální hodnota této vlastnosti.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnoty HRESULT.

### <a name="remarks"></a>Poznámky

Implementace objektu ATL hostitele používá COLOR_BTNFACE nebo COLOR_WINDOW jako výchozí hodnota této vlastnosti (v závislosti na tom, zda nadřazené okno hostitele je dialogové okno, nebo ne).

##  <a name="get_displayasdefault"></a>  IAxWinAmbientDispatch::get_DisplayAsDefault

`DisplayAsDefault` se změní vlastnost ambient umožňující ovládacího prvku a zjistěte, pokud je výchozí ovládací prvek.

```
STDMETHOD(get_DisplayAsDefault)(VARIANT_BOOL* pbDisplayAsDefault);
```

### <a name="parameters"></a>Parametry

*pbDisplayAsDefault*<br/>
[out] Adresa proměnné k získání aktuální hodnota této vlastnosti.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnoty HRESULT.

### <a name="remarks"></a>Poznámky

Implementace objektu ATL hostitele používá VARIANT_FALSE jako výchozí hodnota této vlastnosti.

##  <a name="get_dochostdoubleclickflags"></a>  IAxWinAmbientDispatch::get_DocHostDoubleClickFlags

`DocHostDoubleClickFlags` Vlastnost určuje operaci, která má být provedena v reakci na poklepání.

```
STDMETHOD(get_DocHostDoubleClickFlags)(DWORD* pdwDocHostDoubleClickFlags);
```

### <a name="parameters"></a>Parametry

*pdwDocHostDoubleClickFlags*<br/>
[out] Adresa proměnné k získání aktuální hodnota této vlastnosti.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnoty HRESULT.

### <a name="remarks"></a>Poznámky

Implementace objektu ATL hostitele DOCHOSTUIDBLCLK_DEFAULT používá jako výchozí hodnota této vlastnosti.

##  <a name="get_dochostflags"></a>  IAxWinAmbientDispatch::get_DocHostFlags

`DocHostFlags` Vlastnost určuje možnosti uživatelského rozhraní objektu hostitele.

```
STDMETHOD(get_DocHostFlags)(DWORD* pdwDocHostFlags);
```

### <a name="parameters"></a>Parametry

*pdwDocHostFlags*<br/>
[out] Adresa proměnné k získání aktuální hodnota této vlastnosti.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnoty HRESULT.

### <a name="remarks"></a>Poznámky

Implementace objektu ATL hostitele DOCHOSTUIFLAG_NO3DBORDER používá jako výchozí hodnota této vlastnosti.

##  <a name="get_font"></a>  IAxWinAmbientDispatch::get_Font

`Font` Vlastnost určuje okolí písmo kontejneru.

```
STDMETHOD(get_Font)(IFontDisp** pFont);
```

### <a name="parameters"></a>Parametry

*pFont*<br/>
[out] Adresa `IFontDisp` ukazatel rozhraní, které slouží k přijímání aktuální hodnota této vlastnosti.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnoty HRESULT.

### <a name="remarks"></a>Poznámky

Implementace objektu ATL hostitele používá výchozí písmo grafického uživatelského rozhraní nebo systémové písmo jako výchozí hodnota této vlastnosti.

##  <a name="get_forecolor"></a>  IAxWinAmbientDispatch::get_ForeColor

`ForeColor` Vlastnost určuje barvu popředí okolí kontejneru.

```
STDMETHOD(get_ForeColor)(OLE_COLOR* pclrForeground);
```

### <a name="parameters"></a>Parametry

*pclrForeground*<br/>
[out] Adresa proměnné k získání aktuální hodnota této vlastnosti.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnoty HRESULT.

### <a name="remarks"></a>Poznámky

Implementace objektu ATL hostitele barvu textu okna systému používá jako výchozí hodnota této vlastnosti.

##  <a name="get_localeid"></a>  IAxWinAmbientDispatch::get_LocaleID

`LocaleID` Vlastnost určuje ID národního prostředí okolí kontejneru.

```
STDMETHOD(get_LocaleID)(LCID* plcidLocaleID);
```

### <a name="parameters"></a>Parametry

*plcidLocaleID*<br/>
[out] Adresa proměnné k získání aktuální hodnota této vlastnosti.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnoty HRESULT.

### <a name="remarks"></a>Poznámky

Implementace objektu ATL hostitele používá výchozí národní prostředí uživatele jako výchozí hodnota této vlastnosti.

Pomocí této metody může zjišťovat okolní LocalID, to znamená, že identifikátor národního prostředí programu ovládacího prvku se používá v. Jakmile budete znát identifikátor národního prostředí, můžete volat kód k načtení specifických pro národní prostředí popisky, text chybové zprávy, a tak dále ze souboru prostředků nebo satelitní knihovny DLL.

##  <a name="get_messagereflect"></a>  IAxWinAmbientDispatch::get_MessageReflect

`MessageReflect` Vedlejší vlastnost určuje, zda kontejner bude odrážet zprávy do hostovaného ovládacího prvku.

```
STDMETHOD(get_MessageReflect)(VARIANT_BOOL* pbMessageReflect);
```

### <a name="parameters"></a>Parametry

*pbMessageReflect*<br/>
[out] Adresa proměnné k získání aktuální hodnota této vlastnosti.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnoty HRESULT.

### <a name="remarks"></a>Poznámky

Implementace objektu ATL hostitele používá VARIANT_TRUE jako výchozí hodnota této vlastnosti.

##  <a name="get_optionkeypath"></a>  IAxWinAmbientDispatch::get_OptionKeyPath

`OptionKeyPath` Vlastnost určuje cestu ke klíči registru nastavení pro uživatele.

```
STDMETHOD(get_OptionKeyPath)(BSTR* pbstrOptionKeyPath);
```

### <a name="parameters"></a>Parametry

*pbstrOptionKeyPath*<br/>
[out] Adresa proměnné k získání aktuální hodnota této vlastnosti.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnoty HRESULT.

##  <a name="get_showgrabhandles"></a>  IAxWinAmbientDispatch::get_ShowGrabHandles

`ShowGrabHandles` Vedlejší vlastnost umožňuje řídit a zjistěte, pokud ji by měl vykreslit s úchyty.

```
STDMETHOD(get_ShowGrabHandles)(VARIANT_BOOL* pbShowGrabHandles);
```

### <a name="parameters"></a>Parametry

*pbShowGrabHandles*<br/>
[out] Adresa proměnné k získání aktuální hodnota této vlastnosti.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnoty HRESULT.

### <a name="remarks"></a>Poznámky

Implementace objektu hostitele ATL vždy vrátí VARIANT_FALSE jako hodnotu této vlastnosti.

##  <a name="get_showhatching"></a>  IAxWinAmbientDispatch::get_ShowHatching

`ShowHatching` Vedlejší vlastnost umožňuje zjistit, pokud ji by měl vykreslit zasílána ovládacího prvku.

```
STDMETHOD(get_ShowHatching)(VARIANT_BOOL* pbShowHatching);
```

### <a name="parameters"></a>Parametry

*pbShowHatching*<br/>
[out] Adresa proměnné k získání aktuální hodnota této vlastnosti.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnoty HRESULT.

### <a name="remarks"></a>Poznámky

Implementace objektu hostitele ATL vždy vrátí VARIANT_FALSE jako hodnotu této vlastnosti.

##  <a name="get_usermode"></a>  IAxWinAmbientDispatch::get_UserMode

`UserMode` Vlastnost určuje režim okolí uživatele kontejneru.

```
STDMETHOD(get_UserMode)(VARIANT_BOOL* pbUserMode);
```

### <a name="parameters"></a>Parametry

*pbUserMode*<br/>
[out] Adresa proměnné k získání aktuální hodnota této vlastnosti.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnoty HRESULT.

### <a name="remarks"></a>Poznámky

Implementace objektu ATL hostitele používá VARIANT_TRUE jako výchozí hodnota této vlastnosti.

##  <a name="put_allowcontextmenu"></a>  IAxWinAmbientDispatch::put_AllowContextMenu

`AllowContextMenu` Vlastnost určuje, jestli hostované ovládací prvek se může zobrazit kontextovou nabídku.

```
STDMETHOD(put_AllowContextMenu)(VARIANT_BOOL bAllowContextMenu);
```

### <a name="parameters"></a>Parametry

*bAllowContextMenu*<br/>
[in] Nová hodnota této vlastnosti.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnoty HRESULT.

### <a name="remarks"></a>Poznámky

Implementace objektu ATL hostitele používá VARIANT_TRUE jako výchozí hodnota této vlastnosti.

##  <a name="put_allowshowui"></a>  IAxWinAmbientDispatch::put_AllowShowUI

`AllowShowUI` Vlastnost určuje, jestli hostované ovládací prvek se může zobrazit vlastní uživatelské rozhraní.

```
STDMETHOD(put_AllowShowUI)(VARIANT_BOOL bAllowShowUI);
```

### <a name="parameters"></a>Parametry

*bAllowShowUI*<br/>
[in] Nová hodnota této vlastnosti.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnoty HRESULT.

### <a name="remarks"></a>Poznámky

Implementace objektu ATL hostitele používá VARIANT_FALSE jako výchozí hodnota této vlastnosti.

##  <a name="put_allowwindowlessactivation"></a>  IAxWinAmbientDispatch::put_AllowWindowlessActivation

`AllowWindowlessActivation` Vlastnost určuje, zda kontejner bude umožňovat aktivace bez oken.

```
STDMETHOD(put_AllowWindowlessActivation)(VARIANT_BOOL bAllowWindowless);
```

### <a name="parameters"></a>Parametry

*bAllowWindowless*<br/>
[in] Nová hodnota této vlastnosti.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnoty HRESULT.

### <a name="remarks"></a>Poznámky

Implementace objektu ATL hostitele používá VARIANT_TRUE jako výchozí hodnota této vlastnosti.

##  <a name="put_backcolor"></a>  IAxWinAmbientDispatch::put_BackColor

`BackColor` Vlastnost určuje barvu pozadí okolí kontejneru.

```
STDMETHOD(put_BackColor)(OLE_COLOR clrBackground);
```

### <a name="parameters"></a>Parametry

*clrBackground*<br/>
[in] Nová hodnota této vlastnosti.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnoty HRESULT.

### <a name="remarks"></a>Poznámky

Implementace objektu ATL hostitele používá COLOR_BTNFACE nebo COLOR_WINDOW jako výchozí hodnota této vlastnosti (v závislosti na tom, zda nadřazené okno hostitele je dialogové okno, nebo ne).

##  <a name="put_displayasdefault"></a>  IAxWinAmbientDispatch::put_DisplayAsDefault

`DisplayAsDefault` se změní vlastnost ambient umožňující ovládacího prvku a zjistěte, pokud je výchozí ovládací prvek.

```
STDMETHOD(put_DisplayAsDefault)(VARIANT_BOOL bDisplayAsDefault);
```

### <a name="parameters"></a>Parametry

*bDisplayAsDefault*<br/>
[in] Nová hodnota této vlastnosti.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnoty HRESULT.

### <a name="remarks"></a>Poznámky

Implementace objektu ATL hostitele používá VARIANT_FALSE jako výchozí hodnota této vlastnosti.

##  <a name="put_dochostdoubleclickflags"></a>  IAxWinAmbientDispatch::put_DocHostDoubleClickFlags

`DocHostDoubleClickFlags` Vlastnost určuje operaci, která má být provedena v reakci na poklepání.

```
STDMETHOD(put_DocHostDoubleClickFlags)(DWORD dwDocHostDoubleClickFlags);
```

### <a name="parameters"></a>Parametry

*dwDocHostDoubleClickFlags*<br/>
[in] Nová hodnota této vlastnosti.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnoty HRESULT.

### <a name="remarks"></a>Poznámky

Implementace objektu ATL hostitele DOCHOSTUIDBLCLK_DEFAULT používá jako výchozí hodnota této vlastnosti.

##  <a name="put_dochostflags"></a>  IAxWinAmbientDispatch::put_DocHostFlags

`DocHostFlags` Vlastnost určuje možnosti uživatelského rozhraní objektu hostitele.

```
STDMETHOD(put_DocHostFlags)(DWORD dwDocHostFlags);
```

### <a name="parameters"></a>Parametry

*dwDocHostFlags*<br/>
[in] Nová hodnota této vlastnosti.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnoty HRESULT.

### <a name="remarks"></a>Poznámky

Implementace objektu ATL hostitele DOCHOSTUIFLAG_NO3DBORDER používá jako výchozí hodnota této vlastnosti.

##  <a name="put_font"></a>  IAxWinAmbientDispatch::put_Font

`Font` Vlastnost určuje okolí písmo kontejneru.

```
STDMETHOD(put_Font)(IFontDisp* pFont);
```

### <a name="parameters"></a>Parametry

*pFont*<br/>
[in] Nová hodnota této vlastnosti.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnoty HRESULT.

### <a name="remarks"></a>Poznámky

Implementace objektu ATL hostitele používá výchozí písmo grafického uživatelského rozhraní nebo systémové písmo jako výchozí hodnota této vlastnosti.

##  <a name="put_forecolor"></a>  IAxWinAmbientDispatch::put_ForeColor

`ForeColor` Vlastnost určuje barvu popředí okolí kontejneru.

```
STDMETHOD(put_ForeColor)(OLE_COLOR clrForeground);
```

### <a name="parameters"></a>Parametry

*clrForeground*<br/>
[in] Nová hodnota této vlastnosti.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnoty HRESULT.

### <a name="remarks"></a>Poznámky

Implementace objektu ATL hostitele barvu textu okna systému používá jako výchozí hodnota této vlastnosti.

##  <a name="put_localeid"></a>  IAxWinAmbientDispatch::put_LocaleID

`LocaleID` Vlastnost určuje ID národního prostředí okolí kontejneru.

```
STDMETHOD(put_LocaleID)(LCID lcidLocaleID);
```

### <a name="parameters"></a>Parametry

*lcidLocaleID*<br/>
[in] Nová hodnota této vlastnosti.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnoty HRESULT.

### <a name="remarks"></a>Poznámky

Implementace objektu ATL hostitele používá výchozí národní prostředí uživatele jako výchozí hodnota této vlastnosti.

##  <a name="put_messagereflect"></a>  IAxWinAmbientDispatch::put_MessageReflect

`MessageReflect` Vedlejší vlastnost určuje, zda kontejner bude odrážet zprávy do hostovaného ovládacího prvku.

```
STDMETHOD(put_MessageReflect)(VARIANT_BOOL bMessageReflect);
```

### <a name="parameters"></a>Parametry

*bMessageReflect*<br/>
[in] Nová hodnota této vlastnosti.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnoty HRESULT.

### <a name="remarks"></a>Poznámky

Implementace objektu ATL hostitele používá VARIANT_TRUE jako výchozí hodnota této vlastnosti.

##  <a name="put_optionkeypath"></a>  IAxWinAmbientDispatch::put_OptionKeyPath

`OptionKeyPath` Vlastnost určuje cestu ke klíči registru nastavení pro uživatele.

```
STDMETHOD(put_OptionKeyPath)(BSTR bstrOptionKeyPath);
```

### <a name="parameters"></a>Parametry

*bstrOptionKeyPath*<br/>
[in] Nová hodnota této vlastnosti.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnoty HRESULT.

##  <a name="put_usermode"></a>  IAxWinAmbientDispatch::put_UserMode

`UserMode` Vlastnost určuje režim okolí uživatele kontejneru.

```
STDMETHOD(put_UserMode)(VARIANT_BOOL bUserMode);
```

### <a name="parameters"></a>Parametry

*bUserMode*<br/>
[in] Nová hodnota této vlastnosti.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnoty HRESULT.

### <a name="remarks"></a>Poznámky

Implementace objektu ATL hostitele používá VARIANT_TRUE jako výchozí hodnota této vlastnosti.

## <a name="see-also"></a>Viz také

[IAxWinAmbientDispatchEx – rozhraní](../../atl/reference/iaxwinambientdispatchex-interface.md)<br/>
[IAxWinHostWindow – rozhraní](../../atl/reference/iaxwinhostwindow-interface.md)<br/>
[CAxWindow::QueryHost](../../atl/reference/caxwindow-class.md#queryhost)<br/>
[AtlAxGetHost](composite-control-global-functions.md#atlaxgethost)

