---
title: Třída IAtlMemMgr
ms.date: 11/04/2016
f1_keywords:
- IAtlMemMgr
- ATLMEM/ATL::IAtlMemMgr
- ATLMEM/ATL::Allocate
- ATLMEM/ATL::Free
- ATLMEM/ATL::GetSize
- ATLMEM/ATL::Reallocate
helpviewer_keywords:
- IAtlMemMgr class
- memory, managing
- memory, memory manager
ms.assetid: 18b2c569-25fe-4464-bdb6-3b1abef7154a
ms.openlocfilehash: fcecf716e9d865b1b8590a733216576e0da4c2fb
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81746011"
---
# <a name="iatlmemmgr-class"></a>Třída IAtlMemMgr

Tato třída představuje rozhraní správce paměti.

## <a name="syntax"></a>Syntaxe

```
__interface __declspec(uuid("654F7EF5-CFDF-4df9-A450-6C6A13C622C0")) IAtlMemMgr
```

## <a name="members"></a>Členové

### <a name="methods"></a>Metody

|||
|-|-|
|[Přidělit](#allocate)|Volání této metody přidělit blok paměti.|
|[Free](#free)|Volání této metody uvolnit blok paměti.|
|[GetSize](#getsize)|Volání této metody načíst velikost bloku přidělené paměti.|
|[Přerozdělit](#reallocate)|Volání této metody přerozdělit blok paměti.|

## <a name="remarks"></a>Poznámky

Toto rozhraní je implementováno [CComHeap](../../atl/reference/ccomheap-class.md), [CCRTHeap](../../atl/reference/ccrtheap-class.md), [CLocalHeap](../../atl/reference/clocalheap-class.md), [CGlobalHeap](../../atl/reference/cglobalheap-class.md)nebo [CWin32Heap](../../atl/reference/cwin32heap-class.md).

> [!NOTE]
> Místní a globální haldy funkce jsou pomalejší než jiné funkce správy paměti a neposkytují tolik funkcí. Proto nové aplikace by měly používat [funkce haldy](/windows/win32/Memory/heap-functions). Ty jsou k dispozici ve třídě [CWin32Heap.](../../atl/reference/cwin32heap-class.md)

## <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#94](../../atl/codesnippet/cpp/iatlmemmgr-class_1.cpp)]

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlmem.h

## <a name="iatlmemmgrallocate"></a><a name="allocate"></a>IAtlMemMgr::Přidělit

Volání této metody přidělit blok paměti.

```cpp
void* Allocate(size_t nBytes) throw();
```

### <a name="parameters"></a>Parametry

*nBajtu bajtů*<br/>
Požadovaný počet bajtů v novém bloku paměti.

### <a name="return-value"></a>Návratová hodnota

Vrátí ukazatel na začátek bloku nově přidělené paměti.

### <a name="remarks"></a>Poznámky

Volání [IAtlMemMgr::Free](#free) nebo [IAtlMemMgr::Reallocate](#reallocate) uvolnit paměť přidělené touto metodou.

### <a name="example"></a>Příklad

Například viz [Přehled IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).

## <a name="iatlmemmgrfree"></a><a name="free"></a>IAtlMemMgr::Zdarma

Volání této metody uvolnit blok paměti.

```cpp
void Free(void* p) throw();
```

### <a name="parameters"></a>Parametry

*P*<br/>
Ukazatel na paměť dříve přidělené tímto správcem paměti.

### <a name="remarks"></a>Poznámky

Pomocí této metody můžete uvolnit paměť získanou [iAtlMemMgr::Allocate](#allocate) nebo [IAtlMemMgr::Reallocate](#reallocate).

### <a name="example"></a>Příklad

Například viz [Přehled IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).

## <a name="iatlmemmgrgetsize"></a><a name="getsize"></a>IAtlMemMgr::GetSize

Volání této metody načíst velikost bloku přidělené paměti.

```
size_t GetSize(void* p) throw();
```

### <a name="parameters"></a>Parametry

*P*<br/>
Ukazatel na paměť dříve přidělené tímto správcem paměti.

### <a name="return-value"></a>Návratová hodnota

Vrátí velikost bloku paměti v bajtů.

### <a name="example"></a>Příklad

Například viz [Přehled IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).

## <a name="iatlmemmgrreallocate"></a><a name="reallocate"></a>IAtlMemMgr::Přerozdělit

Volání této metody přerozdělit paměti přidělené tohoto správce paměti.

```cpp
void* Reallocate(void* p, size_t nBytes) throw();
```

### <a name="parameters"></a>Parametry

*P*<br/>
Ukazatel na paměť dříve přidělené tímto správcem paměti.

*nBajtu bajtů*<br/>
Požadovaný počet bajtů v novém bloku paměti.

### <a name="return-value"></a>Návratová hodnota

Vrátí ukazatel na začátek bloku nově přidělené paměti.

### <a name="remarks"></a>Poznámky

Volání [IAtlMemMgr::Free](#free) nebo [IAtlMemMgr::Reallocate](#reallocate) uvolnit paměť přidělené touto metodou.

Koncepčně tato metoda uvolní existující paměti a přiděluje nový blok paměti. Ve skutečnosti může být existující paměť rozšířena nebo jinak znovu použita.

### <a name="example"></a>Příklad

Například viz [Přehled IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).

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

## <a name="iaxwinambientdispatchexsetambientdispatch"></a><a name="setambientdispatch"></a>IAxWinAmbientDispatchEx::SetAmbientDispatch

Tato metoda je volána k doplnění výchozí rozhraní vlastnosti okolí s uživatelem definované rozhraní.

```
virtual HRESULT STDMETHODCALLTYPE SetAmbientDispatch(IDispatch* pDispatch) = 0;
```

### <a name="parameters"></a>Parametry

*pOdeslání*<br/>
Ukazatel na nové rozhraní.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Při `SetAmbientDispatch` volání s ukazatelem na nové rozhraní, toto nové rozhraní se použije k vyvolání všechny vlastnosti nebo metody, které jsou požadovány hostované hostovanou ovládací prvek – pokud tyto vlastnosti již nejsou k dispozici [IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md).

## <a name="iaxwinhostwindowattachcontrol"></a><a name="attachcontrol"></a>IAxWinHostWindow::PřipojitOvládací prvek

Připojí existující (a dříve inicializované) ovládací prvek k objektu hostitele pomocí okna *označeného hWnd*.

```
STDMETHOD(AttachControl)(IUnknown* pUnkControl, HWND hWnd);
```

### <a name="parameters"></a>Parametry

*pUnkControl*<br/>
[v] Ukazatel na `IUnknown` rozhraní ovládacího prvku, který má být připojen k hostitelskému objektu.

*Hwnd*<br/>
[v] Popisovač do okna, které mají být použity pro hostování.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

## <a name="iaxwinhostwindowcreatecontrol"></a><a name="createcontrol"></a>IAxWinHostWindow::Ovládací prvek CreateControl

Vytvoří ovládací prvek, inicializuje jej a hostuje v okně označeném *hWnd*.

```
STDMETHOD(CreateControl)(
    LPCOLESTR lpTricsData,
    HWND hWnd,
    IStream* pStream);
```

### <a name="parameters"></a>Parametry

*lpTricsData*<br/>
[v] Řetězec identifikující ovládací prvek k vytvoření. Může se jednat o kód CLSID (musí obsahovat závorky), progID, adresu URL nebo nezpracovaný kód HTML (předponou **mshtml:**).

*Hwnd*<br/>
[v] Popisovač do okna, které mají být použity pro hostování.

*pStream*<br/>
[v] Ukazatel rozhraní pro datový proud obsahující inicializační data pro ovládací prvek. Může být NULL.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Toto okno bude podtřídou objektem hostitele, který vystavuje toto rozhraní, takže zprávy se mohou odrazit do ovládacího prvku a další funkce kontejneru budou fungovat.

Volání této metody je ekvivalentní volání [IAxWinHostWindow::CreateControlEx](#createcontrolex).

Chcete-li vytvořit licencovaný ovládací prvek ActiveX, přečtěte si informace o tom, že [iAxWinHostWindowLic::CreateControlLic](#createcontrollicex).

## <a name="iaxwinhostwindowcreatecontrolex"></a><a name="createcontrolex"></a>IAxWinHostWindow::CreateControlEx

Vytvoří ovládací prvek ActiveX, inicializuje jej a hostuje v zadaném okně, podobně jako [IAxWinHostWindow::CreateControl](#createcontrol).

```
STDMETHOD(CreateControlEx)(
    LPCOLESTR lpszTricsData,
    HWND hWnd,
    IStream* pStream,
    IUnknown** ppUnk,
    REFIID riidAdvise,
    IUnknown* punkAdvise);
```

### <a name="parameters"></a>Parametry

*lpTricsData*<br/>
[v] Řetězec identifikující ovládací prvek k vytvoření. Může se jednat o kód CLSID (musí obsahovat závorky), progID, adresu URL nebo nezpracovaný kód HTML (s předponou **mshtml:**).

*Hwnd*<br/>
[v] Popisovač do okna, které mají být použity pro hostování.

*pStream*<br/>
[v] Ukazatel rozhraní pro datový proud obsahující inicializační data pro ovládací prvek. Může být NULL.

*ppUnk*<br/>
[out] Adresa ukazatele, který obdrží `IUnknown` rozhraní vytvořeného ovládacího prvku. Může být NULL.

*riidAdvise*<br/>
[v] Identifikátor rozhraní odchozí rozhraní na obsažený objekt. Může být IID_NULL.

*punkAdviseace*<br/>
[v] Ukazatel na `IUnknown` rozhraní objektu jímky, který má být připojen k `iidSink`spojovacímu bodu na obsaženém objektu určeném programem .

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Na `CreateControl` rozdíl `CreateControlEx` od metody také umožňuje přijímat ukazatel rozhraní na nově vytvořený ovládací prvek a nastavit jímka událostí pro příjem událostí vyvolaným ovládacím prvkem.

Chcete-li vytvořit licencovaný ovládací prvek ActiveX, přečtěte si informace o tom, že [iAxWinHostWindowLic::CreateControlLicEx](#createcontrollicex).

## <a name="iaxwinhostwindowquerycontrol"></a><a name="querycontrol"></a>IAxWinHostWindow::Ovládací prvek QueryControl

Vrátí zadaný ukazatel rozhraní poskytoovaný hostovaným ovládacím prvkem.

```
STDMETHOD(QueryControl)(REFIID riid, void** ppvObject);
```

### <a name="parameters"></a>Parametry

*riid řekl:*<br/>
[v] ID rozhraní na ovládací prvek je požadováno.

*ppvObjekt*<br/>
[out] Adresa ukazatele, který obdrží zadané rozhraní vytvořeného ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

## <a name="iaxwinhostwindowsetexternaldispatch"></a><a name="setexternaldispatch"></a>IAxWinHostWindow::SetExternalDispatch

Nastaví externí rozhraní dispinterface, které je k dispozici pro obsažené ovládací prvky prostřednictvím metody [IDocHostUIHandlerDispatch::GetExternal.](../../atl/reference/idochostuihandlerdispatch-interface.md)

```
STDMETHOD(SetExternalDispatch)(IDispatch* pDisp);
```

### <a name="parameters"></a>Parametry

*pDisp*<br/>
[v] Ukazatel na `IDispatch` rozhraní.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

## <a name="iaxwinhostwindowsetexternaluihandler"></a><a name="setexternaluihandler"></a>IAxWinHostWindow::SetExternalUIHandler

Voláním této funkce nastavte externí rozhraní [IDocHostUIHandlerDispatch](../../atl/reference/idochostuihandlerdispatch-interface.md) pro `CAxWindow` objekt.

```
STDMETHOD(SetExternalUIHandler)(IDocHostUIHandlerDispatch* pDisp);
```

### <a name="parameters"></a>Parametry

*pDisp*<br/>
[v] Ukazatel na `IDocHostUIHandlerDispatch` rozhraní.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Tato funkce je používána ovládacími prvky (například ovládacím prvkem `IDocHostUIHandlerDispatch` webového prohlížeče), které dotazují na web hostitele pro rozhraní.

## <a name="iaxwinhostwindowliccreatecontrollic"></a><a name="createcontrollic"></a>IAxWinHostWindowLic::CreateControlLic

Vytvoří licencovaný ovládací prvek, inicializuje jej a hostuje v okně určeném `hWnd`.

```
STDMETHOD(CreateControlLic)(
    LPCOLESTR lpTricsData,
    HWND hWnd,
    IStream* pStream,
    BSTR bstrLic);
```

### <a name="parameters"></a>Parametry

*bstrlic*<br/>
[v] BSTR, který obsahuje licenční klíč pro ovládací prvek.

### <a name="remarks"></a>Poznámky

Viz [IAxWinHostWindow::CreateControl](#createcontrol) pro popis zbývajících parametrů a vrácené hodnoty.

Volání této metody je ekvivalentní volání [IAxWinHostWindowLic::CreateControlLicEx](#createcontrollicex)

### <a name="example"></a>Příklad

Viz [Hostování ovládacích prvků ActiveX pomocí ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) pro ukázku, která používá `IAxWinHostWindowLic::CreateControlLic`.

## <a name="iaxwinhostwindowliccreatecontrollicex"></a><a name="createcontrollicex"></a>IAxWinHostWindowLic::CreateControlLicEx

Vytvoří licencovaný ovládací prvek ActiveX, inicializuje jej a hostuje v zadaném okně, podobně jako [IAxWinHostWindow::CreateControl](#createcontrol).

```
STDMETHOD(CreateControlLicEx)(
    LPCOLESTR lpszTricsData,
    HWND hWnd,
    IStream* pStream,
    IUnknown** ppUnk,
    REFIID riidAdvise,
    IUnknown* punkAdvise,
    BSTR bstrLic);
```

### <a name="parameters"></a>Parametry

*bstrlic*<br/>
[v] BSTR, který obsahuje licenční klíč pro ovládací prvek.

### <a name="remarks"></a>Poznámky

Viz [IAxWinHostWindow::CreateControlEx](#createcontrolex) popis zbývajících parametrů a vrácená hodnota.

### <a name="example"></a>Příklad

Viz [Hostování ovládacích prvků ActiveX pomocí ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) pro ukázku, která používá `IAxWinHostWindowLic::CreateControlLicEx`.

## <a name="see-also"></a>Viz také

[Přehled třídy](../../atl/atl-class-overview.md)
