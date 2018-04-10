---
title: Třída IAtlMemMgr | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- IAtlMemMgr
- ATLMEM/ATL::IAtlMemMgr
- ATLMEM/ATL::Allocate
- ATLMEM/ATL::Free
- ATLMEM/ATL::GetSize
- ATLMEM/ATL::Reallocate
dev_langs:
- C++
helpviewer_keywords:
- IAtlMemMgr class
- memory, managing
- memory, memory manager
ms.assetid: 18b2c569-25fe-4464-bdb6-3b1abef7154a
caps.latest.revision: 21
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a9c9380bddb9b406d9a3e6233a87870ab81df5c2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="iatlmemmgr-class"></a>IAtlMemMgr – třída
Tato třída reprezentuje rozhraní pro správce paměti.  
  
## <a name="syntax"></a>Syntaxe  
  
```
__interface __declspec(uuid("654F7EF5-CFDF-4df9-A450-6C6A13C622C0")) IAtlMemMgr
```  
  
## <a name="members"></a>Členové  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[Přidělit](#allocate)|Voláním této metody lze přidělit blok paměti.|  
|[Volné](#free)|Volejte tuto metodu k bezplatným bloku paměti.|  
|[Getsize –](#getsize)|Volejte tuto metodu za účelem načtení velikost bloku přidělené paměti.|  
|[Přidělit jinému uživateli](#reallocate)|Volejte tuto metodu a znovu přidělte bloku paměti.|  
  
## <a name="remarks"></a>Poznámky  
 Toto rozhraní je implementováno modulem [CComHeap](../../atl/reference/ccomheap-class.md), [CCRTHeap](../../atl/reference/ccrtheap-class.md), [CLocalHeap](../../atl/reference/clocalheap-class.md), [CGlobalHeap](../../atl/reference/cglobalheap-class.md), nebo [CWin32Heap](../../atl/reference/cwin32heap-class.md).  
  
> [!NOTE]
>  Funkce hald místní a globální jsou nižší než jiné funkce správy paměti a neposkytuje jako řadu funkcí. Proto měli používat nové aplikace [haldy funkce](http://msdn.microsoft.com/library/windows/desktop/aa366711). Tyto jsou k dispozici v [CWin32Heap](../../atl/reference/cwin32heap-class.md) třídy.  
  
## <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Utilities#94](../../atl/codesnippet/cpp/iatlmemmgr-class_1.cpp)]  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlmem.h  
  
##  <a name="allocate"></a>IAtlMemMgr::Allocate  
 Voláním této metody lze přidělit blok paměti.  
  
```
void* Allocate(size_t nBytes) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `nBytes`  
 Požadovaný počet bajtů v nového bloku paměti.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrací ukazatel na začátku bloku nově přidělených paměti.  
  
### <a name="remarks"></a>Poznámky  
 Volání [IAtlMemMgr::Free](#free) nebo [IAtlMemMgr::Reallocate](#reallocate) k bezplatným je paměť přidělená touto metodou.  
  
### <a name="example"></a>Příklad  
 Příklad, naleznete v části [IAtlMemMgr přehled](../../atl/reference/iatlmemmgr-class.md).  
  
##  <a name="free"></a>IAtlMemMgr::Free  
 Volejte tuto metodu k bezplatným bloku paměti.  
  
```
void Free(void* p) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `p`  
 Ukazatel na paměti dříve přidělené tomuto správci paměti.  
  
### <a name="remarks"></a>Poznámky  
 Pomocí této metody můžete uvolnit paměť získat [IAtlMemMgr::Allocate](#allocate) nebo [IAtlMemMgr::Reallocate](#reallocate).  
  
### <a name="example"></a>Příklad  
 Příklad, naleznete v části [IAtlMemMgr přehled](../../atl/reference/iatlmemmgr-class.md).  
  
##  <a name="getsize"></a>IAtlMemMgr::GetSize  
 Volejte tuto metodu za účelem načtení velikost bloku přidělené paměti.  
  
```
size_t GetSize(void* p) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `p`  
 Ukazatel na paměti dříve přidělené tomuto správci paměti.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí velikost bloku paměti v bajtech.  
  
### <a name="example"></a>Příklad  
 Příklad, naleznete v části [IAtlMemMgr přehled](../../atl/reference/iatlmemmgr-class.md).  
  
##  <a name="reallocate"></a>IAtlMemMgr::Reallocate  
 Volejte tuto metodu a znovu přidělte paměti přidělené tomuto správci paměti.  
  
```
void* Reallocate(void* p, size_t nBytes) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `p`  
 Ukazatel na paměti dříve přidělené tomuto správci paměti.  
  
 `nBytes`  
 Požadovaný počet bajtů v nového bloku paměti.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrací ukazatel na začátku bloku nově přidělených paměti.  
  
### <a name="remarks"></a>Poznámky  
 Volání [IAtlMemMgr::Free](#free) nebo [IAtlMemMgr::Reallocate](#reallocate) k bezplatným je paměť přidělená touto metodou.  
  
 Tato metoda koncepčně uvolní existující paměti a přiděluje nový blok paměti. Ve skutečnosti může rozšířené existující paměti nebo jinak znovu použít.  
  
### <a name="example"></a>Příklad  
 Příklad, naleznete v části [IAtlMemMgr přehled](../../atl/reference/iatlmemmgr-class.md).  
  
##  <a name="get_allowcontextmenu"></a>IAxWinAmbientDispatch::get_AllowContextMenu  
 **AllowContextMenu** vlastnost určuje, jestli hostované ovládací prvek může zobrazit svůj vlastní místní nabídce.  
  
```
STDMETHOD(get_AllowContextMenu)(VARIANT_BOOL* pbAllowContextMenu);
```  
  
### <a name="parameters"></a>Parametry  
 *pbAllowContextMenu*  
 [out] Adresa proměnnou, která bude přijímat aktuální hodnota této vlastnosti.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT` hodnotu.  
  
### <a name="remarks"></a>Poznámky  
 Implementace objektu hostitele ATL používá `VARIANT_TRUE` jako výchozí hodnota této vlastnosti.  
  
##  <a name="get_allowshowui"></a>IAxWinAmbientDispatch::get_AllowShowUI  
 **AllowShowUI** vlastnost určuje, jestli hostované ovládací prvek může zobrazit svůj vlastní uživatelské rozhraní.  
  
```
STDMETHOD(get_AllowShowUI)(VARIANT_BOOL* pbAllowShowUI);
```  
  
### <a name="parameters"></a>Parametry  
 *pbAllowShowUI*  
 [out] Adresa proměnnou, která bude přijímat aktuální hodnota této vlastnosti.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT` hodnotu.  
  
### <a name="remarks"></a>Poznámky  
 Implementace objektu hostitele ATL používá **VARIANT_FALSE** jako výchozí hodnota této vlastnosti.  
  
##  <a name="get_allowwindowlessactivation"></a>IAxWinAmbientDispatch::get_AllowWindowlessActivation  
 **AllowWindowlessActivation** vlastnost určuje, zda kontejner umožní aktivace bez oken.  
  
```
STDMETHOD(get_AllowWindowlessActivation)(VARIANT_BOOL* pbAllowWindowless);
```  
  
### <a name="parameters"></a>Parametry  
 *pbAllowWindowless*  
 [out] Adresa proměnnou, která bude přijímat aktuální hodnota této vlastnosti.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT` hodnotu.  
  
### <a name="remarks"></a>Poznámky  
 Implementace objektu hostitele ATL používá `VARIANT_TRUE` jako výchozí hodnota této vlastnosti.  
  
##  <a name="get_backcolor"></a>IAxWinAmbientDispatch::get_BackColor  
 `BackColor` Vlastnost určuje barvu pozadí vedlejším kontejneru.  
  
```
STDMETHOD(get_BackColor)(OLE_COLOR* pclrBackground);
```  
  
### <a name="parameters"></a>Parametry  
 *pclrBackground*  
 [out] Adresa proměnnou, která bude přijímat aktuální hodnota této vlastnosti.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT` hodnotu.  
  
### <a name="remarks"></a>Poznámky  
 Implementace objektu hostitele ATL používá **COLOR_BTNFACE** nebo **COLOR_WINDOW** jako výchozí hodnota této vlastnosti (v závislosti na tom, zda nadřazeného okna hostitele je dialogové okno, nebo ne).  
  
##  <a name="get_displayasdefault"></a>IAxWinAmbientDispatch::get_DisplayAsDefault  
 **DisplayAsDefault** je vedlejším vlastnost, která vám umožní kontrolu a zjistěte, zda se jedná o výchozí ovládací prvek.  
  
```
STDMETHOD(get_DisplayAsDefault)(VARIANT_BOOL* pbDisplayAsDefault);
```  
  
### <a name="parameters"></a>Parametry  
 *pbDisplayAsDefault*  
 [out] Adresa proměnnou, která bude přijímat aktuální hodnota této vlastnosti.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT` hodnotu.  
  
### <a name="remarks"></a>Poznámky  
 Implementace objektu hostitele ATL používá **VARIANT_FALSE** jako výchozí hodnota této vlastnosti.  
  
##  <a name="get_dochostdoubleclickflags"></a>IAxWinAmbientDispatch::get_DocHostDoubleClickFlags  
 **DocHostDoubleClickFlags** vlastnost určuje operaci, která má být provedena v reakci na poklikejte na soubor.  
  
```
STDMETHOD(get_DocHostDoubleClickFlags)(DWORD* pdwDocHostDoubleClickFlags);
```  
  
### <a name="parameters"></a>Parametry  
 *pdwDocHostDoubleClickFlags*  
 [out] Adresa proměnnou, která bude přijímat aktuální hodnota této vlastnosti.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT` hodnotu.  
  
### <a name="remarks"></a>Poznámky  
 Implementace objektu hostitele ATL používá **DOCHOSTUIDBLCLK_DEFAULT** jako výchozí hodnota této vlastnosti.  
  
##  <a name="get_dochostflags"></a>IAxWinAmbientDispatch::get_DocHostFlags  
 **DocHostFlags** vlastnost určuje možnosti uživatelského rozhraní objektu hostitele.  
  
```
STDMETHOD(get_DocHostFlags)(DWORD* pdwDocHostFlags);
```  
  
### <a name="parameters"></a>Parametry  
 *pdwDocHostFlags*  
 [out] Adresa proměnnou, která bude přijímat aktuální hodnota této vlastnosti.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT` hodnotu.  
  
### <a name="remarks"></a>Poznámky  
 Implementace objektu hostitele ATL používá **DOCHOSTUIFLAG_NO3DBORDER** jako výchozí hodnota této vlastnosti.  
  
##  <a name="get_font"></a>IAxWinAmbientDispatch::get_Font  
 **Písma** vlastnost určuje vedlejším písmo kontejneru.  
  
```
STDMETHOD(get_Font)(IFontDisp** pFont);
```  
  
### <a name="parameters"></a>Parametry  
 `pFont`  
 [out] Adresa **IFontDisp** ukazatel rozhraní používá k přijetí aktuální hodnota této vlastnosti.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT` hodnotu.  
  
### <a name="remarks"></a>Poznámky  
 Implementace objektu ATL hostitele používá výchozí písmo grafického uživatelského rozhraní nebo písmo systému jako výchozí hodnota této vlastnosti.  
  
##  <a name="get_forecolor"></a>IAxWinAmbientDispatch::get_ForeColor  
 `ForeColor` Vlastnost určuje barvu popředí vedlejším kontejneru.  
  
```
STDMETHOD(get_ForeColor)(OLE_COLOR* pclrForeground);
```  
  
### <a name="parameters"></a>Parametry  
 *pclrForeground*  
 [out] Adresa proměnnou, která bude přijímat aktuální hodnota této vlastnosti.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT` hodnotu.  
  
### <a name="remarks"></a>Poznámky  
 Implementace objektu hostitele ATL používá systém okno barvy jako výchozí hodnota této vlastnosti.  
  
##  <a name="get_localeid"></a>IAxWinAmbientDispatch::get_LocaleID  
 **LocaleID** vlastnost určuje ID národního prostředí vedlejším kontejneru.  
  
```
STDMETHOD(get_LocaleID)(LCID* plcidLocaleID);
```  
  
### <a name="parameters"></a>Parametry  
 *plcidLocaleID*  
 [out] Adresa proměnnou, která bude přijímat aktuální hodnota této vlastnosti.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT` hodnotu.  
  
### <a name="remarks"></a>Poznámky  
 Implementace objektu hostitele ATL používá výchozí národní prostředí uživatele jako výchozí hodnota této vlastnosti.  
  
 Pomocí této metody můžete zjistit vedlejším LocalID, který je identifikátor národního prostředí programu vlastního ovládacího prvku se používá v. Jakmile znáte identifikátor národního prostředí, můžete volat kód pro načtení specifická pro národní prostředí titulky text chybové zprávy, a tak dále ze souboru prostředků nebo satelitní knihovny DLL.  
  
##  <a name="get_messagereflect"></a>IAxWinAmbientDispatch::get_MessageReflect  
 **MessageReflect** – vedlejší vlastnost určuje, zda kontejner bude odrážet zprávy do ovládacího prvku hostované.  
  
```
STDMETHOD(get_MessageReflect)(VARIANT_BOOL* pbMessageReflect);
```  
  
### <a name="parameters"></a>Parametry  
 *pbMessageReflect*  
 [out] Adresa proměnnou, která bude přijímat aktuální hodnota této vlastnosti.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT` hodnotu.  
  
### <a name="remarks"></a>Poznámky  
 Implementace objektu hostitele ATL používá `VARIANT_TRUE` jako výchozí hodnota této vlastnosti.  
  
##  <a name="get_optionkeypath"></a>IAxWinAmbientDispatch::get_OptionKeyPath  
 **OptionKeyPath** vlastnost určuje cestu klíče registru nastavení pro uživatele.  
  
```
STDMETHOD(get_OptionKeyPath)(BSTR* pbstrOptionKeyPath);
```  
  
### <a name="parameters"></a>Parametry  
 *pbstrOptionKeyPath*  
 [out] Adresa proměnnou, která bude přijímat aktuální hodnota této vlastnosti.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT` hodnotu.  
  
##  <a name="get_showgrabhandles"></a>IAxWinAmbientDispatch::get_ShowGrabHandles  
 **ShowGrabHandles** – vedlejší vlastnost umožňuje zjistit, pokud ho (RTL) vykreslovat samotné s okamžitými výsledky popisovače ovládacího prvku.  
  
```
STDMETHOD(get_ShowGrabHandles)(VARIANT_BOOL* pbShowGrabHandles);
```  
  
### <a name="parameters"></a>Parametry  
 *pbShowGrabHandles*  
 [out] Adresa proměnnou, která bude přijímat aktuální hodnota této vlastnosti.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT` hodnotu.  
  
### <a name="remarks"></a>Poznámky  
 Implementace objektu hostitele ATL vždy vrátí **VARIANT_FALSE** jako hodnota této vlastnosti.  
  
##  <a name="get_showhatching"></a>IAxWinAmbientDispatch::get_ShowHatching  
 **ShowHatching** – vedlejší vlastnost umožňuje zjistit, pokud ho měli kreslení samotné zasílána ovládacího prvku.  
  
```
STDMETHOD(get_ShowHatching)(VARIANT_BOOL* pbShowHatching);
```  
  
### <a name="parameters"></a>Parametry  
 *pbShowHatching*  
 [out] Adresa proměnnou, která bude přijímat aktuální hodnota této vlastnosti.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT` hodnotu.  
  
### <a name="remarks"></a>Poznámky  
 Implementace objektu hostitele ATL vždy vrátí **VARIANT_FALSE** jako hodnota této vlastnosti.  
  
##  <a name="get_usermode"></a>IAxWinAmbientDispatch::get_UserMode  
 **Přesměrovač** vlastnost určuje režim vedlejším uživatele kontejneru.  
  
```
STDMETHOD(get_UserMode)(VARIANT_BOOL* pbUserMode);
```  
  
### <a name="parameters"></a>Parametry  
 *pbUserMode*  
 [out] Adresa proměnnou, která bude přijímat aktuální hodnota této vlastnosti.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT` hodnotu.  
  
### <a name="remarks"></a>Poznámky  
 Implementace objektu hostitele ATL používá `VARIANT_TRUE` jako výchozí hodnota této vlastnosti.  
  
##  <a name="put_allowcontextmenu"></a>IAxWinAmbientDispatch::put_AllowContextMenu  
 **AllowContextMenu** vlastnost určuje, jestli hostované ovládací prvek může zobrazit svůj vlastní místní nabídce.  
  
```
STDMETHOD(put_AllowContextMenu)(VARIANT_BOOL bAllowContextMenu);
```  
  
### <a name="parameters"></a>Parametry  
 *bAllowContextMenu*  
 [v] Nová hodnota této vlastnosti.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT` hodnotu.  
  
### <a name="remarks"></a>Poznámky  
 Implementace objektu hostitele ATL používá `VARIANT_TRUE` jako výchozí hodnota této vlastnosti.  
  
##  <a name="put_allowshowui"></a>IAxWinAmbientDispatch::put_AllowShowUI  
 **AllowShowUI** vlastnost určuje, jestli hostované ovládací prvek může zobrazit svůj vlastní uživatelské rozhraní.  
  
```
STDMETHOD(put_AllowShowUI)(VARIANT_BOOL bAllowShowUI);
```  
  
### <a name="parameters"></a>Parametry  
 *bAllowShowUI*  
 [v] Nová hodnota této vlastnosti.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT` hodnotu.  
  
### <a name="remarks"></a>Poznámky  
 Implementace objektu hostitele ATL používá **VARIANT_FALSE** jako výchozí hodnota této vlastnosti.  
  
##  <a name="put_allowwindowlessactivation"></a>IAxWinAmbientDispatch::put_AllowWindowlessActivation  
 **AllowWindowlessActivation** vlastnost určuje, zda kontejner umožní aktivace bez oken.  
  
```
STDMETHOD(put_AllowWindowlessActivation)(VARIANT_BOOL bAllowWindowless);
```  
  
### <a name="parameters"></a>Parametry  
 *bAllowWindowless*  
 [v] Nová hodnota této vlastnosti.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT` hodnotu.  
  
### <a name="remarks"></a>Poznámky  
 Implementace objektu hostitele ATL používá `VARIANT_TRUE` jako výchozí hodnota této vlastnosti.  
  
##  <a name="put_backcolor"></a>IAxWinAmbientDispatch::put_BackColor  
 `BackColor` Vlastnost určuje barvu pozadí vedlejším kontejneru.  
  
```
STDMETHOD(put_BackColor)(OLE_COLOR clrBackground);
```  
  
### <a name="parameters"></a>Parametry  
 *clrBackground*  
 [v] Nová hodnota této vlastnosti.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT` hodnotu.  
  
### <a name="remarks"></a>Poznámky  
 Implementace objektu hostitele ATL používá **COLOR_BTNFACE** nebo **COLOR_WINDOW** jako výchozí hodnota této vlastnosti (v závislosti na tom, zda nadřazeného okna hostitele je dialogové okno, nebo ne).  
  
##  <a name="put_displayasdefault"></a>IAxWinAmbientDispatch::put_DisplayAsDefault  
 **DisplayAsDefault** je vedlejším vlastnost, která vám umožní kontrolu a zjistěte, zda se jedná o výchozí ovládací prvek.  
  
```
STDMETHOD(put_DisplayAsDefault)(VARIANT_BOOL bDisplayAsDefault);
```  
  
### <a name="parameters"></a>Parametry  
 `bDisplayAsDefault`  
 [v] Nová hodnota této vlastnosti.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT` hodnotu.  
  
### <a name="remarks"></a>Poznámky  
 Implementace objektu hostitele ATL používá **VARIANT_FALSE** jako výchozí hodnota této vlastnosti.  
  
##  <a name="put_dochostdoubleclickflags"></a>IAxWinAmbientDispatch::put_DocHostDoubleClickFlags  
 **DocHostDoubleClickFlags** vlastnost určuje operaci, která má být provedena v reakci na poklikejte na soubor.  
  
```
STDMETHOD(put_DocHostDoubleClickFlags)(DWORD dwDocHostDoubleClickFlags);
```  
  
### <a name="parameters"></a>Parametry  
 *dwDocHostDoubleClickFlags*  
 [v] Nová hodnota této vlastnosti.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT` hodnotu.  
  
### <a name="remarks"></a>Poznámky  
 Implementace objektu hostitele ATL používá **DOCHOSTUIDBLCLK_DEFAULT** jako výchozí hodnota této vlastnosti.  
  
##  <a name="put_dochostflags"></a>IAxWinAmbientDispatch::put_DocHostFlags  
 **DocHostFlags** vlastnost určuje možnosti uživatelského rozhraní objektu hostitele.  
  
```
STDMETHOD(put_DocHostFlags)(DWORD dwDocHostFlags);
```  
  
### <a name="parameters"></a>Parametry  
 *dwDocHostFlags*  
 [v] Nová hodnota této vlastnosti.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT` hodnotu.  
  
### <a name="remarks"></a>Poznámky  
 Implementace objektu hostitele ATL používá **DOCHOSTUIFLAG_NO3DBORDER** jako výchozí hodnota této vlastnosti.  
  
##  <a name="put_font"></a>IAxWinAmbientDispatch::put_Font  
 **Písma** vlastnost určuje vedlejším písmo kontejneru.  
  
```
STDMETHOD(put_Font)(IFontDisp* pFont);
```  
  
### <a name="parameters"></a>Parametry  
 `pFont`  
 [v] Nová hodnota této vlastnosti.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT` hodnotu.  
  
### <a name="remarks"></a>Poznámky  
 Implementace objektu ATL hostitele používá výchozí písmo grafického uživatelského rozhraní nebo písmo systému jako výchozí hodnota této vlastnosti.  
  
##  <a name="put_forecolor"></a>IAxWinAmbientDispatch::put_ForeColor  
 `ForeColor` Vlastnost určuje barvu popředí vedlejším kontejneru.  
  
```
STDMETHOD(put_ForeColor)(OLE_COLOR clrForeground);
```  
  
### <a name="parameters"></a>Parametry  
 *clrForeground*  
 [v] Nová hodnota této vlastnosti.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT` hodnotu.  
  
### <a name="remarks"></a>Poznámky  
 Implementace objektu hostitele ATL používá systém okno barvy jako výchozí hodnota této vlastnosti.  
  
##  <a name="put_localeid"></a>IAxWinAmbientDispatch::put_LocaleID  
 **LocaleID** vlastnost určuje ID národního prostředí vedlejším kontejneru.  
  
```
STDMETHOD(put_LocaleID)(LCID lcidLocaleID);
```  
  
### <a name="parameters"></a>Parametry  
 *lcidLocaleID*  
 [v] Nová hodnota této vlastnosti.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT` hodnotu.  
  
### <a name="remarks"></a>Poznámky  
 Implementace objektu hostitele ATL používá výchozí národní prostředí uživatele jako výchozí hodnota této vlastnosti.  
  
##  <a name="put_messagereflect"></a>IAxWinAmbientDispatch::put_MessageReflect  
 **MessageReflect** – vedlejší vlastnost určuje, zda kontejner bude odrážet zprávy do ovládacího prvku hostované.  
  
```
STDMETHOD(put_MessageReflect)(VARIANT_BOOL bMessageReflect);
```  
  
### <a name="parameters"></a>Parametry  
 `bMessageReflect`  
 [v] Nová hodnota této vlastnosti.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT` hodnotu.  
  
### <a name="remarks"></a>Poznámky  
 Implementace objektu hostitele ATL používá `VARIANT_TRUE` jako výchozí hodnota této vlastnosti.  
  
##  <a name="put_optionkeypath"></a>IAxWinAmbientDispatch::put_OptionKeyPath  
 **OptionKeyPath** vlastnost určuje cestu klíče registru nastavení pro uživatele.  
  
```
STDMETHOD(put_OptionKeyPath)(BSTR bstrOptionKeyPath);
```  
  
### <a name="parameters"></a>Parametry  
 *bstrOptionKeyPath*  
 [v] Nová hodnota této vlastnosti.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT` hodnotu.  
  
##  <a name="put_usermode"></a>IAxWinAmbientDispatch::put_UserMode  
 **Přesměrovač** vlastnost určuje režim vedlejším uživatele kontejneru.  
  
```
STDMETHOD(put_UserMode)(VARIANT_BOOL bUserMode);
```  
  
### <a name="parameters"></a>Parametry  
 `bUserMode`  
 [v] Nová hodnota této vlastnosti.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT` hodnotu.  
  
### <a name="remarks"></a>Poznámky  
 Implementace objektu hostitele ATL používá `VARIANT_TRUE` jako výchozí hodnota této vlastnosti.  
  
##  <a name="setambientdispatch"></a>IAxWinAmbientDispatchEx::SetAmbientDispatch  
 Tato metoda je volána doplníte rozhraní – vedlejší vlastnost výchozí uživatelské rozhraní.  
  
```
virtual HRESULT STDMETHODCALLTYPE SetAmbientDispatch(IDispatch* pDispatch) = 0;
```  
  
### <a name="parameters"></a>Parametry  
 *pDispatch*  
 Ukazatel na nové rozhraní.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Když `SetAmbientDispatch` je volána s ukazatel na nové rozhraní, toto nové rozhraní se použije k vyvolání jakékoli vlastnosti nebo metody žádali hostované ovládacím prvkem – Pokud tyto vlastnosti nejsou obsaženy ve [IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md).  
  
##  <a name="attachcontrol"></a>IAxWinHostWindow::AttachControl  
 Připojí ovládacího prvku existující (a dříve inicializovaného) k objektu hostitele pomocí okna identifikovaný `hWnd`.  
  
```
STDMETHOD(AttachControl)(IUnknown* pUnkControl, HWND hWnd);
```  
  
### <a name="parameters"></a>Parametry  
 *pUnkControl*  
 [v] Ukazatel **IUnknown** rozhraní ovládacího prvku být připojen k objektu hostitele.  
  
 `hWnd`  
 [v] Obslužná rutina do okna má být použit pro hostování.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT` hodnotu.  
  
##  <a name="createcontrol"></a>IAxWinHostWindow::CreateControl  
 Vytvoří ovládací prvek, inicializuje ji a hostuje v okně identifikovaný `hWnd`.  
  
```
STDMETHOD(CreateControl)(
    LPCOLESTR lpTricsData,
    HWND hWnd,
    IStream* pStream);
```  
  
### <a name="parameters"></a>Parametry  
 `lpTricsData`  
 [v] Řetězec identifikující k vytvoření ovládacího prvku. Může být CLSID (musí zahrnovat složené závorky), ProgID, adresa URL nebo kód HTML (s předponou podle **MSHTML:**).  
  
 `hWnd`  
 [v] Obslužná rutina do okna má být použit pro hostování.  
  
 `pStream`  
 [v] Ukazatel rozhraní pro datový proud obsahující inicializační data pro ovládací prvek. Může být **NULL**.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT` hodnotu.  
  
### <a name="remarks"></a>Poznámky  
 Toto okno se rozčlenění objektem hostitele vystavení toto rozhraní tak, aby se zprávy můžou odrážet do ovládacího prvku a další funkce kontejneru, budou fungovat.  
  
 Voláním této metody je ekvivalentní volání [IAxWinHostWindow::CreateControlEx](#createcontrolex).  
  
 Vytvořit licencované ovládací prvek ActiveX, najdete v části [IAxWinHostWindowLic::CreateControlLic](#createcontrollicex).  
  
##  <a name="createcontrolex"></a>IAxWinHostWindow::CreateControlEx  
 Vytvoří ovládací prvek ActiveX, inicializuje ji a hostuje v zadané okno podobné [IAxWinHostWindow::CreateControl](#createcontrol).  
  
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
 `lpTricsData`  
 [v] Řetězec identifikující k vytvoření ovládacího prvku. Může být CLSID (musí zahrnovat složené závorky), ProgID, adresa URL nebo kód HTML (s předponou **MSHTML:**).  
  
 `hWnd`  
 [v] Obslužná rutina do okna má být použit pro hostování.  
  
 `pStream`  
 [v] Ukazatel rozhraní pro datový proud obsahující inicializační data pro ovládací prvek. Může být **NULL**.  
  
 `ppUnk`  
 [out] Adresu ukazatele, který se zobrazí **IUnknown** rozhraní vytvořený ovládacího prvku. Může být **NULL**.  
  
 *riidAdvise*  
 [v] Identifikátor rozhraní odchozí rozhraní na obsažený objekt. Může být **IID_NULL**.  
  
 *punkAdvise*  
 [v] Ukazatel **IUnknown** rozhraní podřízený objekt, který má být připojen k bodu připojení na obsažený objekt určeného `iidSink`.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT` hodnotu.  
  
### <a name="remarks"></a>Poznámky  
 Na rozdíl od `CreateControl` metody `CreateControlEx` můžete taky přijímat ukazatele rozhraní do ovládacího prvku nově vytvořený a nastavení jímky událostí pro příjem událostí aktivováno pomocí ovládacího prvku.  
  
 Vytvořit licencované ovládací prvek ActiveX, najdete v části [IAxWinHostWindowLic::CreateControlLicEx](#createcontrollicex).  
  
##  <a name="querycontrol"></a>IAxWinHostWindow::QueryControl  
 Vrátí ukazatel zadaný rozhraní poskytované hostovaného ovládacího prvku.  
  
```
STDMETHOD(QueryControl)(REFIID riid, void** ppvObject);
```  
  
### <a name="parameters"></a>Parametry  
 `riid`  
 [v] ID rozhraní na ovládací prvek požadováno.  
  
 `ppvObject`  
 [out] Adresa ukazatele, která bude přijímat specifikované rozhraní vytvořený ovládacího prvku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT` hodnotu.  
  
##  <a name="setexternaldispatch"></a>IAxWinHostWindow::SetExternalDispatch  
 Nastaví externí dispinterface, která je k dispozici prostřednictvím ovládacím prvkům obsažené [IDocHostUIHandlerDispatch::GetExternal](../../atl/reference/idochostuihandlerdispatch-interface.md) metoda.  
  
```
STDMETHOD(SetExternalDispatch)(IDispatch* pDisp);
```  
  
### <a name="parameters"></a>Parametry  
 `pDisp`  
 [v] Ukazatel na `IDispatch` rozhraní.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT` hodnotu.  
  
##  <a name="setexternaluihandler"></a>IAxWinHostWindow::SetExternalUIHandler  
 Volání této funkce nastavit externí [IDocHostUIHandlerDispatch](../../atl/reference/idochostuihandlerdispatch-interface.md) rozhraní `CAxWindow` objektu.  
  
```
STDMETHOD(SetExternalUIHandler)(IDocHostUIHandlerDispatch* pDisp);
```  
  
### <a name="parameters"></a>Parametry  
 `pDisp`  
 [v] Ukazatel na **IDocHostUIHandlerDispatch** rozhraní.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT` hodnotu.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce používá ovládací prvky (například ovládacího prvku webového prohlížeče), které lokality hostitele pro dotazování `IDocHostUIHandlerDispatch` rozhraní.  
  
##  <a name="createcontrollic"></a>IAxWinHostWindowLic::CreateControlLic  
 Vytvoří licencované ovládací prvek, inicializuje ji a hostuje v okně identifikovaný `hWnd`.  
  
```
STDMETHOD(CreateControlLic)(
    LPCOLESTR lpTricsData,
    HWND hWnd,
    IStream* pStream,
    BSTR bstrLic);
```  
  
### <a name="parameters"></a>Parametry  
 `bstrLic`  
 [v] BSTR, který obsahuje licenční klíč pro ovládací prvek.  
  
### <a name="remarks"></a>Poznámky  
 V tématu [IAxWinHostWindow::CreateControl](#createcontrol) popis zbývající parametry a návratové hodnoty.  
  
 Voláním této metody je ekvivalentní volání [IAxWinHostWindowLic::CreateControlLicEx](#createcontrollicex)  
  
### <a name="example"></a>Příklad  
 V tématu [hostování ActiveX ovládacích prvků pomocí knihovny ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) příklad, který používá `IAxWinHostWindowLic::CreateControlLic`.  
  
##  <a name="createcontrollicex"></a>IAxWinHostWindowLic::CreateControlLicEx  
 Vytvoří licencované ovládací prvek ActiveX, inicializuje ji a hostuje v zadané okno podobné [IAxWinHostWindow::CreateControl](#createcontrol).  
  
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
 `bstrLic`  
 [v] BSTR, který obsahuje licenční klíč pro ovládací prvek.  
  
### <a name="remarks"></a>Poznámky  
 V tématu [IAxWinHostWindow::CreateControlEx](#createcontrolex) popis zbývající parametry a návratové hodnoty.  
  
### <a name="example"></a>Příklad  
 V tématu [hostování ActiveX ovládacích prvků pomocí knihovny ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) příklad, který používá `IAxWinHostWindowLic::CreateControlLicEx`.  
  
## <a name="see-also"></a>Viz také  
 [Přehled třídy](../../atl/atl-class-overview.md)
