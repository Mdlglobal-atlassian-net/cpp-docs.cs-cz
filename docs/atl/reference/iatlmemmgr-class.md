---
title: IAtlMemMgr – třída
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
ms.openlocfilehash: a0d79ae95a0604ca75f03673873e99394a1bc295
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79417654"
---
# <a name="iatlmemmgr-class"></a>IAtlMemMgr – třída

Tato třída představuje rozhraní pro správce paměti.

## <a name="syntax"></a>Syntaxe

```
__interface __declspec(uuid("654F7EF5-CFDF-4df9-A450-6C6A13C622C0")) IAtlMemMgr
```

## <a name="members"></a>Členové

### <a name="methods"></a>Metody

|||
|-|-|
|[FISIM](#allocate)|Voláním této metody přidělíte blok paměti.|
|[Free](#free)|Voláním této metody uvolníte blok paměti.|
|[GetSize](#getsize)|Voláním této metody načtete velikost přiděleného bloku paměti.|
|[Znovu přidělte](#reallocate)|Voláním této metody znovu přidělíte blok paměti.|

## <a name="remarks"></a>Poznámky

Toto rozhraní je implementováno pomocí [CComHeap](../../atl/reference/ccomheap-class.md), [CCRTHeap](../../atl/reference/ccrtheap-class.md), [CLocalHeap](../../atl/reference/clocalheap-class.md), [CGlobalHeap](../../atl/reference/cglobalheap-class.md)nebo [CWin32Heap](../../atl/reference/cwin32heap-class.md).

> [!NOTE]
>  Místní a globální funkce haldy jsou pomalejší než jiné funkce správy paměti a neposkytují tolik funkcí. Proto by nové aplikace měly používat [funkce haldy](/windows/win32/Memory/heap-functions). Jsou k dispozici ve třídě [CWin32Heap](../../atl/reference/cwin32heap-class.md) .

## <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#94](../../atl/codesnippet/cpp/iatlmemmgr-class_1.cpp)]

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlmem. h

##  <a name="allocate"></a>IAtlMemMgr:: allocate

Voláním této metody přidělíte blok paměti.

```
void* Allocate(size_t nBytes) throw();
```

### <a name="parameters"></a>Parametry

*nBytes*<br/>
Požadovaný počet bajtů v novém bloku paměti.

### <a name="return-value"></a>Návratová hodnota

Vrátí ukazatel na začátek nově přiděleného bloku paměti.

### <a name="remarks"></a>Poznámky

Zavolejte [IAtlMemMgr:: Free](#free) nebo [IAtlMemMgr:: realokaci](#reallocate) pro uvolnění paměti přidělené touto metodou.

### <a name="example"></a>Příklad

Příklad najdete v [přehledu IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).

##  <a name="free"></a>IAtlMemMgr:: Free

Voláním této metody uvolníte blok paměti.

```
void Free(void* p) throw();
```

### <a name="parameters"></a>Parametry

*trub*<br/>
Ukazatel na paměť, která byla dříve přidělena tímto správcem paměti.

### <a name="remarks"></a>Poznámky

Tuto metodu použijte, pokud chcete uvolnit paměť získanou [IAtlMemMgr:: allocate](#allocate) nebo [IAtlMemMgr:: Reallocate](#reallocate).

### <a name="example"></a>Příklad

Příklad najdete v [přehledu IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).

##  <a name="getsize"></a>IAtlMemMgr:: GetSize

Voláním této metody načtete velikost přiděleného bloku paměti.

```
size_t GetSize(void* p) throw();
```

### <a name="parameters"></a>Parametry

*trub*<br/>
Ukazatel na paměť, která byla dříve přidělena tímto správcem paměti.

### <a name="return-value"></a>Návratová hodnota

Vrátí velikost bloku paměti v bajtech.

### <a name="example"></a>Příklad

Příklad najdete v [přehledu IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).

##  <a name="reallocate"></a>IAtlMemMgr:: realokaci

Zavolejte tuto metodu pro opětovné přidělení paměti přidělené tímto správcem paměti.

```
void* Reallocate(void* p, size_t nBytes) throw();
```

### <a name="parameters"></a>Parametry

*trub*<br/>
Ukazatel na paměť, která byla dříve přidělena tímto správcem paměti.

*nBytes*<br/>
Požadovaný počet bajtů v novém bloku paměti.

### <a name="return-value"></a>Návratová hodnota

Vrátí ukazatel na začátek nově přiděleného bloku paměti.

### <a name="remarks"></a>Poznámky

Zavolejte [IAtlMemMgr:: Free](#free) nebo [IAtlMemMgr:: realokaci](#reallocate) pro uvolnění paměti přidělené touto metodou.

Koncepčně Tato metoda uvolní existující paměť a přidělí nový blok paměti. Ve skutečnosti může být existující paměť rozšířena nebo jinak znovu použita.

### <a name="example"></a>Příklad

Příklad najdete v [přehledu IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).

##  <a name="get_allowcontextmenu"></a>IAxWinAmbientDispatch:: get_AllowContextMenu

Vlastnost `AllowContextMenu` určuje, zda má hostovaný ovládací prvek povoleno zobrazit vlastní kontextovou nabídku.

```
STDMETHOD(get_AllowContextMenu)(VARIANT_BOOL* pbAllowContextMenu);
```

### <a name="parameters"></a>Parametry

*pbAllowContextMenu*<br/>
mimo Adresa proměnné pro přijetí aktuální hodnoty této vlastnosti.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Implementace hostitelského objektu knihovny ATL používá jako výchozí hodnotu této vlastnosti VARIANT_TRUE.

##  <a name="get_allowshowui"></a>IAxWinAmbientDispatch:: get_AllowShowUI

Vlastnost `AllowShowUI` určuje, zda je povoleno zobrazení vlastního uživatelského rozhraní v hostovaném ovládacím prvku.

```
STDMETHOD(get_AllowShowUI)(VARIANT_BOOL* pbAllowShowUI);
```

### <a name="parameters"></a>Parametry

*pbAllowShowUI*<br/>
mimo Adresa proměnné pro přijetí aktuální hodnoty této vlastnosti.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Implementace hostitelského objektu knihovny ATL používá jako výchozí hodnotu této vlastnosti VARIANT_FALSE.

##  <a name="get_allowwindowlessactivation"></a>IAxWinAmbientDispatch:: get_AllowWindowlessActivation

Vlastnost `AllowWindowlessActivation` určuje, zda bude kontejner umožňovat aktivaci bez oken.

```
STDMETHOD(get_AllowWindowlessActivation)(VARIANT_BOOL* pbAllowWindowless);
```

### <a name="parameters"></a>Parametry

*pbAllowWindowless*<br/>
mimo Adresa proměnné pro přijetí aktuální hodnoty této vlastnosti.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Implementace hostitelského objektu knihovny ATL používá jako výchozí hodnotu této vlastnosti VARIANT_TRUE.

##  <a name="get_backcolor"></a>IAxWinAmbientDispatch:: get_BackColor

Vlastnost `BackColor` určuje okolní barvu pozadí kontejneru.

```
STDMETHOD(get_BackColor)(OLE_COLOR* pclrBackground);
```

### <a name="parameters"></a>Parametry

*pclrBackground*<br/>
mimo Adresa proměnné pro přijetí aktuální hodnoty této vlastnosti.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Implementace hostitelského objektu knihovny ATL používá jako výchozí hodnotu této vlastnosti COLOR_BTNFACE nebo COLOR_WINDOW (v závislosti na tom, zda je nadřazeným oknem hostitele dialogové okno nebo ne).

##  <a name="get_displayasdefault"></a>IAxWinAmbientDispatch:: get_DisplayAsDefault

`DisplayAsDefault` je ambientní vlastnost, která umožňuje ovládacímu prvku zjistit, zda se jedná o výchozí ovládací prvek.

```
STDMETHOD(get_DisplayAsDefault)(VARIANT_BOOL* pbDisplayAsDefault);
```

### <a name="parameters"></a>Parametry

*pbDisplayAsDefault*<br/>
mimo Adresa proměnné pro přijetí aktuální hodnoty této vlastnosti.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Implementace hostitelského objektu knihovny ATL používá jako výchozí hodnotu této vlastnosti VARIANT_FALSE.

##  <a name="get_dochostdoubleclickflags"></a>IAxWinAmbientDispatch:: get_DocHostDoubleClickFlags

Vlastnost `DocHostDoubleClickFlags` určuje operaci, která by měla probíhat v reakci na dvakrát kliknout.

```
STDMETHOD(get_DocHostDoubleClickFlags)(DWORD* pdwDocHostDoubleClickFlags);
```

### <a name="parameters"></a>Parametry

*pdwDocHostDoubleClickFlags*<br/>
mimo Adresa proměnné pro přijetí aktuální hodnoty této vlastnosti.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Implementace hostitelského objektu knihovny ATL používá jako výchozí hodnotu této vlastnosti DOCHOSTUIDBLCLK_DEFAULT.

##  <a name="get_dochostflags"></a>IAxWinAmbientDispatch:: get_DocHostFlags

Vlastnost `DocHostFlags` Určuje možnosti uživatelského rozhraní objektu hostitele.

```
STDMETHOD(get_DocHostFlags)(DWORD* pdwDocHostFlags);
```

### <a name="parameters"></a>Parametry

*pdwDocHostFlags*<br/>
mimo Adresa proměnné pro přijetí aktuální hodnoty této vlastnosti.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Implementace hostitelského objektu knihovny ATL používá jako výchozí hodnotu této vlastnosti DOCHOSTUIFLAG_NO3DBORDER.

##  <a name="get_font"></a>IAxWinAmbientDispatch:: get_Font

Vlastnost `Font` určuje okolí písma kontejneru.

```
STDMETHOD(get_Font)(IFontDisp** pFont);
```

### <a name="parameters"></a>Parametry

*pFont*<br/>
mimo Adresa ukazatele rozhraní `IFontDisp` použitá pro příjem aktuální hodnoty této vlastnosti.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Implementace hostitelského objektu knihovny ATL používá jako výchozí hodnotu této vlastnosti výchozí písmo grafického uživatelského rozhraní (GUI) nebo systémové písmo.

##  <a name="get_forecolor"></a>IAxWinAmbientDispatch:: get_ForeColor

Vlastnost `ForeColor` Určuje barvu popředí okolí kontejneru.

```
STDMETHOD(get_ForeColor)(OLE_COLOR* pclrForeground);
```

### <a name="parameters"></a>Parametry

*pclrForeground*<br/>
mimo Adresa proměnné pro přijetí aktuální hodnoty této vlastnosti.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Implementace hostitelského objektu knihovny ATL používá jako výchozí hodnotu této vlastnosti barvu textu okna systému.

##  <a name="get_localeid"></a>IAxWinAmbientDispatch:: get_LocaleID

Vlastnost `LocaleID` Určuje ID okolního prostředí kontejneru.

```
STDMETHOD(get_LocaleID)(LCID* plcidLocaleID);
```

### <a name="parameters"></a>Parametry

*plcidLocaleID*<br/>
mimo Adresa proměnné pro přijetí aktuální hodnoty této vlastnosti.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Implementace objektu hostitele ATL používá výchozí národní prostředí uživatele jako výchozí hodnotu této vlastnosti.

Pomocí této metody můžete zjistit okolní LocalID, tedy LocaleID programu, ve kterém se ovládací prvek používá. Jakmile znáte LocaleID, můžete volat kód pro načtení titulků specifických pro národní prostředí, text chybové zprávy a tak dále ze souboru prostředků nebo satelitní knihovny DLL.

##  <a name="get_messagereflect"></a>IAxWinAmbientDispatch:: get_MessageReflect

Vlastnost Ambient `MessageReflect` určuje, zda kontejner bude odrážet zprávy do hostovaného ovládacího prvku.

```
STDMETHOD(get_MessageReflect)(VARIANT_BOOL* pbMessageReflect);
```

### <a name="parameters"></a>Parametry

*pbMessageReflect*<br/>
mimo Adresa proměnné pro přijetí aktuální hodnoty této vlastnosti.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Implementace hostitelského objektu knihovny ATL používá jako výchozí hodnotu této vlastnosti VARIANT_TRUE.

##  <a name="get_optionkeypath"></a>IAxWinAmbientDispatch:: get_OptionKeyPath

Vlastnost `OptionKeyPath` Určuje cestu ke klíči registru pro nastavení uživatele.

```
STDMETHOD(get_OptionKeyPath)(BSTR* pbstrOptionKeyPath);
```

### <a name="parameters"></a>Parametry

*pbstrOptionKeyPath*<br/>
mimo Adresa proměnné pro přijetí aktuální hodnoty této vlastnosti.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

##  <a name="get_showgrabhandles"></a>IAxWinAmbientDispatch:: get_ShowGrabHandles

Vlastnost Ambient `ShowGrabHandles` umožňuje ovládacímu prvku zjistit, zda se má vykreslovat pomocí táhel.

```
STDMETHOD(get_ShowGrabHandles)(VARIANT_BOOL* pbShowGrabHandles);
```

### <a name="parameters"></a>Parametry

*pbShowGrabHandles*<br/>
mimo Adresa proměnné pro přijetí aktuální hodnoty této vlastnosti.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Implementace objektu hostitele ATL vždy vrací VARIANT_FALSE jako hodnotu této vlastnosti.

##  <a name="get_showhatching"></a>IAxWinAmbientDispatch:: get_ShowHatching

Vlastnost Ambient `ShowHatching` umožňuje ovládacímu prvku zjistit, zda by měl vykreslovat vlastní šrafování.

```
STDMETHOD(get_ShowHatching)(VARIANT_BOOL* pbShowHatching);
```

### <a name="parameters"></a>Parametry

*pbShowHatching*<br/>
mimo Adresa proměnné pro přijetí aktuální hodnoty této vlastnosti.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Implementace objektu hostitele ATL vždy vrací VARIANT_FALSE jako hodnotu této vlastnosti.

##  <a name="get_usermode"></a>IAxWinAmbientDispatch:: get_UserMode

Vlastnost `UserMode` určuje režim okolního uživatele kontejneru.

```
STDMETHOD(get_UserMode)(VARIANT_BOOL* pbUserMode);
```

### <a name="parameters"></a>Parametry

*pbUserMode*<br/>
mimo Adresa proměnné pro přijetí aktuální hodnoty této vlastnosti.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Implementace hostitelského objektu knihovny ATL používá jako výchozí hodnotu této vlastnosti VARIANT_TRUE.

##  <a name="put_allowcontextmenu"></a>IAxWinAmbientDispatch::p ut_AllowContextMenu

Vlastnost `AllowContextMenu` určuje, zda má hostovaný ovládací prvek povoleno zobrazit vlastní kontextovou nabídku.

```
STDMETHOD(put_AllowContextMenu)(VARIANT_BOOL bAllowContextMenu);
```

### <a name="parameters"></a>Parametry

*bAllowContextMenu*<br/>
pro Nová hodnota této vlastnosti

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Implementace hostitelského objektu knihovny ATL používá jako výchozí hodnotu této vlastnosti VARIANT_TRUE.

##  <a name="put_allowshowui"></a>IAxWinAmbientDispatch::p ut_AllowShowUI

Vlastnost `AllowShowUI` určuje, zda je povoleno zobrazení vlastního uživatelského rozhraní v hostovaném ovládacím prvku.

```
STDMETHOD(put_AllowShowUI)(VARIANT_BOOL bAllowShowUI);
```

### <a name="parameters"></a>Parametry

*bAllowShowUI*<br/>
pro Nová hodnota této vlastnosti

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Implementace hostitelského objektu knihovny ATL používá jako výchozí hodnotu této vlastnosti VARIANT_FALSE.

##  <a name="put_allowwindowlessactivation"></a>IAxWinAmbientDispatch::p ut_AllowWindowlessActivation

Vlastnost `AllowWindowlessActivation` určuje, zda bude kontejner umožňovat aktivaci bez oken.

```
STDMETHOD(put_AllowWindowlessActivation)(VARIANT_BOOL bAllowWindowless);
```

### <a name="parameters"></a>Parametry

*bAllowWindowless*<br/>
pro Nová hodnota této vlastnosti

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Implementace hostitelského objektu knihovny ATL používá jako výchozí hodnotu této vlastnosti VARIANT_TRUE.

##  <a name="put_backcolor"></a>IAxWinAmbientDispatch::p ut_BackColor

Vlastnost `BackColor` určuje okolní barvu pozadí kontejneru.

```
STDMETHOD(put_BackColor)(OLE_COLOR clrBackground);
```

### <a name="parameters"></a>Parametry

*clrBackground*<br/>
pro Nová hodnota této vlastnosti

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Implementace hostitelského objektu knihovny ATL používá jako výchozí hodnotu této vlastnosti COLOR_BTNFACE nebo COLOR_WINDOW (v závislosti na tom, zda je nadřazeným oknem hostitele dialogové okno nebo ne).

##  <a name="put_displayasdefault"></a>IAxWinAmbientDispatch::p ut_DisplayAsDefault

`DisplayAsDefault` je ambientní vlastnost, která umožňuje ovládacímu prvku zjistit, zda se jedná o výchozí ovládací prvek.

```
STDMETHOD(put_DisplayAsDefault)(VARIANT_BOOL bDisplayAsDefault);
```

### <a name="parameters"></a>Parametry

*bDisplayAsDefault*<br/>
pro Nová hodnota této vlastnosti

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Implementace hostitelského objektu knihovny ATL používá jako výchozí hodnotu této vlastnosti VARIANT_FALSE.

##  <a name="put_dochostdoubleclickflags"></a>IAxWinAmbientDispatch::p ut_DocHostDoubleClickFlags

Vlastnost `DocHostDoubleClickFlags` určuje operaci, která by měla probíhat v reakci na dvakrát kliknout.

```
STDMETHOD(put_DocHostDoubleClickFlags)(DWORD dwDocHostDoubleClickFlags);
```

### <a name="parameters"></a>Parametry

*dwDocHostDoubleClickFlags*<br/>
pro Nová hodnota této vlastnosti

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Implementace hostitelského objektu knihovny ATL používá jako výchozí hodnotu této vlastnosti DOCHOSTUIDBLCLK_DEFAULT.

##  <a name="put_dochostflags"></a>IAxWinAmbientDispatch::p ut_DocHostFlags

Vlastnost `DocHostFlags` Určuje možnosti uživatelského rozhraní objektu hostitele.

```
STDMETHOD(put_DocHostFlags)(DWORD dwDocHostFlags);
```

### <a name="parameters"></a>Parametry

*dwDocHostFlags*<br/>
pro Nová hodnota této vlastnosti

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Implementace hostitelského objektu knihovny ATL používá jako výchozí hodnotu této vlastnosti DOCHOSTUIFLAG_NO3DBORDER.

##  <a name="put_font"></a>IAxWinAmbientDispatch::p ut_Font

Vlastnost `Font` určuje okolí písma kontejneru.

```
STDMETHOD(put_Font)(IFontDisp* pFont);
```

### <a name="parameters"></a>Parametry

*pFont*<br/>
pro Nová hodnota této vlastnosti

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Implementace hostitelského objektu knihovny ATL používá jako výchozí hodnotu této vlastnosti výchozí písmo grafického uživatelského rozhraní (GUI) nebo systémové písmo.

##  <a name="put_forecolor"></a>IAxWinAmbientDispatch::p ut_ForeColor

Vlastnost `ForeColor` Určuje barvu popředí okolí kontejneru.

```
STDMETHOD(put_ForeColor)(OLE_COLOR clrForeground);
```

### <a name="parameters"></a>Parametry

*clrForeground*<br/>
pro Nová hodnota této vlastnosti

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Implementace hostitelského objektu knihovny ATL používá jako výchozí hodnotu této vlastnosti barvu textu okna systému.

##  <a name="put_localeid"></a>IAxWinAmbientDispatch::p ut_LocaleID

Vlastnost `LocaleID` Určuje ID okolního prostředí kontejneru.

```
STDMETHOD(put_LocaleID)(LCID lcidLocaleID);
```

### <a name="parameters"></a>Parametry

*lcidLocaleID*<br/>
pro Nová hodnota této vlastnosti

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Implementace objektu hostitele ATL používá výchozí národní prostředí uživatele jako výchozí hodnotu této vlastnosti.

##  <a name="put_messagereflect"></a>IAxWinAmbientDispatch::p ut_MessageReflect

Vlastnost Ambient `MessageReflect` určuje, zda kontejner bude odrážet zprávy do hostovaného ovládacího prvku.

```
STDMETHOD(put_MessageReflect)(VARIANT_BOOL bMessageReflect);
```

### <a name="parameters"></a>Parametry

*bMessageReflect*<br/>
pro Nová hodnota této vlastnosti

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Implementace hostitelského objektu knihovny ATL používá jako výchozí hodnotu této vlastnosti VARIANT_TRUE.

##  <a name="put_optionkeypath"></a>IAxWinAmbientDispatch::p ut_OptionKeyPath

Vlastnost `OptionKeyPath` Určuje cestu ke klíči registru pro nastavení uživatele.

```
STDMETHOD(put_OptionKeyPath)(BSTR bstrOptionKeyPath);
```

### <a name="parameters"></a>Parametry

*bstrOptionKeyPath*<br/>
pro Nová hodnota této vlastnosti

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

##  <a name="put_usermode"></a>IAxWinAmbientDispatch::p ut_UserMode

Vlastnost `UserMode` určuje režim okolního uživatele kontejneru.

```
STDMETHOD(put_UserMode)(VARIANT_BOOL bUserMode);
```

### <a name="parameters"></a>Parametry

*bUserMode*<br/>
pro Nová hodnota této vlastnosti

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Implementace hostitelského objektu knihovny ATL používá jako výchozí hodnotu této vlastnosti VARIANT_TRUE.

##  <a name="setambientdispatch"></a>IAxWinAmbientDispatchEx::SetAmbientDispatch

Tato metoda je volána pro doplnění výchozího rozhraní vnější vlastnosti s uživatelsky definovaným rozhraním.

```
virtual HRESULT STDMETHODCALLTYPE SetAmbientDispatch(IDispatch* pDispatch) = 0;
```

### <a name="parameters"></a>Parametry

*pDispatch*<br/>
Ukazatel na nové rozhraní.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Při volání `SetAmbientDispatch` s ukazatelem na nové rozhraní se toto nové rozhraní použije k vyvolání jakýchkoli vlastností nebo metod, které požadoval hostovaný ovládací prvek – Pokud tyto vlastnosti ještě nejsou poskytovány funkcí [IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md).

##  <a name="attachcontrol"></a>IAxWinHostWindow::AttachControl

Připojí existující ovládací prvek (a dříve inicializovaný) k objektu hostitele pomocí okna určeného prvkem *HWND*.

```
STDMETHOD(AttachControl)(IUnknown* pUnkControl, HWND hWnd);
```

### <a name="parameters"></a>Parametry

*pUnkControl*<br/>
pro Ukazatel na `IUnknown` rozhraní ovládacího prvku, který se má připojit k objektu hostitele.

*hWnd*<br/>
pro Popisovač okna, který se má použít pro hostování.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

##  <a name="createcontrol"></a>IAxWinHostWindow::CreateControl

Vytvoří ovládací prvek, inicializuje ho a hostuje ho v okně identifikovaném pomocí *HWND*.

```
STDMETHOD(CreateControl)(
    LPCOLESTR lpTricsData,
    HWND hWnd,
    IStream* pStream);
```

### <a name="parameters"></a>Parametry

*lpTricsData*<br/>
pro Řetězec identifikující ovládací prvek, který má být vytvořen. Může se jednat o CLSID (musí zahrnovat složené závorky), ProgID, URL nebo raw HTML (s předponou **MSHTML:** ).

*hWnd*<br/>
pro Popisovač okna, který se má použít pro hostování.

*pStream*<br/>
pro Ukazatel rozhraní pro datový proud, který obsahuje inicializační data ovládacího prvku. Může mít hodnotu NULL.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Toto okno bude podtřídit objektem hostitele, který toto rozhraní vystavuje, aby bylo možné zprávy odrážet s ovládacím prvkem a další funkce kontejneru budou fungovat.

Volání této metody je ekvivalentní volání metody [IAxWinHostWindow:: CreateControlEx](#createcontrolex).

Chcete-li vytvořit licencovaný ovládací prvek ActiveX, přečtěte si téma [IAxWinHostWindowLic:: CreateControlLic](#createcontrollicex).

##  <a name="createcontrolex"></a>IAxWinHostWindow::CreateControlEx

Vytvoří ovládací prvek ActiveX, inicializuje ho a hostuje v zadaném okně, podobně jako [IAxWinHostWindow:: CreateControl](#createcontrol).

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
pro Řetězec identifikující ovládací prvek, který má být vytvořen. Může to být CLSID (musí zahrnovat složené závorky), ProgID, URL nebo raw HTML (s předponou **MSHTML:** ).

*hWnd*<br/>
pro Popisovač okna, který se má použít pro hostování.

*pStream*<br/>
pro Ukazatel rozhraní pro datový proud, který obsahuje inicializační data ovládacího prvku. Může mít hodnotu NULL.

*ppUnk*<br/>
mimo Adresa ukazatele, který získá `IUnknown` rozhraní vytvořeného ovládacího prvku. Může mít hodnotu NULL.

*riidAdvise*<br/>
pro Identifikátor rozhraní odchozího rozhraní u objektu, který ho obsahuje. Lze IID_NULL.

*punkAdvise*<br/>
pro Ukazatel na `IUnknown` rozhraní objektu jímky, který má být připojen k bodu připojení v objektu, který je určen `iidSink`.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Na rozdíl od metody `CreateControl`, `CreateControlEx` také umožňuje získat ukazatel rozhraní na nově vytvořený ovládací prvek a nastavit jímku událostí pro příjem událostí vyvolaných ovládacím prvkem.

Chcete-li vytvořit licencovaný ovládací prvek ActiveX, přečtěte si téma [IAxWinHostWindowLic:: CreateControlLicEx](#createcontrollicex).

##  <a name="querycontrol"></a>IAxWinHostWindow::QueryControl

Vrátí zadaný ukazatel rozhraní poskytnutý hostovaným ovládacím prvkem.

```
STDMETHOD(QueryControl)(REFIID riid, void** ppvObject);
```

### <a name="parameters"></a>Parametry

*riid*<br/>
pro IDENTIFIKÁTOR rozhraní na ovládacím prvku, který se požaduje.

*ppvObject*<br/>
mimo Adresa ukazatele, který získá určené rozhraní vytvořeného ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

##  <a name="setexternaldispatch"></a>IAxWinHostWindow::SetExternalDispatch

Nastaví externí odesílající rozhraní, které je k dispozici pro obsažené ovládací prvky prostřednictvím metody [IDocHostUIHandlerDispatch:: getexternal](../../atl/reference/idochostuihandlerdispatch-interface.md) .

```
STDMETHOD(SetExternalDispatch)(IDispatch* pDisp);
```

### <a name="parameters"></a>Parametry

*pDisp*<br/>
pro Ukazatel na rozhraní `IDispatch`.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

##  <a name="setexternaluihandler"></a>IAxWinHostWindow::SetExternalUIHandler

Voláním této funkce nastavíte externí rozhraní [IDocHostUIHandlerDispatch](../../atl/reference/idochostuihandlerdispatch-interface.md) pro objekt `CAxWindow`.

```
STDMETHOD(SetExternalUIHandler)(IDocHostUIHandlerDispatch* pDisp);
```

### <a name="parameters"></a>Parametry

*pDisp*<br/>
pro Ukazatel na rozhraní `IDocHostUIHandlerDispatch`.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Tato funkce je používána ovládacími prvky (jako je ovládací prvek webového prohlížeče), který se dotazuje na web hostitele pro rozhraní `IDocHostUIHandlerDispatch`.

##  <a name="createcontrollic"></a>IAxWinHostWindowLic::CreateControlLic

Vytvoří licencovaný ovládací prvek, inicializuje ho a hostuje ho v okně určeném `hWnd`.

```
STDMETHOD(CreateControlLic)(
    LPCOLESTR lpTricsData,
    HWND hWnd,
    IStream* pStream,
    BSTR bstrLic);
```

### <a name="parameters"></a>Parametry

*bstrLic*<br/>
pro BSTR, který obsahuje licenční klíč pro ovládací prvek.

### <a name="remarks"></a>Poznámky

Popis zbývajících parametrů a návratové hodnoty naleznete v tématu [IAxWinHostWindow:: CreateControl](#createcontrol) .

Volání této metody je ekvivalentní volání metody [IAxWinHostWindowLic:: CreateControlLicEx](#createcontrollicex)

### <a name="example"></a>Příklad

Ukázku, která používá `IAxWinHostWindowLic::CreateControlLic`, najdete v tématu [hostování ovládacích prvků ActiveX pomocí ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) .

##  <a name="createcontrollicex"></a>IAxWinHostWindowLic::CreateControlLicEx

Vytvoří licencovaný ovládací prvek ActiveX, inicializuje ho a hostuje v zadaném okně, podobně jako [IAxWinHostWindow:: CreateControl](#createcontrol).

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

*bstrLic*<br/>
pro BSTR, který obsahuje licenční klíč pro ovládací prvek.

### <a name="remarks"></a>Poznámky

Popis zbývajících parametrů a návratové hodnoty naleznete v tématu [IAxWinHostWindow:: CreateControlEx](#createcontrolex) .

### <a name="example"></a>Příklad

Ukázku, která používá `IAxWinHostWindowLic::CreateControlLicEx`, najdete v tématu [hostování ovládacích prvků ActiveX pomocí ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) .

## <a name="see-also"></a>Viz také

[Přehled třídy](../../atl/atl-class-overview.md)
