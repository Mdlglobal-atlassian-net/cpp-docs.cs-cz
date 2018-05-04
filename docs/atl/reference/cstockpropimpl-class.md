---
title: Třída CStockPropImpl | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CStockPropImpl
- ATLCTL/ATL::CStockPropImpl
- ATLCTL/ATL::get_Appearance
- ATLCTL/ATL::get_AutoSize
- ATLCTL/ATL::get_BackColor
- ATLCTL/ATL::get_BackStyle
- ATLCTL/ATL::get_BorderColor
- ATLCTL/ATL::get_BorderStyle
- ATLCTL/ATL::get_BorderVisible
- ATLCTL/ATL::get_BorderWidth
- ATLCTL/ATL::get_Caption
- ATLCTL/ATL::get_DrawMode
- ATLCTL/ATL::get_DrawStyle
- ATLCTL/ATL::get_DrawWidth
- ATLCTL/ATL::get_Enabled
- ATLCTL/ATL::get_FillColor
- ATLCTL/ATL::get_FillStyle
- ATLCTL/ATL::get_Font
- ATLCTL/ATL::get_ForeColor
- ATLCTL/ATL::get_HWND
- ATLCTL/ATL::get_MouseIcon
- ATLCTL/ATL::get_MousePointer
- ATLCTL/ATL::get_Picture
- ATLCTL/ATL::get_ReadyState
- ATLCTL/ATL::get_TabStop
- ATLCTL/ATL::get_Text
- ATLCTL/ATL::getvalid
- ATLCTL/ATL::get_Window
- ATLCTL/ATL::put_Appearance
- ATLCTL/ATL::put_AutoSize
- ATLCTL/ATL::put_BackColor
- ATLCTL/ATL::put_BackStyle
- ATLCTL/ATL::put_BorderColor
- ATLCTL/ATL::put_BorderStyle
- ATLCTL/ATL::put_BorderVisible
- ATLCTL/ATL::put_BorderWidth
- ATLCTL/ATL::put_Caption
- ATLCTL/ATL::put_DrawMode
- ATLCTL/ATL::put_DrawStyle
- ATLCTL/ATL::put_DrawWidth
- ATLCTL/ATL::put_Enabled
- ATLCTL/ATL::put_FillColor
- ATLCTL/ATL::put_FillStyle
- ATLCTL/ATL::put_Font
- ATLCTL/ATL::put_ForeColor
- ATLCTL/ATL::put_HWND
- ATLCTL/ATL::put_MouseIcon
- ATLCTL/ATL::put_MousePointer
- ATLCTL/ATL::put_Picture
- ATLCTL/ATL::put_ReadyState
- ATLCTL/ATL::put_TabStop
- ATLCTL/ATL::put_Text
- ATLCTL/ATL::putvalid
- ATLCTL/ATL::put_Window
- ATLCTL/ATL::putref_Font
- ATLCTL/ATL::putref_MouseIcon
- ATLCTL/ATL::putref_Picture
dev_langs:
- C++
helpviewer_keywords:
- CStockPropImpl class
- controls [ATL], stock properties
- stock properties, ATL controls
ms.assetid: 45f11d7d-6580-4a0e-872d-3bc8b836cfda
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f12cff287b9a9c74b548a08d9a03f73869671fc1
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="cstockpropimpl-class"></a>CStockPropImpl – třída
Tato třída poskytuje metody pro podporu uložených vlastností hodnoty.  
  
> [!IMPORTANT]
>  Tato třída a její členy nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class T, class InterfaceName,
    const IID* piid = &_ATL_IIDOF(InterfaceName),
    const GUID* plibid = &CComModule::m_libid,
    WORD wMajor = 1,
    WORD wMinor = 0, class tihclass = CcomTypeInfoHolder>  
class ATL_NO_VTABLE CStockPropImpl : public IDispatchImpl<InterfaceName, piid,
 plibid,
    wMajor,
 wMinor,
    tihclass>
