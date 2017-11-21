---
title: "Rozhraní IAxWinAmbientDispatch | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IAxWinAmbientDispatch
- No header/ATL::IAxWinAmbientDispatch
- No header/ATL::get_AllowContextMenu
- No header/ATL::get_AllowShowUI
- No header/ATL::get_AllowWindowlessActivation
- No header/ATL::get_BackColor
- No header/ATL::get_DisplayAsDefault
- No header/ATL::get_DocHostDoubleClickFlags
- No header/ATL::get_DocHostFlags
- No header/ATL::get_Font
- No header/ATL::get_ForeColor
- No header/ATL::get_LocaleID
- No header/ATL::get_MessageReflect
- No header/ATL::get_OptionKeyPath
- No header/ATL::get_ShowGrabHandles
- No header/ATL::get_ShowHatching
- No header/ATL::get_UserMode
- No header/ATL::put_AllowContextMenu
- No header/ATL::put_AllowShowUI
- No header/ATL::put_AllowWindowlessActivation
- No header/ATL::put_BackColor
- No header/ATL::put_DisplayAsDefault
- No header/ATL::put_DocHostDoubleClickFlags
- No header/ATL::put_DocHostFlags
- No header/ATL::put_Font
- No header/ATL::put_ForeColor
- No header/ATL::put_LocaleID
- No header/ATL::put_MessageReflect
- No header/ATL::put_OptionKeyPath
- No header/ATL::put_UserMode
dev_langs: C++
helpviewer_keywords: IAxWinAmbientDispatch interface
ms.assetid: 55ba6f7b-7a3c-4792-ae47-c8a84b683ca9
caps.latest.revision: "24"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c4886ff3c3e4a635e390774d21afea407b4d8077
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="iaxwinambientdispatch-interface"></a>IAxWinAmbientDispatch rozhraní
Toto rozhraní poskytuje metody pro zadání vlastnosti hostované řízení nebo kontejneru.  
  
