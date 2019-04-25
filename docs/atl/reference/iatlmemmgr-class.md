---
title: Iatlmemmgr – třída
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
ms.openlocfilehash: b9b6ac6dc265378f617e053bc48ac6030425cef4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62276246"
---
# <a name="iatlmemmgr-class"></a>Iatlmemmgr – třída

Tato třída reprezentuje rozhraní pro správce paměti.

## <a name="syntax"></a>Syntaxe

```
__interface __declspec(uuid("654F7EF5-CFDF-4df9-A450-6C6A13C622C0")) IAtlMemMgr
```

## <a name="members"></a>Členové

### <a name="methods"></a>Metody

|||
|-|-|
|[přidělení](#allocate)|Volejte tuto metodu za účelem přidělení bloku paměti.|
|[Free](#free)|Volejte tuto metodu pro uvolnění bloku paměti.|
|[GetSize](#getsize)|Volejte tuto metodu, aby se načetla velikost přidělené paměti bloku.|
|[Přidělit jinému uživateli](#reallocate)|Volejte tuto metodu za účelem přidělení bloku paměti.|

## <a name="remarks"></a>Poznámky

Toto rozhraní je implementováno [ccomheap –](../../atl/reference/ccomheap-class.md), [ccrtheap –](../../atl/reference/ccrtheap-class.md), [clocalheap –](../../atl/reference/clocalheap-class.md), [cglobalheap –](../../atl/reference/cglobalheap-class.md), nebo [CWin32Heap](../../atl/reference/cwin32heap-class.md).

> [!NOTE]
>  Funkce místní a globální haldy jsou pomalejší než jiné funkce správy paměti a neposkytuje tolik funkcí. Proto měli používat nové aplikace [haldy funkce](/windows/desktop/Memory/heap-functions). Tyto jsou dostupné v [CWin32Heap](../../atl/reference/cwin32heap-class.md) třídy.

## <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#94](../../atl/codesnippet/cpp/iatlmemmgr-class_1.cpp)]

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlmem.h

##  <a name="allocate"></a>  IAtlMemMgr::Allocate

Volejte tuto metodu za účelem přidělení bloku paměti.

```
void* Allocate(size_t nBytes) throw();
```

### <a name="parameters"></a>Parametry

*nBytes*<br/>
Požadovaný počet bajtů v nového bloku paměti.

### <a name="return-value"></a>Návratová hodnota

Vrací ukazatel na začátek bloku nově přidělenou paměť.

### <a name="remarks"></a>Poznámky

Volání [IAtlMemMgr::Free](#free) nebo [IAtlMemMgr::Reallocate](#reallocate) k uvolnění paměti přidělené touto metodou.

### <a name="example"></a>Příklad

Příklad najdete v tématu [iatlmemmgr – přehled](../../atl/reference/iatlmemmgr-class.md).

##  <a name="free"></a>  IAtlMemMgr::Free

Volejte tuto metodu pro uvolnění bloku paměti.

```
void Free(void* p) throw();
```

### <a name="parameters"></a>Parametry

*p*<br/>
Ukazatel na paměť přidělenou dříve metodou tento správce paměti.

### <a name="remarks"></a>Poznámky

Tuto metodu použijte k uvolnění paměti získá [IAtlMemMgr::Allocate](#allocate) nebo [IAtlMemMgr::Reallocate](#reallocate).

### <a name="example"></a>Příklad

Příklad najdete v tématu [iatlmemmgr – přehled](../../atl/reference/iatlmemmgr-class.md).

##  <a name="getsize"></a>  IAtlMemMgr::GetSize

Volejte tuto metodu, aby se načetla velikost přidělené paměti bloku.

```
size_t GetSize(void* p) throw();
```

### <a name="parameters"></a>Parametry

*p*<br/>
Ukazatel na paměť přidělenou dříve metodou tento správce paměti.

### <a name="return-value"></a>Návratová hodnota

Vrátí velikost bloku paměti v bajtech.

### <a name="example"></a>Příklad

Příklad najdete v tématu [iatlmemmgr – přehled](../../atl/reference/iatlmemmgr-class.md).

##  <a name="reallocate"></a>  IAtlMemMgr::Reallocate

Volejte tuto metodu, aby mohla znovu přidělit paměti přidělené tímto správcem paměti.

```
void* Reallocate(void* p, size_t nBytes) throw();
```

### <a name="parameters"></a>Parametry

*p*<br/>
Ukazatel na paměť přidělenou dříve metodou tento správce paměti.

*nBytes*<br/>
Požadovaný počet bajtů v nového bloku paměti.

### <a name="return-value"></a>Návratová hodnota

Vrací ukazatel na začátek bloku nově přidělenou paměť.

### <a name="remarks"></a>Poznámky

Volání [IAtlMemMgr::Free](#free) nebo [IAtlMemMgr::Reallocate](#reallocate) k uvolnění paměti přidělené touto metodou.

Tato metoda koncepčně uvolní paměť existující a nový blok paměti přidělí. Ve skutečnosti může rozšířit stávající paměť nebo jinak znovu použít.

### <a name="example"></a>Příklad

Příklad najdete v tématu [iatlmemmgr – přehled](../../atl/reference/iatlmemmgr-class.md).

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

##  <a name="setambientdispatch"></a>  IAxWinAmbientDispatchEx::SetAmbientDispatch

Tato metoda je volána k doplnění rozhraní vedlejší vlastnost výchozí uživatelské rozhraní.

```
virtual HRESULT STDMETHODCALLTYPE SetAmbientDispatch(IDispatch* pDispatch) = 0;
```

### <a name="parameters"></a>Parametry

*pDispatch*<br/>
Ukazatel na nové rozhraní.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Při `SetAmbientDispatch` se volá s ukazatelem na nové rozhraní, bude toto nové rozhraní použít k vyvolání žádné vlastnosti nebo metody požádá hostovaného ovládacího prvku, pokud tyto vlastnosti nejsou obsaženy ve [iaxwinambientdispatch –](../../atl/reference/iaxwinambientdispatch-interface.md).

##  <a name="attachcontrol"></a>  IAxWinHostWindow::AttachControl

Ovládací prvek existující (a dřív inicializovaný) připojí ke objekt hostitele pomocí okna identifikovaný *hWnd*.

```
STDMETHOD(AttachControl)(IUnknown* pUnkControl, HWND hWnd);
```

### <a name="parameters"></a>Parametry

*pUnkControl*<br/>
[in] Ukazatel `IUnknown` rozhraní připojené k hostitelský objekt ovládacího prvku.

*hWnd*<br/>
[in] Popisovač okna pro hostování.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnoty HRESULT.

##  <a name="createcontrol"></a>  IAxWinHostWindow::CreateControl

Vytvoří ovládací prvek, inicializuje ji a hostuje ji v okně identifikovaný *hWnd*.

```
STDMETHOD(CreateControl)(
    LPCOLESTR lpTricsData,
    HWND hWnd,
    IStream* pStream);
```

### <a name="parameters"></a>Parametry

*lpTricsData*<br/>
[in] Řetězec, který identifikuje ovládací prvek k vytvoření. Může být identifikátor CLSID (musí obsahovat složené závorky), ProgID, adresa URL nebo nezpracovaný kód HTML (předchází **MSHTML:**).

*hWnd*<br/>
[in] Popisovač okna pro hostování.

*pStream*<br/>
[in] Ukazatel rozhraní pro datový proud obsahující inicializační data pro ovládací prvek. Může mít hodnotu NULL.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnoty HRESULT.

### <a name="remarks"></a>Poznámky

Toto okno se má rozčlenit do podtříd objektem hostitele vystavení toto rozhraní tak, aby se zprávy můžou projeví do ovládacího prvku a další funkce kontejneru bude fungovat.

Voláním této metody je ekvivalentní volání [IAxWinHostWindow::CreateControlEx](#createcontrolex).

Vytvoření licencovaného ovládacího prvku ActiveX, najdete v tématu [IAxWinHostWindowLic::CreateControlLic](#createcontrollicex).

##  <a name="createcontrolex"></a>  IAxWinHostWindow::CreateControlEx

Vytvoří ovládací prvek ActiveX, inicializuje ji a hostuje ji v zadaném okně, podobně jako [IAxWinHostWindow::CreateControl](#createcontrol).

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
[in] Řetězec, který identifikuje ovládací prvek k vytvoření. Může být identifikátor CLSID (musí obsahovat složené závorky), ProgID, adresa URL nebo nezpracovaný kód HTML (s předponou **MSHTML:**).

*hWnd*<br/>
[in] Popisovač okna pro hostování.

*pStream*<br/>
[in] Ukazatel rozhraní pro datový proud obsahující inicializační data pro ovládací prvek. Může mít hodnotu NULL.

*ppUnk*<br/>
[out] Adresa ukazatel, který se zobrazí `IUnknown` rozhraní vytvořený ovládací prvek. Může mít hodnotu NULL.

*riidAdvise*<br/>
[in] Identifikátor rozhraní odchozí rozhraní v obsažený objekt. Může mít hodnotu IID_NULL.

*punkAdvise*<br/>
[in] Ukazatel `IUnknown` rozhraní jímky objektu k připojení k bodu připojení na obsaženého objektu určeného `iidSink`.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnoty HRESULT.

### <a name="remarks"></a>Poznámky

Na rozdíl od `CreateControl` metody `CreateControlEx` také umožňuje přijímat ukazatel rozhraní na nově vytvořený ovládací prvek a nastavit jímky událostí přijímat události vyvolané ovládacího prvku.

Vytvoření licencovaného ovládacího prvku ActiveX, najdete v tématu [IAxWinHostWindowLic::CreateControlLicEx](#createcontrollicex).

##  <a name="querycontrol"></a>  IAxWinHostWindow::QueryControl

Vrátí ukazatel zadané rozhraní poskytovaných hostovaného ovládacího prvku.

```
STDMETHOD(QueryControl)(REFIID riid, void** ppvObject);
```

### <a name="parameters"></a>Parametry

*riid*<br/>
[in] ID rozhraní na ovládací prvek požaduje.

*ppvObject*<br/>
[out] Adresa ukazatel, který se zobrazí zadané rozhraní vytvořený ovládací prvek.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnoty HRESULT.

##  <a name="setexternaldispatch"></a>  IAxWinHostWindow::SetExternalDispatch

Nastaví externí dispinterface, která je k dispozici pro obsažené ovládací prvky prostřednictvím [IDocHostUIHandlerDispatch::GetExternal](../../atl/reference/idochostuihandlerdispatch-interface.md) metody.

```
STDMETHOD(SetExternalDispatch)(IDispatch* pDisp);
```

### <a name="parameters"></a>Parametry

*pDisp*<br/>
[in] Ukazatel `IDispatch` rozhraní.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnoty HRESULT.

##  <a name="setexternaluihandler"></a>  IAxWinHostWindow::SetExternalUIHandler

Voláním této funkce nastavíte externí [idochostuihandlerdispatch –](../../atl/reference/idochostuihandlerdispatch-interface.md) rozhraní `CAxWindow` objektu.

```
STDMETHOD(SetExternalUIHandler)(IDocHostUIHandlerDispatch* pDisp);
```

### <a name="parameters"></a>Parametry

*pDisp*<br/>
[in] Ukazatel `IDocHostUIHandlerDispatch` rozhraní.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnoty HRESULT.

### <a name="remarks"></a>Poznámky

Tato funkce používá ovládací prvky (jako je například ovládací prvek webového prohlížeče), které se dotazují hostitelský server pro `IDocHostUIHandlerDispatch` rozhraní.

##  <a name="createcontrollic"></a>  IAxWinHostWindowLic::CreateControlLic

Vytvoří licencovaného ovládacího prvku, inicializuje ji a hostuje ji v okně identifikovaný `hWnd`.

```
STDMETHOD(CreateControlLic)(
    LPCOLESTR lpTricsData,
    HWND hWnd,
    IStream* pStream,
    BSTR bstrLic);
```

### <a name="parameters"></a>Parametry

*bstrLic*<br/>
[in] BSTR, který obsahuje licenční klíč pro ovládací prvek.

### <a name="remarks"></a>Poznámky

Zobrazit [IAxWinHostWindow::CreateControl](#createcontrol) popis zbývající parametry a návratové hodnoty.

Voláním této metody je ekvivalentní volání [IAxWinHostWindowLic::CreateControlLicEx](#createcontrollicex)

### <a name="example"></a>Příklad

Zobrazit [hostování ActiveX ovládacích prvků pomocí knihovny ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) ukázku, která používá `IAxWinHostWindowLic::CreateControlLic`.

##  <a name="createcontrollicex"></a>  IAxWinHostWindowLic::CreateControlLicEx

Vytvoří licencovaného ovládacího prvku ActiveX, inicializuje ji a hostuje ji v zadaném okně, podobně jako [IAxWinHostWindow::CreateControl](#createcontrol).

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
[in] BSTR, který obsahuje licenční klíč pro ovládací prvek.

### <a name="remarks"></a>Poznámky

Zobrazit [IAxWinHostWindow::CreateControlEx](#createcontrolex) popis zbývající parametry a návratové hodnoty.

### <a name="example"></a>Příklad

Zobrazit [hostování ActiveX ovládacích prvků pomocí knihovny ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) ukázku, která používá `IAxWinHostWindowLic::CreateControlLicEx`.

## <a name="see-also"></a>Viz také:

[Přehled tříd](../../atl/atl-class-overview.md)