```   
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Třída implementace ovládacího prvku a odvozování z `CStockPropImpl`.  
  
 `InterfaceName`  
 Duální rozhraní vystavení uložených vlastností.  
  
 `piid`  
 Ukazatel na identifikátory IID `InterfaceName`.  
  
 `plibid`  
 Ukazatel na ID KNIHOVNY knihovny typů obsahující definice `InterfaceName`.  
  
 `wMajor`  
 Hlavní verze knihovny typů. Výchozí hodnota je 1.  
  
 `wMinor`  
 Vedlejší verze knihovny typů. Výchozí hodnota je 0.  
  
 `tihclass`  
 Třída, která slouží ke správě informací o typu pro `T`. Výchozí hodnota je `CComTypeInfoHolder`.  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|||  
|-|-|  
|[get_Appearance](#get_appearance)|Volejte tuto metodu za účelem získání Malování styl používaný ovládacího prvku, třeba, ploché nebo 3D.|  
|[get_AutoSize](#get_autosize)|Volejte tuto metodu za účelem získání stavu příznak, který určuje, zda ovládací prvek nemůže být jiné velikost.|  
|[get_BackColor](#get_backcolor)|Volejte tuto metodu za účelem získání barvu pozadí ovládacího prvku.|  
|[get_BackStyle](#get_backstyle)|Volejte tuto metodu za účelem získání průhledného nebo neprůhledného pozadí styl ovládacího prvku.|  
|[get_BorderColor](#get_bordercolor)|Volejte tuto metodu za účelem získání barvu ohraničení ovládacího prvku.|  
|[get_BorderStyle](#get_borderstyle)|Volejte tuto metodu za účelem získání styl ohraničení ovládacího prvku.|  
|[get_BorderVisible](#get_bordervisible)|Volejte tuto metodu za účelem získání stavu příznak označující, zda je viditelná ohraničení ovládacího prvku, či nikoliv.|  
|[get_BorderWidth](#get_borderwidth)|Volejte tuto metodu za účelem získání šířku ohraničení ovládacího prvku (v pixelech).|  
|[get_Caption](#get_caption)|Volejte tuto metodu za účelem získání bude text zadaný v objektu titulku.|  
|[get_DrawMode](#get_drawmode)|Volejte tuto metodu za účelem získání ovládacího prvku režim kreslení, například XOR pera nebo Invertovat barvy.|  
|[get_DrawStyle](#get_drawstyle)|Volejte tuto metodu za účelem získání styl vykreslování ovládacího prvku, například plnou, přerušovanou nebo s tečkou.|  
|[get_DrawWidth](#get_drawwidth)|Volejte tuto metodu za účelem získání šířku (v pixelech) používané metody vykreslování ovládacího prvku.|  
|[get_Enabled](#get_enabled)|Volejte tuto metodu za účelem získání stavu příznak označující, zda je povoleno ovládacího prvku.|  
|[get_FillColor](#get_fillcolor)|Volejte tuto metodu za účelem získání barvu výplně ovládacího prvku.|  
|[get_FillStyle](#get_fillstyle)|Volejte tuto metodu za účelem získání styl výplně ovládacího prvku, například plnou, transparentní nebo mezi zasílána.|  
|[get_Font](#get_font)|Volejte tuto metodu za účelem získání ukazatele na písma vlastností ovládacího prvku.|  
|[get_ForeColor](#get_forecolor)|Volejte tuto metodu za účelem získání barvu popředí ovládacího prvku.|  
|[get_HWND](#get_hwnd)|Voláním této metody lze získat popisovač okna přidruženého k ovládacímu prvku.|  
|[get_MouseIcon](#get_mouseicon)|Voláním této metody lze získat vlastnosti obrázku grafiky (ikona, rastrového obrázku nebo metafile), který se má zobrazit při přesunutí myši na ovládací prvek.|  
|[get_MousePointer](#get_mousepointer)|Voláním této metody lze získat typ ukazatele myši zobrazit při přesunutí myši na ovládací prvek, například šipku, mezi nebo přesýpacích hodin.|  
|[get_Picture](#get_picture)|Volejte tuto metodu za účelem získání ukazatele na vlastnosti obrázku grafiky (ikona, rastrového obrázku nebo metafile), který se má zobrazit.|  
|[get_ReadyState](#get_readystate)|Volejte tuto metodu za účelem získání stavu Připraveno ovládacího prvku, například načítání nebo načíst.|  
|[get_TabStop](#get_tabstop)|Volejte tuto metodu za účelem získání příznak označující, zda je ovládací prvek zarážku či nikoliv.|  
|[get_Text](#get_text)|Volejte tuto metodu za účelem získání text, který se zobrazí pomocí ovládacího prvku.|  
|[getvalid](#get_valid)|Volejte tuto metodu za účelem získání stavu příznak označující, zda je ovládací prvek platný nebo není.|  
|[get_Window](#get_window)|Voláním této metody lze získat popisovač okna přidruženého k ovládacímu prvku. Stejný jako [CStockPropImpl::get_HWND](#get_hwnd).|  
|[put_Appearance](#put_appearance)|Volejte tuto metodu a nastavit Malování styl používaný ovládacího prvku, třeba, ploché nebo 3D.|  
|[put_AutoSize](#put_autosize)|Volejte tuto metodu a nastavit hodnotu příznak, který určuje, zda ovládací prvek nemůže být jiné velikost.|  
|[put_BackColor](#put_backcolor)|Volejte tuto metodu a nastavit barvu pozadí ovládacího prvku.|  
|[put_BackStyle](#put_backstyle)|Volejte tuto metodu a nastavit styl pozadí ovládacího prvku.|  
|[put_BorderColor](#put_bordercolor)|Volejte tuto metodu a nastavit barvu ohraničení ovládacího prvku.|  
|[put_BorderStyle](#put_borderstyle)|Volejte tuto metodu a nastavit styl ohraničení ovládacího prvku.|  
|[put_BorderVisible](#put_bordervisible)|Volejte tuto metodu a nastavit hodnotu příznak označující, zda je viditelná ohraničení ovládacího prvku, či nikoliv.|  
|[put_BorderWidth](#put_borderwidth)|Volejte tuto metodu a nastavit šířku ohraničení ovládacího prvku.|  
|[put_Caption](#put_caption)|Volejte tuto metodu a nastavit text, který se zobrazí pomocí ovládacího prvku.|  
|[put_DrawMode](#put_drawmode)|Volejte tuto metodu a nastavit ovládacího prvku režim kreslení, například XOR pera nebo Invertovat barvy.|  
|[put_DrawStyle](#put_drawstyle)|Volejte tuto metodu a nastavit styl vykreslování ovládacího prvku, například plnou, přerušovanou nebo s tečkou.|  
|[put_DrawWidth](#put_drawwidth)|Volejte tuto metodu a nastavit šířku (v pixelech) používané metody vykreslování ovládacího prvku.|  
|[put_Enabled](#put_enabled)|Volejte tuto metodu a nastavit příznak označující, zda je povoleno ovládacího prvku.|  
|[put_FillColor](#put_fillcolor)|Volejte tuto metodu a nastavit barvu výplně ovládacího prvku.|  
|[put_FillStyle](#put_fillstyle)|Volejte tuto metodu a nastavit styl výplně ovládacího prvku, například plnou, transparentní nebo mezi zasílána.|  
|[put_Font](#put_font)|Volejte tuto metodu a nastavit vlastnosti písem ovládacího prvku.|  
|[put_ForeColor](#put_forecolor)|Volejte tuto metodu a nastavit barvu popředí ovládacího prvku.|  
|[put_HWND](#put_hwnd)|Tato metoda vrátí E_FAIL.|  
|[put_MouseIcon](#put_mouseicon)|Volejte tuto metodu a nastavit vlastnosti obrázku grafiky (ikona, rastrového obrázku nebo metafile), který se má zobrazit při přesunutí myši na ovládací prvek.|  
|[put_MousePointer](#put_mousepointer)|Volejte tuto metodu a nastavit typ ukazatele myši zobrazit při přesunutí myši na ovládací prvek, například šipku, mezi nebo přesýpacích hodin.|  
|[put_Picture](#put_picture)|Volejte tuto metodu a nastavit vlastnosti obrázku grafiky (ikona, rastrového obrázku nebo metafile), který se má zobrazit.|  
|[put_ReadyState](#put_readystate)|Volejte tuto metodu a nastavit ovládacího prvku stavu Připraveno, například načítání nebo načíst.|  
|[put_TabStop](#put_tabstop)|Volejte tuto metodu a nastavit hodnotu příznak označující, zda je ovládací prvek zarážku či nikoliv.|  
|[put_Text](#put_text)|Volejte tuto metodu a nastavit text, který se zobrazí pomocí ovládacího prvku.|  
|[putvalid](#put_valid)|Volejte tuto metodu a nastavit příznak, který určuje, zda je ovládací prvek platná nebo ne.|  
|[put_Window](#put_window)|Tato metoda volá [CStockPropImpl::put_HWND](#put_hwnd), která vrací E_FAIL.|  
|[putref_Font](#putref_font)|Voláním této metody lze nastavit vlastnosti písem ovládacího prvku, s počtem odkaz.|  
|[putref_MouseIcon](#putref_mouseicon)|Volejte tuto metodu a nastavit vlastnosti obrázku grafiky (ikona, rastrového obrázku nebo metafile), který se má zobrazit při přesunutí myši na ovládací prvek s počtem odkaz.|  
|[putref_Picture](#putref_picture)|Volejte tuto metodu a nastavit vlastnosti obrázku grafiky (ikona, rastrového obrázku nebo metafile), který se má zobrazit, s počtem odkaz.|  
  
## <a name="remarks"></a>Poznámky  
 `CStockPropImpl` poskytuje **put** a **získat** metody pro každý uložených vlastností. Tyto metody zadejte kód potřeba nastavit nebo získat data člena spojené s každou vlastnost a upozornění a synchronizovat s kontejneru, když se změní libovolné vlastnosti.  
  
 Visual C++ poskytuje podporu pro uložených vlastností prostřednictvím jeho průvodců. Další informace o přidání uložených vlastností do ovládacího prvku, najdete v článku [ATL – tutoriál](../../atl/active-template-library-atl-tutorial.md).  
  
 Z důvodu zpětné kompatibility `CStockPropImpl` taky zpřístupňuje `get_Window` a `put_Window` metody, které volají jednoduše `get_HWND` a `put_HWND`, v uvedeném pořadí. Výchozí implementaci `put_HWND` vrátí **E_FAIL** od `HWND` by měla být vlastnost určenou jen pro čtení.  
  
 Také mít následující vlastnosti **typu putref** implementace:  
  
-   Písma  
  
-   MouseIcon  
  
-   Obrázek  
  
 Stejné tři uložené vlastnosti vyžadují jejich odpovídající – datový člen bude typu `CComPtr` nebo některé jiné třídě, která obsahuje referenční informace o správné rozhraní počítání prostřednictvím operátor přiřazení.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `T`  
  
 [IDispatchImpl](../../atl/reference/idispatchimpl-class.md)  
  
 `CStockPropImpl`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlctl.h  
  
##  <a name="get_appearance"></a>  CStockPropImpl::get_Appearance  
 Volejte tuto metodu za účelem získání Malování styl používaný ovládacího prvku, třeba, ploché nebo 3D.  
  
```
HRESULT STDMETHODCALLTYPE get_Appearance(SHORT pnAppearance);
```  
  
### <a name="parameters"></a>Parametry  
 *pnAppearance*  
 Proměnná, která přijímá styl Malování ovládacího prvku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
##  <a name="get_autosize"></a>  CStockPropImpl::get_AutoSize  
 Volejte tuto metodu za účelem získání stavu příznak, který určuje, zda ovládací prvek nemůže být jiné velikost.  
  
```
HRESULT STDMETHODCALLTYPE get_Autosize(VARIANT_BOOL* pbAutoSize);
```  
  
### <a name="parameters"></a>Parametry  
 *pbAutoSize*  
 Proměnná, která přijímá příznak stav. Pravda označuje, že ovládací prvek nemůže být jiné velikost.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
##  <a name="get_backcolor"></a>  CStockPropImpl::get_BackColor  
 Volejte tuto metodu za účelem získání barvu pozadí ovládacího prvku.  
  
```
HRESULT STDMETHODCALLTYPE get_BackColor(OLE_COLOR* pclrBackColor);
```  
  
### <a name="parameters"></a>Parametry  
 *pclrBackColor*  
 Proměnná, která přijímá barvu pozadí ovládacího prvku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
##  <a name="get_backstyle"></a>  CStockPropImpl::get_BackStyle  
 Volejte tuto metodu za účelem získání průhledného nebo neprůhledného pozadí styl ovládacího prvku.  
  
```
HRESULT STDMETHODCALLTYPE get_BackStyle(LONG* pnBackStyle);
```  
  
### <a name="parameters"></a>Parametry  
 *pnBackStyle*  
 Proměnná, která přijímá styl pozadí ovládacího prvku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
##  <a name="get_bordercolor"></a>  CStockPropImpl::get_BorderColor  
 Volejte tuto metodu za účelem získání barvu ohraničení ovládacího prvku.  
  
```
HRESULT STDMETHODCALLTYPE get_BorderColor(OLE_COLOR* pclrBorderColor);
```  
  
### <a name="parameters"></a>Parametry  
 *pclrBorderColor*  
 Proměnná, která přijímá barvu ohraničení ovládacího prvku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
##  <a name="get_borderstyle"></a>  CStockPropImpl::get_BorderStyle  
 Volejte tuto metodu za účelem získání styl ohraničení ovládacího prvku.  
  
```
HRESULT STDMETHODCALLTYPE get_BorderStyle(LONG* pnBorderStyle);
```  
  
### <a name="parameters"></a>Parametry  
 *pnBorderStyle*  
 Proměnná, která přijímá styl ohraničení ovládacího prvku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
##  <a name="get_bordervisible"></a>  CStockPropImpl::get_BorderVisible  
 Volejte tuto metodu za účelem získání stavu příznak označující, zda je viditelná ohraničení ovládacího prvku, či nikoliv.  
  
```
HRESULT STDMETHODCALLTYPE get_BorderVisible(VARIANT_BOOL* pbBorderVisible);
```  
  
### <a name="parameters"></a>Parametry  
 *pbBorderVisible*  
 Proměnná, která přijímá příznak stav. Pravda označuje, že ohraničení ovládacího prvku je viditelná.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
##  <a name="get_borderwidth"></a>  CStockPropImpl::get_BorderWidth  
 Volejte tuto metodu za účelem získání šířka ohraničení ovládacího prvku.  
  
```
HRESULT STDMETHODCALLTYPE get_BorderWidth(LONG* pnBorderWidth);
```  
  
### <a name="parameters"></a>Parametry  
 *pnBorderWidth*  
 Proměnná, která přijímá šířka ohraničení ovládacího prvku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
##  <a name="get_caption"></a>  CStockPropImpl::get_Caption  
 Volejte tuto metodu za účelem získání bude text zadaný v objektu titulku.  
  
```
HRESULT STDMETHODCALLTYPE get_Caption(BSTR* pbstrCaption);
```  
  
### <a name="parameters"></a>Parametry  
 *pbstrCaption*  
 Text, který se má zobrazit pomocí ovládacího prvku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
##  <a name="get_drawmode"></a>  CStockPropImpl::get_DrawMode  
 Volejte tuto metodu za účelem získání ovládacího prvku režim kreslení, například XOR pera nebo Invertovat barvy.  
  
```
HRESULT STDMETHODCALLTYPE get_DrawMode(LONG* pnDrawMode);
```  
  
### <a name="parameters"></a>Parametry  
 *pnDrawMode*  
 Proměnná, která přijímá režimu vykreslování ovládacího prvku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
##  <a name="get_drawstyle"></a>  CStockPropImpl::get_DrawStyle  
 Volejte tuto metodu za účelem získání styl vykreslování ovládacího prvku, například plnou, přerušovanou nebo s tečkou.  
  
```
HRESULT STDMETHODCALLTYPE get_DrawStyle(LONG* pnDrawStyle);
```  
  
### <a name="parameters"></a>Parametry  
 *pnDrawStyle*  
 Proměnná, která přijímá styl vykreslování ovládacího prvku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
##  <a name="get_drawwidth"></a>  CStockPropImpl::get_DrawWidth  
 Volejte tuto metodu za účelem získání šířku (v pixelech) používané metody vykreslování ovládacího prvku.  
  
```
HRESULT STDMETHODCALLTYPE get_DrawWidth(LONG* pnDrawWidth);
```  
  
### <a name="parameters"></a>Parametry  
 *pnDrawWidth*  
 Proměnná, která přijímá hodnotu Šířka ovládacího prvku v pixelech.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
##  <a name="get_enabled"></a>  CStockPropImpl::get_Enabled  
 Volejte tuto metodu za účelem získání stavu příznak označující, zda je povoleno ovládacího prvku.  
  
```
HRESULT STDMETHODCALLTYPE get_Enabled(VARIANT_BOOL* pbEnabled);
```  
  
### <a name="parameters"></a>Parametry  
 `pbEnabled`  
 Proměnná, která přijímá příznak stav. Pravda označuje, zda je povoleno ovládacího prvku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
##  <a name="get_fillcolor"></a>  CStockPropImpl::get_FillColor  
 Volejte tuto metodu za účelem získání barvu výplně ovládacího prvku.  
  
```
HRESULT STDMETHODCALLTYPE get_FillColor(OLE_COLOR* pclrFillColor);
```  
  
### <a name="parameters"></a>Parametry  
 *pclrFillColor*  
 Proměnná, která přijímá barvu výplně ovládacího prvku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
##  <a name="get_fillstyle"></a>  CStockPropImpl::get_FillStyle  
 Volejte tuto metodu za účelem získání styl výplně ovládacího prvku, například plnou, transparentní nebo crosshatched.  
  
```
HRESULT STDMETHODCALLTYPE get_FillStyle(LONG* pnFillStyle);
```  
  
### <a name="parameters"></a>Parametry  
 *pnFillStyle*  
 Proměnná, která přijímá styl výplně ovládacího prvku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
##  <a name="get_font"></a>  CStockPropImpl::get_Font  
 Volejte tuto metodu za účelem získání ukazatele na písma vlastností ovládacího prvku.  
  
```
HRESULT STDMETHODCALLTYPE get_Font(IFontDisp** ppFont);
```  
  
### <a name="parameters"></a>Parametry  
 `ppFont`  
 Proměnná, která přijímá ukazatel k vlastnostem písma ovládacího prvku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
##  <a name="get_forecolor"></a>  CStockPropImpl::get_ForeColor  
 Volejte tuto metodu za účelem získání barvu popředí ovládacího prvku.  
  
```
HRESULT STDMETHODCALLTYPE get_ForeColor(OLE_COLOR* pclrForeColor);
```  
  
### <a name="parameters"></a>Parametry  
 *pclrForeColor*  
 Proměnná, která přijímá barvu popředí ovládací prvky.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
##  <a name="get_hwnd"></a>  CStockPropImpl::get_HWND  
 Voláním této metody lze získat popisovač okna přidruženého k ovládacímu prvku.  
  
```
HRESULT STDMETHODCALLTYPE get_HWND(LONG_PTR* phWnd);
```  
  
### <a name="parameters"></a>Parametry  
 `phWnd`  
 Popisovač okna přidruženého k ovládacímu prvku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
##  <a name="get_mouseicon"></a>  CStockPropImpl::get_MouseIcon  
 Voláním této metody lze získat vlastnosti obrázku grafiky (ikona, rastrového obrázku nebo metafile), který se má zobrazit při přesunutí myši na ovládací prvek.  
  
```
HRESULT STDMETHODCALLTYPE get_MouseIcon(IPictureDisp** ppPicture);
```  
  
### <a name="parameters"></a>Parametry  
 `ppPicture`  
 Proměnná, která přijímá ukazatel na obrázek vlastnosti na obrázku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
##  <a name="get_mousepointer"></a>  CStockPropImpl::get_MousePointer  
 Voláním této metody lze získat typ ukazatele myši zobrazit při přesunutí myši na ovládací prvek, například šipku, mezi nebo přesýpacích hodin.  
  
```
HRESULT STDMETHODCALLTYPE get_MousePointer(LONG* pnMousePointer);
```  
  
### <a name="parameters"></a>Parametry  
 *pnMousePointer*  
 Proměnná, která přijímá typ ukazatele myši.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
##  <a name="get_picture"></a>  CStockPropImpl::get_Picture  
 Volejte tuto metodu za účelem získání ukazatele na vlastnosti obrázku grafiky (ikona, rastrového obrázku nebo metafile), který se má zobrazit.  
  
```
HRESULT STDMETHODCALLTYPE get_Picture(IPictureDisp** ppPicture);
```  
  
### <a name="parameters"></a>Parametry  
 `ppPicture`  
 Proměnná, která přijímá ukazatel na vlastnosti na obrázku. V tématu [IPictureDisp](http://msdn.microsoft.com/library/windows/desktop/ms680762) další podrobnosti.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
##  <a name="get_readystate"></a>  CStockPropImpl::get_ReadyState  
 Volejte tuto metodu za účelem získání stavu Připraveno ovládacího prvku, například načítání nebo načíst.  
  
```
HRESULT STDMETHODCALLTYPE get_ReadyState(LONG* pnReadyState);
```  
  
### <a name="parameters"></a>Parametry  
 *pnReadyState*  
 Proměnná, která přijímá stavu Připraveno ovládacího prvku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
##  <a name="get_tabstop"></a>  CStockPropImpl::get_TabStop  
 Volejte tuto metodu za účelem získání stavu příznak označující, zda je ovládací prvek zarážku či nikoliv.  
  
```
HRESULT STDMETHODCALLTYPE get_TabStop(VARIANT_BOOL* pbTabStop);
```  
  
### <a name="parameters"></a>Parametry  
 *pbTabStop*  
 Proměnná, která přijímá příznak stav. Pravda označuje, že ovládací prvek je zarážku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
##  <a name="get_text"></a>  CStockPropImpl::get_Text  
 Volejte tuto metodu za účelem získání text, který se zobrazí pomocí ovládacího prvku.  
  
```
HRESULT STDMETHODCALLTYPE get_Text(BSTR* pbstrText);
```  
  
### <a name="parameters"></a>Parametry  
 *pbstrText*  
 Text, který se zobrazí pomocí ovládacího prvku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
##  <a name="get_valid"></a>  CStockPropImpl::getvalid  
 Volejte tuto metodu za účelem získání stavu příznak označující, zda je ovládací prvek platný nebo není.  
  
```
HRESULT STDMETHODCALLTYPE getvalid(VARIANT_BOOL* pbValid);
```  
  
### <a name="parameters"></a>Parametry  
 *pbValid*  
 Proměnná, která přijímá příznak stav. Pravda označuje, že ovládací prvek je platný.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
##  <a name="get_window"></a>  CStockPropImpl::get_Window  
 Voláním této metody lze získat popisovač okna přidruženého k ovládacímu prvku. Stejný jako [CStockPropImpl::get_HWND](#get_hwnd).  
  
```
HRESULT STDMETHODCALLTYPE get_Window(LONG_PTR* phWnd);
```  
  
### <a name="parameters"></a>Parametry  
 `phWnd`  
 Popisovač okna přidruženého k ovládacímu prvku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
##  <a name="put_appearance"></a>  CStockPropImpl::put_Appearance  
 Volejte tuto metodu a nastavit Malování styl používaný ovládacího prvku, třeba, ploché nebo 3D.  
  
```
HRESULT STDMETHODCALLTYPE put_Appearance(SHORT nAppearance);
```  
  
### <a name="parameters"></a>Parametry  
 `nAppearance`  
 Nový styl Malování má být používána ovládacího prvku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
##  <a name="put_autosize"></a>  CStockPropImpl::put_AutoSize  
 Volejte tuto metodu a nastavit hodnotu příznak, který určuje, zda ovládací prvek nemůže být jiné velikost.  
  
```
HRESULT STDMETHODCALLTYPE put_AutoSize(VARIANT_BOOL bAutoSize,);
```  
  
### <a name="parameters"></a>Parametry  
 *bAutoSize*  
 Hodnota TRUE, pokud ovládací prvek nemůže být jiné velikost.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
##  <a name="put_backcolor"></a>  CStockPropImpl::put_BackColor  
 Volejte tuto metodu a nastavit barvu pozadí ovládacího prvku.  
  
```
HRESULT STDMETHODCALLTYPE put_BackColor(OLE_COLOR clrBackColor);
```  
  
### <a name="parameters"></a>Parametry  
 *clrBackColor*  
 Barva pozadí nový ovládací prvek.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
##  <a name="put_backstyle"></a>  CStockPropImpl::put_BackStyle  
 Volejte tuto metodu a nastavit styl pozadí ovládacího prvku.  
  
```
HRESULT STDMETHODCALLTYPE put_BackStyle(LONG nBackStyle);
```  
  
### <a name="parameters"></a>Parametry  
 *nBackStyle*  
 Nový styl pozadí ovládacího prvku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
##  <a name="put_bordercolor"></a>  CStockPropImpl::put_BorderColor  
 Volejte tuto metodu a nastavit barvu ohraničení ovládacího prvku.  
  
```
HRESULT STDMETHODCALLTYPE put_BorderColor(OLE_COLOR clrBorderColor);
```  
  
### <a name="parameters"></a>Parametry  
 *clrBorderColor*  
 Nové barvu ohraničení. Datový typ OLE_COLOR interně představuje 32bitové dlouhé celé číslo.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
##  <a name="put_borderstyle"></a>  CStockPropImpl::put_BorderStyle  
 Volejte tuto metodu a nastavit styl ohraničení ovládacího prvku.  
  
```
HRESULT STDMETHODCALLTYPE put_BorderStyle(LONG nBorderStyle);
```  
  
### <a name="parameters"></a>Parametry  
 *nBorderStyle*  
 Nový styl ohraničení.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
##  <a name="put_bordervisible"></a>  CStockPropImpl::put_BorderVisible  
 Volejte tuto metodu a nastavit hodnotu příznak označující, zda je viditelná ohraničení ovládacího prvku, či nikoliv.  
  
```
HRESULT STDMETHODCALLTYPE put_BorderVisible(VARIANT_BOOL bBorderVisible);
```  
  
### <a name="parameters"></a>Parametry  
 *bBorderVisible*  
 Hodnota TRUE, pokud není viditelná.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
##  <a name="put_borderwidth"></a>  CStockPropImpl::put_BorderWidth  
 Volejte tuto metodu a nastavit šířku ohraničení ovládacího prvku.  
  
```
HRESULT STDMETHODCALLTYPE put_BorderWidth(LONG nBorderWidth);
```  
  
### <a name="parameters"></a>Parametry  
 `nBorderWidth`  
 Nové šířka ohraničení ovládacího prvku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
##  <a name="put_caption"></a>  CStockPropImpl::put_Caption  
 Volejte tuto metodu a nastavit text, který se zobrazí pomocí ovládacího prvku.  
  
```
HRESULT STDMETHODCALLTYPE put_Caption(BSTR bstrCaption);
```  
  
### <a name="parameters"></a>Parametry  
 *bstrCaption*  
 Text, který se má zobrazit pomocí ovládacího prvku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
##  <a name="put_drawmode"></a>  CStockPropImpl::put_DrawMode  
 Volejte tuto metodu a nastavit ovládacího prvku režim kreslení, například XOR pera nebo Invertovat barvy.  
  
```
HRESULT STDMETHODCALLTYPE put_DrawMode(LONG nDrawMode);
```  
  
### <a name="parameters"></a>Parametry  
 `nDrawMode`  
 Nový režim vykreslování ovládacího prvku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
##  <a name="put_drawstyle"></a>  CStockPropImpl::put_DrawStyle  
 Volejte tuto metodu a nastavit styl vykreslování ovládacího prvku, například plnou, přerušovanou nebo s tečkou.  
  
```
HRESULT STDMETHODCALLTYPE put_DrawStyle(LONG pnDrawStyle);
```  
  
### <a name="parameters"></a>Parametry  
 *nDrawStyle*  
 Nový styl vykreslování ovládacího prvku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
##  <a name="put_drawwidth"></a>  CStockPropImpl::put_DrawWidth  
 Volejte tuto metodu a nastavit šířku (v pixelech) používané metody vykreslování ovládacího prvku.  
  
```
HRESULT STDMETHODCALLTYPE put_DrawWidth(LONG nDrawWidth);
```  
  
### <a name="parameters"></a>Parametry  
 *nDrawWidth*  
 Nové šířku, která má být používána ovládací prvek pro kreslení metody.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
##  <a name="put_enabled"></a>  CStockPropImpl::put_Enabled  
 Volejte tuto metodu a nastavit hodnotu příznak označující, zda je povoleno ovládacího prvku.  
  
```
HRESULT STDMETHODCALLTYPE put_Enabled(VARIANT_BOOL bEnabled);
```  
  
### <a name="parameters"></a>Parametry  
 `bEnabled`  
 Hodnota TRUE, pokud je povoleno ovládacího prvku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
##  <a name="put_fillcolor"></a>  CStockPropImpl::put_FillColor  
 Volejte tuto metodu a nastavit barvu výplně ovládacího prvku.  
  
```
HRESULT STDMETHODCALLTYPE put_FillColor(OLE_COLOR clrFillColor);
```  
  
### <a name="parameters"></a>Parametry  
 *clrFillColor*  
 Nové barvu výplně pro ovládací prvek.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
##  <a name="put_fillstyle"></a>  CStockPropImpl::put_FillStyle  
 Volejte tuto metodu a nastavit styl výplně ovládacího prvku, například plnou, transparentní nebo mezi zasílána.  
  
```
HRESULT STDMETHODCALLTYPE put_FillStyle(LONG nFillStyle);
```  
  
### <a name="parameters"></a>Parametry  
 *nFillStyle*  
 Nový styl výplně pro ovládací prvek.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
##  <a name="put_font"></a>  CStockPropImpl::put_Font  
 Volejte tuto metodu a nastavit vlastnosti písem ovládacího prvku.  
  
```
HRESULT STDMETHODCALLTYPE put_Font(IFontDisp* pFont);
```  
  
### <a name="parameters"></a>Parametry  
 `pFont`  
 Ukazatel na písma vlastností ovládacího prvku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
##  <a name="put_forecolor"></a>  CStockPropImpl::put_ForeColor  
 Volejte tuto metodu a nastavit barvu popředí ovládacího prvku.  
  
```
HRESULT STDMETHODCALLTYPE put_ForeColor(OLE_COLOR clrForeColor);
```  
  
### <a name="parameters"></a>Parametry  
 *clrForeColor*  
 Nové barvu popředí ovládacího prvku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
##  <a name="put_hwnd"></a>  CStockPropImpl::put_HWND  
 Tato metoda vrátí E_FAIL.  
  
```
HRESULT STDMETHODCALLTYPE put_HWND(LONG_PTR /* hWnd */);
```  
  
### <a name="parameters"></a>Parametry  
 */\* hWnd \*/*  
 Vyhrazena.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí E_FAIL.  
  
### <a name="remarks"></a>Poznámky  
 Popisovač okna je hodnota jen pro čtení.  
  
##  <a name="put_mouseicon"></a>  CStockPropImpl::put_MouseIcon  
 Volejte tuto metodu a nastavit vlastnosti obrázku grafiky (ikona, rastrového obrázku nebo metafile), který se má zobrazit při přesunutí myši na ovládací prvek.  
  
```
HRESULT STDMETHODCALLTYPE put_MouseIcon(IPictureDisp* pPicture);
```  
  
### <a name="parameters"></a>Parametry  
 `pPicture`  
 Ukazatel na obrázek vlastnosti na obrázku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
##  <a name="put_mousepointer"></a>  CStockPropImpl::put_MousePointer  
 Volejte tuto metodu a nastavit typ ukazatele myši zobrazit při přesunutí myši na ovládací prvek, například šipku, mezi nebo přesýpacích hodin.  
  
```
HRESULT STDMETHODCALLTYPE put_MousePointer(LONG nMousePointer);
```  
  
### <a name="parameters"></a>Parametry  
 *nMousePointer*  
 Typ ukazatele myši.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
##  <a name="put_picture"></a>  CStockPropImpl::put_Picture  
 Volejte tuto metodu a nastavit vlastnosti obrázku grafiky (ikona, rastrového obrázku nebo metafile), který se má zobrazit.  
  
```
HRESULT STDMETHODCALLTYPE put_Picture(IPictureDisp* pPicture);
```  
  
### <a name="parameters"></a>Parametry  
 `pPicture`  
 Ukazatel na vlastnosti na obrázku. V tématu [IPictureDisp](http://msdn.microsoft.com/library/windows/desktop/ms680762) další podrobnosti.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
##  <a name="put_readystate"></a>  CStockPropImpl::put_ReadyState  
 Volejte tuto metodu a nastavit ovládacího prvku stavu Připraveno, například načítání nebo načíst.  
  
```
HRESULT STDMETHODCALLTYPE put_ReadyState(LONG nReadyState);
```  
  
### <a name="parameters"></a>Parametry  
 *nReadyState*  
 Stavu Připraveno ovládacího prvku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
##  <a name="put_tabstop"></a>  CStockPropImpl::put_TabStop  
 Volejte tuto metodu a nastavit příznak označující, zda je ovládací prvek zarážku či nikoliv.  
  
```
HRESULT STDMETHODCALLTYPE put_TabStop(VARIANT_BOOL bTabStop);
```  
  
### <a name="parameters"></a>Parametry  
 *bTabStop*  
 TRUE, pokud je ovládací prvek zarážku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
##  <a name="put_text"></a>  CStockPropImpl::put_Text  
 Volejte tuto metodu a nastavit text, který se zobrazí pomocí ovládacího prvku.  
  
```
HRESULT STDMETHODCALLTYPE put_Text(BSTR bstrText);
```  
  
### <a name="parameters"></a>Parametry  
 `bstrText`  
 Text, který se zobrazí pomocí ovládacího prvku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
##  <a name="put_valid"></a>  CStockPropImpl::putvalid  
 Volejte tuto metodu a nastavit příznak, který určuje, zda je ovládací prvek platná nebo ne.  
  
```
HRESULT STDMETHODCALLTYPE getvalid(VARIANT_BOOL bValid);
```  
  
### <a name="parameters"></a>Parametry  
 *bValid*  
 Hodnota TRUE, pokud ovládací prvek je platný.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
##  <a name="put_window"></a>  CStockPropImpl::put_Window  
 Tato metoda volá [CStockPropImpl::put_HWND](#put_hwnd), která vrací E_FAIL.  
  
```
HRESULT STDMETHODCALLTYPE put_Window(LONG_PTR hWnd);
```  
  
### <a name="parameters"></a>Parametry  
 `hWnd`  
 Popisovač okna.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí E_FAIL.  
  
### <a name="remarks"></a>Poznámky  
 Popisovač okna je hodnota jen pro čtení.  
  
##  <a name="putref_font"></a>  CStockPropImpl::putref_Font  
 Voláním této metody lze nastavit vlastnosti písem ovládacího prvku, s počtem odkaz.  
  
```
HRESULT STDMETHODCALLTYPE putref_Font(IFontDisp* pFont);
```  
  
### <a name="parameters"></a>Parametry  
 `pFont`  
 Ukazatel na písma vlastností ovládacího prvku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Stejné jako [CStockPropImpl::put_Font](#put_font), ale počet odkazů.  
  
##  <a name="putref_mouseicon"></a>  CStockPropImpl::putref_MouseIcon  
 Volejte tuto metodu a nastavit vlastnosti obrázku grafiky (ikona, rastrového obrázku nebo metafile), který se má zobrazit při přesunutí myši na ovládací prvek s počtem odkaz.  
  
```
HRESULT STDMETHODCALLTYPE putref_MouseIcon(IPictureDisp* pPicture);
```  
  
### <a name="parameters"></a>Parametry  
 `pPicture`  
 Ukazatel na obrázek vlastnosti na obrázku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Stejné jako [CStockPropImpl::put_MouseIcon](#put_mouseicon), ale počet odkazů.  
  
##  <a name="putref_picture"></a>  CStockPropImpl::putref_Picture  
 Volejte tuto metodu a nastavit vlastnosti obrázku grafiky (ikona, rastrového obrázku nebo metafile), který se má zobrazit, s počtem odkaz.  
  
```
HRESULT STDMETHODCALLTYPE putref_Picture(IPictureDisp* pPicture);
```  
  
### <a name="parameters"></a>Parametry  
 `pPicture`  
 Ukazatel na vlastnosti na obrázku. V tématu [IPictureDisp](http://msdn.microsoft.com/library/windows/desktop/ms680762) další podrobnosti.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Stejné jako [CStockPropImpl::put_Picture](#put_picture), ale počet odkazů.  
  
## <a name="see-also"></a>Viz také  
 [Přehled třídy](../../atl/atl-class-overview.md)   
 [IDispatchImpl – třída](../../atl/reference/idispatchimpl-class.md)