> [!IMPORTANT]
>  Tato třída a její členy nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
interface IAxWinAmbientDispatch : IDispatch
```  
  
## <a name="members"></a>Členové  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[get_AllowContextMenu](#get_allowcontextmenu)|**AllowContextMenu** vlastnost určuje, jestli hostované ovládací prvek může zobrazit svůj vlastní místní nabídce.|  
|[get_AllowShowUI](#get_allowshowui)|**AllowShowUI** vlastnost určuje, jestli hostované ovládací prvek může zobrazit svůj vlastní uživatelské rozhraní.|  
|[get_AllowWindowlessActivation](#get_allowwindowlessactivation)|**AllowWindowlessActivation** vlastnost určuje, zda kontejner umožní aktivace bez oken.|  
|[get_BackColor](#get_backcolor)|`BackColor` Vlastnost určuje barvu pozadí vedlejším kontejneru.|  
|[get_DisplayAsDefault](#get_displayasdefault)|**DisplayAsDefault** je vedlejším vlastnost, která vám umožní kontrolu a zjistěte, zda se jedná o výchozí ovládací prvek.|  
|[get_DocHostDoubleClickFlags](#get_dochostdoubleclickflags)|**DocHostDoubleClickFlags** vlastnost určuje operaci, která má být provedena v reakci na poklikejte na soubor.|  
|[get_DocHostFlags](#get_dochostflags)|**DocHostFlags** vlastnost určuje možnosti uživatelského rozhraní objektu hostitele.|  
|[get_Font](#get_font)|**Písma** vlastnost určuje vedlejším písmo kontejneru.|  
|[get_ForeColor](#get_forecolor)|`ForeColor` Vlastnost určuje barvu popředí vedlejším kontejneru.|  
|[get_LocaleID](#get_localeid)|**LocaleID** vlastnost určuje ID národního prostředí vedlejším kontejneru.|  
|[get_MessageReflect](#get_messagereflect)|**MessageReflect** – vedlejší vlastnost určuje, zda kontejner bude odrážet zprávy do ovládacího prvku hostované.|  
|[get_OptionKeyPath](#get_optionkeypath)|**OptionKeyPath** vlastnost určuje cestu klíče registru nastavení pro uživatele.|  
|[get_ShowGrabHandles](#get_showgrabhandles)|**ShowGrabHandles** – vedlejší vlastnost umožňuje zjistit, pokud ho (RTL) vykreslovat samotné s okamžitými výsledky popisovače ovládacího prvku.|  
|[get_ShowHatching](#get_showhatching)|**ShowHatching** – vedlejší vlastnost umožňuje zjistit, pokud ho měli kreslení samotné zasílána ovládacího prvku.|  
|[get_UserMode](#get_usermode)|**Přesměrovač** vlastnost určuje režim vedlejším uživatele kontejneru.|  
|[put_AllowContextMenu](#put_allowcontextmenu)|**AllowContextMenu** vlastnost určuje, jestli hostované ovládací prvek může zobrazit svůj vlastní místní nabídce.|  
|[put_AllowShowUI](#put_allowshowui)|**AllowShowUI** vlastnost určuje, jestli hostované ovládací prvek může zobrazit svůj vlastní uživatelské rozhraní.|  
|[put_AllowWindowlessActivation](#put_allowwindowlessactivation)|**AllowWindowlessActivation** vlastnost určuje, zda kontejner umožní aktivace bez oken.|  
|[put_BackColor](#put_backcolor)|`BackColor` Vlastnost určuje barvu pozadí vedlejším kontejneru.|  
|[put_DisplayAsDefault](#put_displayasdefault)|**DisplayAsDefault** je vedlejším vlastnost, která vám umožní kontrolu a zjistěte, zda se jedná o výchozí ovládací prvek.|  
|[put_DocHostDoubleClickFlags](#put_dochostdoubleclickflags)|**DocHostDoubleClickFlags** vlastnost určuje operaci, která má být provedena v reakci na poklikejte na soubor.|  
|[put_DocHostFlags](#put_dochostflags)|**DocHostFlags** vlastnost určuje možnosti uživatelského rozhraní objektu hostitele.|  
|[put_Font](#put_font)|**Písma** vlastnost určuje vedlejším písmo kontejneru.|  
|[put_ForeColor](#put_forecolor)|`ForeColor` Vlastnost určuje barvu popředí vedlejším kontejneru.|  
|[put_LocaleID](#put_localeid)|**LocaleID** vlastnost určuje ID národního prostředí vedlejším kontejneru.|  
|[put_MessageReflect](#put_messagereflect)|**MessageReflect** – vedlejší vlastnost určuje, zda kontejner bude odrážet zprávy do ovládacího prvku hostované.|  
|[put_OptionKeyPath](#put_optionkeypath)|**OptionKeyPath** vlastnost určuje cestu klíče registru nastavení pro uživatele.|  
|[put_UserMode](#put_usermode)|**Přesměrovač** vlastnost určuje režim vedlejším uživatele kontejneru.|  
  
## <a name="remarks"></a>Poznámky  
 Toto rozhraní je zveřejněný prostřednictvím ovládacího prvku ActiveX knihovny ATL pro hostování objekty. Volání metody na tomto rozhraní nastavit vlastnosti prostředí, které je k dispozici do ovládacího prvku hostované nebo k zadání dalších aspektů chování kontejneru. Doplníte vlastnosti poskytované `IAxWinAmbientDispatch`, použijte [IAxWinAmbientDispatchEx](../../atl/reference/iaxwinambientdispatchex-interface.md).  
  
 [AXHost](https://msdn.microsoft.com/library/system.windows.forms.axhost.aspx) se pokusí načíst informace o typu o `IAxWinAmbientDispatch` a `IAxWinAmbientDispatchEx` z knihovny typelib, který obsahuje kód.  
  
 Pokud se připojujete k ATL90.dll, **AXHost** načte informace o typu z knihovny typelib v knihovně DLL.  
  
 V tématu [hostování ActiveX ovládacích prvků pomocí knihovny ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) další podrobnosti.  
  
## <a name="requirements"></a>Požadavky  
 Definice toto rozhraní je k dispozici v různých formách, jak je znázorněno v následující tabulce.  
  
|Definice typu|Soubor|  
|---------------------|----------|  
|IDL|atliface.IDL|  
|Knihovny typů|ATL.|  
|C++|atliface.h (také obsaženy v ATLBase.h)|  
  
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
  
## <a name="see-also"></a>Viz také  
 [IAxWinAmbientDispatchEx rozhraní](../../atl/reference/iaxwinambientdispatchex-interface.md)   
 [IAxWinHostWindow rozhraní](../../atl/reference/iaxwinhostwindow-interface.md)   
 [CAxWindow::QueryHost](../../atl/reference/caxwindow-class.md#queryhost)   
 [AtlAxGetHost](composite-control-global-functions.md#atlaxgethost)









