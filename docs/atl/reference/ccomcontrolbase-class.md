---
title: "Třída CComControlBase | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComControlBase
- ATLCTL/ATL::CComControlBase
- ATLCTL/ATL::CComControlBase::AppearanceType
- ATLCTL/ATL::CComControlBase::CComControlBase
- ATLCTL/ATL::CComControlBase::ControlQueryInterface
- ATLCTL/ATL::CComControlBase::DoesVerbActivate
- ATLCTL/ATL::CComControlBase::DoesVerbUIActivate
- ATLCTL/ATL::CComControlBase::DoVerbProperties
- ATLCTL/ATL::CComControlBase::FireViewChange
- ATLCTL/ATL::CComControlBase::GetAmbientAppearance
- ATLCTL/ATL::CComControlBase::GetAmbientAutoClip
- ATLCTL/ATL::CComControlBase::GetAmbientBackColor
- ATLCTL/ATL::CComControlBase::GetAmbientCharSet
- ATLCTL/ATL::CComControlBase::GetAmbientCodePage
- ATLCTL/ATL::CComControlBase::GetAmbientDisplayAsDefault
- ATLCTL/ATL::CComControlBase::GetAmbientDisplayName
- ATLCTL/ATL::CComControlBase::GetAmbientFont
- ATLCTL/ATL::CComControlBase::GetAmbientFontDisp
- ATLCTL/ATL::CComControlBase::GetAmbientForeColor
- ATLCTL/ATL::CComControlBase::GetAmbientLocaleID
- ATLCTL/ATL::CComControlBase::GetAmbientMessageReflect
- ATLCTL/ATL::CComControlBase::GetAmbientPalette
- ATLCTL/ATL::CComControlBase::GetAmbientProperty
- ATLCTL/ATL::CComControlBase::GetAmbientRightToLeft
- ATLCTL/ATL::CComControlBase::GetAmbientScaleUnits
- ATLCTL/ATL::CComControlBase::GetAmbientShowGrabHandles
- ATLCTL/ATL::CComControlBase::GetAmbientShowHatching
- ATLCTL/ATL::CComControlBase::GetAmbientSupportsMnemonics
- ATLCTL/ATL::CComControlBase::GetAmbientTextAlign
- ATLCTL/ATL::CComControlBase::GetAmbientTopToBottom
- ATLCTL/ATL::CComControlBase::GetAmbientUIDead
- ATLCTL/ATL::CComControlBase::GetAmbientUserMode
- ATLCTL/ATL::CComControlBase::GetDirty
- ATLCTL/ATL::CComControlBase::GetZoomInfo
- ATLCTL/ATL::CComControlBase::InPlaceActivate
- ATLCTL/ATL::CComControlBase::InternalGetSite
- ATLCTL/ATL::CComControlBase::OnDraw
- ATLCTL/ATL::CComControlBase::OnDrawAdvanced
- ATLCTL/ATL::CComControlBase::OnKillFocus
- ATLCTL/ATL::CComControlBase::OnMouseActivate
- ATLCTL/ATL::CComControlBase::OnPaint
- ATLCTL/ATL::CComControlBase::OnSetFocus
- ATLCTL/ATL::CComControlBase::PreTranslateAccelerator
- ATLCTL/ATL::CComControlBase::SendOnClose
- ATLCTL/ATL::CComControlBase::SendOnDataChange
- ATLCTL/ATL::CComControlBase::SendOnRename
- ATLCTL/ATL::CComControlBase::SendOnSave
- ATLCTL/ATL::CComControlBase::SendOnViewChange
- ATLCTL/ATL::CComControlBase::SetControlFocus
- ATLCTL/ATL::CComControlBase::SetDirty
- ATLCTL/ATL::CComControlBase::m_bAutoSize
- ATLCTL/ATL::CComControlBase::m_bDrawFromNatural
- ATLCTL/ATL::CComControlBase::m_bDrawGetDataInHimetric
- ATLCTL/ATL::CComControlBase::m_bInPlaceActive
- ATLCTL/ATL::CComControlBase::m_bInPlaceSiteEx
- ATLCTL/ATL::CComControlBase::m_bNegotiatedWnd
- ATLCTL/ATL::CComControlBase::m_bRecomposeOnResize
- ATLCTL/ATL::CComControlBase::m_bRequiresSave
- ATLCTL/ATL::CComControlBase::m_bResizeNatural
- ATLCTL/ATL::CComControlBase::m_bUIActive
- ATLCTL/ATL::CComControlBase::m_bUsingWindowRgn
- ATLCTL/ATL::CComControlBase::m_bWasOnceWindowless
- ATLCTL/ATL::CComControlBase::m_bWindowOnly
- ATLCTL/ATL::CComControlBase::m_bWndLess
- ATLCTL/ATL::CComControlBase::m_hWndCD
- ATLCTL/ATL::CComControlBase::m_nFreezeEvents
- ATLCTL/ATL::CComControlBase::m_rcPos
- ATLCTL/ATL::CComControlBase::m_sizeExtent
- ATLCTL/ATL::CComControlBase::m_sizeNatural
- ATLCTL/ATL::CComControlBase::m_spAdviseSink
- ATLCTL/ATL::CComControlBase::m_spAmbientDispatch
- ATLCTL/ATL::CComControlBase::m_spClientSite
- ATLCTL/ATL::CComControlBase::m_spDataAdviseHolder
- ATLCTL/ATL::CComControlBase::m_spInPlaceSite
- ATLCTL/ATL::CComControlBase::m_spOleAdviseHolder
dev_langs:
- C++
helpviewer_keywords:
- CComControlBase class
ms.assetid: 3d1bf022-acf2-4092-8283-ff8cee6332f3
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d6109bfaf29ee26053bc1dcbb5af8f56a0612215
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="ccomcontrolbase-class"></a>CComControlBase – třída
Tato třída poskytuje metody pro vytváření a správu ATL ovládací prvky.  
  
> [!IMPORTANT]
>  Tato třída a její členy nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class ATL_NO_VTABLE CComControlBase
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-typedefs"></a>Veřejné – definice TypeDef  
  
|Název|Popis|  
|----------|-----------------|  
|[CComControlBase::AppearanceType](#appearancetype)|Přepsat, pokud vaše `m_nAppearance` uložených vlastností není typu `short`.|  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CComControlBase::CComControlBase](#ccomcontrolbase)|Konstruktor|  
|[CComControlBase:: ~ CComControlBase](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CComControlBase::ControlQueryInterface](#controlqueryinterface)|Načte ukazatel na požadované rozhraní.|  
|[CComControlBase::DoesVerbActivate](#doesverbactivate)|Kontroluje, zda `iVerb` parametr používá `IOleObjectImpl::DoVerb` buď aktivuje uživatelské rozhraní ovládacího prvku ( `iVerb` rovná `OLEIVERB_UIACTIVATE`), definuje akce při poklepání ovládacího prvku ( `iVerb` rovná `OLEIVERB_PRIMARY`), zobrazí ovládací prvek ( `iVerb` rovná `OLEIVERB_SHOW`), nebo aktivuje ovládacího prvku ( `iVerb` rovná **OLEIVERB_INPLACEACTIVATE**).|  
|[CComControlBase::DoesVerbUIActivate](#doesverbuiactivate)|Kontroluje, zda `iVerb` parametr používá `IOleObjectImpl::DoVerb` způsobí, že uživatelské rozhraní ovládacího prvku k aktivaci a vrátí **TRUE**.|  
|[CComControlBase::DoVerbProperties](#doverbproperties)|Zobrazí stránky vlastností ovládacího prvku.|  
|[CComControlBase::FireViewChange](#fireviewchange)|Volat tuto metodu říct kontejner, aby ho překreslit ovládací prvek nebo odeslání oznámení jímky registrované doporučení, které došlo ke změně zobrazení ovládacího prvku.|  
|[CComControlBase::GetAmbientAppearance](#getambientappearance)|Načte **DISPID_AMBIENT_APPEARANCE**, aktuální vzhled nastavení pro ovládací prvek: 0 pro dvojrozměrném a 1 pro 3D.|  
|[CComControlBase::GetAmbientAutoClip](#getambientautoclip)|Načte **DISPID_AMBIENT_AUTOCLIP**, příznak označující, zda kontejner podporuje automatické výstřižek oblasti zobrazení ovládacího prvku.|  
|[CComControlBase::GetAmbientBackColor](#getambientbackcolor)|Načte **DISPID_AMBIENT_BACKCOLOR**, barvu pozadí vedlejším pro všechny ovládací prvky definované kontejneru.|  
|[CComControlBase::GetAmbientCharSet](#getambientcharset)|Načte **DISPID_AMBIENT_CHARSET**, vedlejším znaková sada pro všechny ovládací prvky definované kontejneru.|  
|[CComControlBase::GetAmbientCodePage](#getambientcodepage)|Načte **DISPID_AMBIENT_CODEPAGE**, vedlejším znaková sada pro všechny ovládací prvky definované kontejneru.|  
|[CComControlBase::GetAmbientDisplayAsDefault](#getambientdisplayasdefault)|Načte **DISPID_AMBIENT_DISPLAYASDEFAULT**, příznak, který je **TRUE** Pokud kontejneru označila ovládacího prvku v této lokalitě jako výchozího tlačítka, a proto ovládacího prvku tlačítko (RTL) vykreslovat s silnější rámce.|  
|[CComControlBase::GetAmbientDisplayName](#getambientdisplayname)|Načte **DISPID_AMBIENT_DISPLAYNAME**, název kontejneru dodal do ovládacího prvku.|  
|[CComControlBase::GetAmbientFont](#getambientfont)|Načte ukazatel do kontejneru je vedlejším `IFont` rozhraní.|  
|[CComControlBase::GetAmbientFontDisp](#getambientfontdisp)|Načte ukazatel do kontejneru je vedlejším **IFontDisp** odesílání rozhraní.|  
|[CComControlBase::GetAmbientForeColor](#getambientforecolor)|Načte **DISPID_AMBIENT_FORECOLOR**, barvu popředí vedlejším pro všechny ovládací prvky definované kontejneru.|  
|[CComControlBase::GetAmbientLocaleID](#getambientlocaleid)|Načte **DISPID_AMBIENT_LOCALEID**, identifikátor jazyka, který používá kontejneru.|  
|[CComControlBase::GetAmbientMessageReflect](#getambientmessagereflect)|Načte **DISPID_AMBIENT_MESSAGEREFLECT**, příznak označující, zda kontejner chce dostávat zprávy oken (například `WM_DRAWITEM`) jako události.|  
|[CComControlBase::GetAmbientPalette](#getambientpalette)|Načte **DISPID_AMBIENT_PALETTE**používané pro přístup k kontejneru `HPALETTE`.|  
|[CComControlBase::GetAmbientProperty](#getambientproperty)|Načte vlastnost kontejneru určeného `id`.|  
|[CComControlBase::GetAmbientRightToLeft](#getambientrighttoleft)|Načte **DISPID_AMBIENT_RIGHTTOLEFT**, směr, ve kterém se zobrazí obsah pomocí kontejneru.|  
|[CComControlBase::GetAmbientScaleUnits](#getambientscaleunits)|Načte **DISPID_AMBIENT_SCALEUNITS**, kontejneru vedlejším jednotky (například palce nebo cm) pro popisování zobrazí.|  
|[CComControlBase::GetAmbientShowGrabHandles](#getambientshowgrabhandles)|Načte **DISPID_AMBIENT_SHOWGRABHANDLES**, příznak označující, zda kontejner umožňuje ovládací prvek zobrazí okamžitými výsledky obslužné rutiny pro sebe sama při aktivní.|  
|[CComControlBase::GetAmbientShowHatching](#getambientshowhatching)|Načte **DISPID_AMBIENT_SHOWHATCHING**, příznak označující, zda kontejner umožňuje zobrazení samotného pomocí šrafované vzoru, když je aktivní uživatelské rozhraní ovládacího prvku.|  
|[CComControlBase::GetAmbientSupportsMnemonics](#getambientsupportsmnemonics)|Načte **DISPID_AMBIENT_SUPPORTSMNEMONICS**, příznak označující, zda kontejner podporuje klávesové zkratky klávesnice.|  
|[CComControlBase::GetAmbientTextAlign](#getambienttextalign)|Načte **DISPID_AMBIENT_TEXTALIGN**, zarovnání textu preferované kontejnerem: 0 pro obecné zarovnání (vlevo text pravé straně čísla), 1 pro zarovnání vlevo, 2 pro zarovnání na střed a 3 pro zarovnání doprava.|  
|[CComControlBase::GetAmbientTopToBottom](#getambienttoptobottom)|Načte **DISPID_AMBIENT_TOPTOBOTTOM**, směr, ve kterém se zobrazí obsah pomocí kontejneru.|  
|[CComControlBase::GetAmbientUIDead](#getambientuidead)|Načte **DISPID_AMBIENT_UIDEAD**, příznak označující, zda chce kontejneru ovládacího prvku reagovat na akce uživatelského rozhraní.|  
|[CComControlBase::GetAmbientUserMode](#getambientusermode)|Načte **DISPID_AMBIENT_USERMODE**, příznak určující, zda kontejner je v režimu spuštění ( **TRUE**) nebo v režimu návrhu ( **FALSE**).|  
|[CComControlBase::GetDirty](#getdirty)|Vrátí hodnotu – datový člen `m_bRequiresSave`.|  
|[CComControlBase::GetZoomInfo](#getzoominfo)|Načte x a y hodnoty čítači a jmenovatel na faktor zvětšování pro ovládací prvek aktivovaný pro místní úpravy.|  
|[CComControlBase::InPlaceActivate](#inplaceactivate)|Způsobí, že ovládací prvek pro přechod z neaktivní stav ať stavu příkaz v `iVerb` označuje.|  
|[CComControlBase::InternalGetSite](#internalgetsite)|Volejte tuto metodu za účelem dotaz řízení lokality pro ukazatel na zjištěné rozhraní.|  
|[CComControlBase::OnDraw](#ondraw)|Potlačí tuto metodu k vykreslení ovládacího prvku.|  
|[CComControlBase::OnDrawAdvanced](#ondrawadvanced)|Výchozí hodnota **OnDrawAdvanced** připraví kontextu normalizovaný zařízení pro vykreslování a potom volá třída ovládacích prvků `OnDraw` metoda.|  
|[CComControlBase::OnKillFocus](#onkillfocus)|Kontroluje, zda ovládací prvek je aktivní na místě a má platný řízení lokality, a kontejneru informuje, že ovládací prvek ztratil fokus.|  
|[CComControlBase::OnMouseActivate](#onmouseactivate)|Kontroluje, zda je v uživatelském režimu uživatelského rozhraní, a aktivuje ovládacího prvku.|  
|[CComControlBase::OnPaint](#onpaint)|Připraví kontejneru pro malování, získá ovládacího prvku klientské oblasti a pak zavolá třídu ovládacího prvku `OnDraw` metoda.|  
|[CComControlBase::OnSetFocus](#onsetfocus)|Kontroluje, zda ovládací prvek je aktivní na místě a má platný řízení lokality, a informuje kontejneru ovládacího prvku si získávají fokus.|  
|[CComControlBase::PreTranslateAccelerator](#pretranslateaccelerator)|Potlačí tuto metodu poskytnout vlastní klávesnice akcelerátoru obslužné rutiny.|  
|[CComControlBase::SendOnClose](#sendonclose)|Oznámí všechny poradní jímky zaregistrována držitele doporučení, že byla uzavřena ovládacího prvku.|  
|[CComControlBase::SendOnDataChange](#sendondatachange)|Oznámí všechny poradní jímky zaregistrována držitele doporučení, které se změnily data ovládacího prvku.|  
|[CComControlBase::SendOnRename](#sendonrename)|Oznámí všechny poradní jímky zaregistrována držitele doporučení, že ovládací prvek má nové přezdívka.|  
|[CComControlBase::SendOnSave](#sendonsave)|Oznámí všechny poradní jímky zaregistrována držitele doporučení, která byla uložena ovládacího prvku.|  
|[CComControlBase::SendOnViewChange](#sendonviewchange)|Upozorní, že všechny registrované poradní jímky, které došlo ke změně zobrazení ovládacího prvku.|  
|[CComControlBase::SetControlFocus](#setcontrolfocus)|Nastaví nebo odebere fokus klávesnice do nebo z ovládacího prvku.|  
|[CComControlBase::SetDirty](#setdirty)|Nastaví datový člen `m_bRequiresSave` na hodnotu v `bDirty`.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CComControlBase::m_bAutoSize](#m_bautosize)|Příznak, což značí, že ovládací prvek nemůže být jiné velikost.|  
|[CComControlBase::m_bDrawFromNatural](#m_bdrawfromnatural)|Příznak označující, že `IDataObjectImpl::GetData` a `CComControlBase::GetZoomInfo` měli nastavit velikost ovládacího prvku z `m_sizeNatural` spíše než z `m_sizeExtent`.|  
|[CComControlBase::m_bDrawGetDataInHimetric](#m_bdrawgetdatainhimetric)|Příznak označující, že `IDataObjectImpl::GetData` měli použít HIMETRIC jednotky a ne pixelů při kreslení.|  
|[CComControlBase::m_bInPlaceActive](#m_binplaceactive)|Příznak, což značí, že je na místě aktivní ovládací prvek.|  
|[CComControlBase::m_bInPlaceSiteEx](#m_binplacesiteex)|Příznak indikující podporuje kontejneru **IOleInPlaceSiteEx** rozhraní a OCX96 řízení funkcí, jako je například bez oken a bez blikání ovládací prvky.|  
|[CComControlBase::m_bNegotiatedWnd](#m_bnegotiatedwnd)|Příznak indikující, zda má ovládací prvek vyjedná se kontejneru o podporu pro funkce řízení OCX96 (například blikání a bez oken ovládací prvky) a zda je ovládací prvek oddílové nebo bez oken.|  
|[CComControlBase::m_bRecomposeOnResize](#m_brecomposeonresize)|Příznak, což značí, že chce znovu zalomit jeho prezentace, když se změní velikost zobrazení ovládacího prvku kontejneru ovládacího prvku.|  
|[CComControlBase::m_bRequiresSave](#m_brequiressave)|Příznak, což značí, že ovládací prvek se změnil od posledního uložení.|  
|[CComControlBase::m_bResizeNatural](#m_bresizenatural)|Příznak, který udává ovládacího prvku chce změnit velikost jeho přirozené rozsah (jeho bez měřítka fyzické velikost) až kontejneru změní velikost zobrazení ovládacího prvku.|  
|[CComControlBase::m_bUIActive](#m_buiactive)|Příznak, který udává ovládacího prvku uživatelského rozhraní, jako je například nabídek a panelů nástrojů, je aktivní.|  
|[CComControlBase::m_bUsingWindowRgn](#m_busingwindowrgn)|Příznak, což značí, že používá oblasti zadaný kontejner okno ovládacího prvku.|  
|[CComControlBase::m_bWasOnceWindowless](#m_bwasoncewindowless)|Příznak označující ovládací prvek byl bez oken, ale může nebo nemusí být nyní bez oken.|  
|[CComControlBase::m_bWindowOnly](#m_bwindowonly)|Příznak, což značí, že by měla být i v případě, že kontejner podporuje bez oken řízení oddílové, ovládacího prvku.|  
|[CComControlBase::m_bWndLess](#m_bwndless)|Příznak, což značí, že je ovládací prvek bez oken.|  
|[CComControlBase::m_hWndCD](#m_hwndcd)|Obsahuje odkaz na popisovač okna přidruženého k ovládacímu prvku.|  
|[CComControlBase::m_nFreezeEvents](#m_nfreezeevents)|Počet kolikrát kontejneru má pozastaveny události (odmítl akceptovat události) bez použité rozmrazení událostí (přijetí událostí).|  
|[CComControlBase::m_rcPos](#m_rcpos)|Umístění ovládacího prvku, vyjádřené v souřadnicích kontejneru v pixelech.|  
|[CComControlBase::m_sizeExtent](#m_sizeextent)|Rozsah ovládacího prvku HIMETRIC jednotky (jednotlivých jednotek je 0,01 milimetry) pro konkrétní zobrazení.|  
|[CComControlBase::m_sizeNatural](#m_sizenatural)|Fyzické velikosti ovládacího prvku HIMETRIC jednotky (jednotlivých jednotek je 0,01 milimetrech).|  
|[CComControlBase::m_spAdviseSink](#m_spadvisesink)|Přímé ukazatel na poradní připojení na kontejneru (kontejneru [IAdviseSink](http://msdn.microsoft.com/library/windows/desktop/ms692513)).|  
|[CComControlBase::m_spAmbientDispatch](#m_spambientdispatch)|A `CComDispatchDriver` objekt, který vám umožní načíst a nastavit vlastnosti kontejneru prostřednictvím `IDispatch` ukazatel.|  
|[CComControlBase::m_spClientSite](#m_spclientsite)|Ukazatel na lokality klienta ovládacího prvku v kontejneru.|  
|[CComControlBase::m_spDataAdviseHolder](#m_spdataadviseholder)|Poskytuje standardní prostředky k uložení poradní připojení mezi datové objekty a poradit jímky.|  
|[CComControlBase::m_spInPlaceSite](#m_spinplacesite)|Ukazatel na kontejneru [IOleInPlaceSite](http://msdn.microsoft.com/library/windows/desktop/ms686586), [IOleInPlaceSiteEx](http://msdn.microsoft.com/library/windows/desktop/ms693461), nebo [IOleInPlaceSiteWindowless](http://msdn.microsoft.com/library/windows/desktop/ms682300) ukazatel rozhraní.|  
|[CComControlBase::m_spOleAdviseHolder](#m_spoleadviseholder)|Poskytuje standardní implementace způsob, jak uložení poradní připojení.|  
  
## <a name="remarks"></a>Poznámky  
 Tato třída poskytuje metody pro vytváření a správu ATL ovládací prvky. [Třída CComControl](../../atl/reference/ccomcontrol-class.md) je odvozena z `CComControlBase`. Když vytvoříte standardního ovládacího prvku nebo DHTML ovládacího prvku s použitím Průvodce ovládacím prvkem ATL, průvodce automaticky odvodí třídě z `CComControlBase`.  
  
 Další informace o vytvoření ovládacího prvku, najdete v článku [ATL – tutoriál](../../atl/active-template-library-atl-tutorial.md). Další informace o Průvodci projektu knihovny ATL, najdete v článku [vytváření projektu knihovny ATL](../../atl/reference/creating-an-atl-project.md).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlctl.h  
  
##  <a name="appearancetype"></a>CComControlBase::AppearanceType  
 Přepsat, pokud vaše **m_nAppearance** uložených vlastností není typu **krátké**.  
  
```
typedef short AppearanceType;
```  
  
### <a name="remarks"></a>Poznámky  
 Průvodce ovládacím prvkem ATL přidá **m_nAppearance** stock vlastnost typu krátké. Přepsání `AppearanceType` Pokud použijete na jiný datový typ.  
  
##  <a name="ccomcontrolbase"></a>CComControlBase::CComControlBase  
 Konstruktor  
  
```
CComControlBase(HWND& h);
```  
  
### <a name="parameters"></a>Parametry  
 `h`  
 Popisovač okna přidruženého k ovládacímu prvku.  
  
### <a name="remarks"></a>Poznámky  
 Inicializuje na ovládací prvek velikost jednotky HIMETRIC 5080 X 5080 (2 "X 2") a inicializuje `CComControlBase` – datový člen hodnoty k **NULL** nebo **FALSE**.  
  
##  <a name="dtor"></a>CComControlBase:: ~ CComControlBase  
 Destruktor.  
  
```
~CComControlBase();
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud je ovládací prvek oddílové, `~CComControlBase` zničí voláním [destroywindow –](http://msdn.microsoft.com/library/windows/desktop/ms632682).  
  
##  <a name="controlqueryinterface"></a>CComControlBase::ControlQueryInterface  
 Načte ukazatel na požadované rozhraní.  
  
```
virtual HRESULT ControlQueryInterface(const IID& iid,
    void** ppv);
```  
  
### <a name="parameters"></a>Parametry  
 `iid`  
 Identifikátor GUID se požadované rozhraní.  
  
 `ppv`  
 Ukazatel na ukazatel rozhraní identifikovaný `iid`, nebo **NULL** Pokud rozhraní nebyl nalezen.  
  
### <a name="remarks"></a>Poznámky  
 Zpracovává jenom rozhraní v tabulce COM mapy.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_COM#15](../../atl/codesnippet/cpp/ccomcontrolbase-class_1.cpp)]  
  
##  <a name="doesverbactivate"></a>CComControlBase::DoesVerbActivate  
 Kontroluje, zda `iVerb` parametr používá `IOleObjectImpl::DoVerb` buď aktivuje uživatelské rozhraní ovládacího prvku ( `iVerb` rovná `OLEIVERB_UIACTIVATE`), definuje akce při poklepání ovládacího prvku ( `iVerb` rovná `OLEIVERB_PRIMARY`), zobrazí ovládací prvek ( `iVerb` rovná `OLEIVERB_SHOW`), nebo aktivuje ovládacího prvku ( `iVerb` rovná **OLEIVERB_INPLACEACTIVATE**).  
  
```
BOOL DoesVerbActivate(LONG iVerb);
```  
  
### <a name="parameters"></a>Parametry  
 `iVerb`  
 Hodnotu, která určuje akci provedenou `DoVerb`.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí **TRUE** Pokud `iVerb` rovná `OLEIVERB_UIACTIVATE`, `OLEIVERB_PRIMARY`, `OLEIVERB_SHOW`, nebo **OLEIVERB_INPLACEACTIVATE**, jinak vrátí **FALSE**.  
  
### <a name="remarks"></a>Poznámky  
 Mohou přepsat tuto metodu můžete definovat vlastní příkaz aktivace.  
  
##  <a name="doesverbuiactivate"></a>CComControlBase::DoesVerbUIActivate  
 Kontroluje, zda `iVerb` parametr používá `IOleObjectImpl::DoVerb` způsobí, že uživatelské rozhraní ovládacího prvku k aktivaci a vrátí **TRUE**.  
  
```
BOOL DoesVerbUIActivate(LONG iVerb);
```  
  
### <a name="parameters"></a>Parametry  
 `iVerb`  
 Hodnotu, která určuje akci provedenou `DoVerb`.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí **TRUE** Pokud `iVerb` rovná `OLEIVERB_UIACTIVATE`, `OLEIVERB_PRIMARY`, `OLEIVERB_SHOW`, nebo **OLEIVERB_INPLACEACTIVATE**. Jinak, vrátí metoda **FALSE**.  
  
##  <a name="doverbproperties"></a>CComControlBase::DoVerbProperties  
 Zobrazí stránky vlastností ovládacího prvku.  
  
```
HRESULT DoVerbProperties(LPCRECT /* prcPosRect */, HWND hwndParent);
```  
  
### <a name="parameters"></a>Parametry  
 `prcPosRec`  
 Vyhrazena.  
  
 *hwndParent*  
 Popisovač okna obsahující ovládacího prvku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Jeden standardní hodnoty HRESULT.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_COM#19](../../atl/codesnippet/cpp/ccomcontrolbase-class_2.cpp)]  
  
 [!code-cpp[NVC_ATL_COM#20](../../atl/codesnippet/cpp/ccomcontrolbase-class_3.h)]  
  
##  <a name="fireviewchange"></a>CComControlBase::FireViewChange  
 Volat tuto metodu říct kontejner, aby ho překreslit ovládací prvek nebo odeslání oznámení jímky registrované doporučení, které došlo ke změně zobrazení ovládacího prvku.  
  
```
HRESULT FireViewChange();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Jeden standardní hodnoty HRESULT.  
  
### <a name="remarks"></a>Poznámky  
 Pokud je aktivní ovládací prvek (datový člen třídy ovládacího prvku [CComControlBase::m_bInPlaceActive](#m_binplaceactive) je **TRUE**), upozorní kontejneru, chcete ho překreslit celý ovládací prvek. Pokud ovládací prvek je neaktivní, upozorní ovládací prvek je registrován poradit jímky (prostřednictvím datový člen třídy ovládacího prvku [CComControlBase::m_spAdviseSink](#m_spadvisesink)), došlo ke změně zobrazení ovládacího prvku.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_COM#21](../../atl/codesnippet/cpp/ccomcontrolbase-class_4.cpp)]  
  
##  <a name="getambientappearance"></a>CComControlBase::GetAmbientAppearance  
 Načte **DISPID_AMBIENT_APPEARANCE**, aktuální vzhled nastavení pro ovládací prvek: 0 pro dvojrozměrném a 1 pro 3D.  
  
```
HRESULT GetAmbientAppearance(short& nAppearance);
```  
  
### <a name="parameters"></a>Parametry  
 `nAppearance`  
 Vlastnost **DISPID_AMBIENT_APPEARANCE**.  
  
### <a name="return-value"></a>Návratová hodnota  
 Jeden standardní hodnoty HRESULT.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_COM#22](../../atl/codesnippet/cpp/ccomcontrolbase-class_5.h)]  
  
##  <a name="getambientautoclip"></a>CComControlBase::GetAmbientAutoClip  
 Načte **DISPID_AMBIENT_AUTOCLIP**, příznak označující, zda kontejner podporuje automatické výstřižek oblasti zobrazení ovládacího prvku.  
  
```
HRESULT GetAmbientAutoClip(BOOL& bAutoClip);
```  
  
### <a name="parameters"></a>Parametry  
 *bAutoClip*  
 Vlastnost **DISPID_AMBIENT_AUTOCLIP**.  
  
### <a name="return-value"></a>Návratová hodnota  
 Jeden standardní hodnoty HRESULT.  
  
##  <a name="getambientbackcolor"></a>CComControlBase::GetAmbientBackColor  
 Načte **DISPID_AMBIENT_BACKCOLOR**, barvu pozadí vedlejším pro všechny ovládací prvky definované kontejneru.  
  
```
HRESULT GetAmbientBackColor(OLE_COLOR& BackColor);
```  
  
### <a name="parameters"></a>Parametry  
 *Barva pozadí*  
 Vlastnost **DISPID_AMBIENT_BACKCOLOR**.  
  
### <a name="return-value"></a>Návratová hodnota  
 Jeden standardní hodnoty HRESULT.  
  
##  <a name="getambientcharset"></a>CComControlBase::GetAmbientCharSet  
 Načte **DISPID_AMBIENT_CHARSET**, vedlejším znaková sada pro všechny ovládací prvky definované kontejneru.  
  
```
HRESULT GetAmbientCharSet(BSTR& bstrCharSet);
```  
  
### <a name="parameters"></a>Parametry  
 *bstrCharSet*  
 Vlastnost **DISPID_AMBIENT_CHARSET**.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
##  <a name="getambientcodepage"></a>CComControlBase::GetAmbientCodePage  
 Načte **DISPID_AMBIENT_CODEPAGE**, vedlejším kódové stránky pro všechny ovládací prvky definované kontejneru.  
  
```
HRESULT GetAmbientCodePage(ULONG& ulCodePage);
```  
  
### <a name="parameters"></a>Parametry  
 *ulCodePage*  
 Vlastnost **DISPID_AMBIENT_CODEPAGE**.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
##  <a name="getambientdisplayasdefault"></a>CComControlBase::GetAmbientDisplayAsDefault  
 Načte **DISPID_AMBIENT_DISPLAYASDEFAULT**, příznak, který je **TRUE** Pokud kontejneru označila ovládacího prvku v této lokalitě jako výchozího tlačítka, a proto ovládacího prvku tlačítko (RTL) vykreslovat s silnější rámce.  
  
```
HRESULT GetAmbientDisplayAsDefault(BOOL& bDisplayAsDefault);
```  
  
### <a name="parameters"></a>Parametry  
 `bDisplayAsDefault`  
 Vlastnost **DISPID_AMBIENT_DISPLAYASDEFAULT**.  
  
### <a name="return-value"></a>Návratová hodnota  
 Jeden standardní hodnoty HRESULT.  
  
##  <a name="getambientdisplayname"></a>CComControlBase::GetAmbientDisplayName  
 Načte **DISPID_AMBIENT_DISPLAYNAME**, název kontejneru dodal do ovládacího prvku.  
  
```
HRESULT GetAmbientDisplayName(BSTR& bstrDisplayName);
```  
  
### <a name="parameters"></a>Parametry  
 *bstrDisplayName*  
 Vlastnost **DISPID_AMBIENT_DISPLAYNAME**.  
  
### <a name="return-value"></a>Návratová hodnota  
 Jeden standardní hodnoty HRESULT.  
  
##  <a name="getambientfont"></a>CComControlBase::GetAmbientFont  
 Načte ukazatel do kontejneru je vedlejším `IFont` rozhraní.  
  
```
HRESULT GetAmbientFont(IFont** ppFont);
```  
  
### <a name="parameters"></a>Parametry  
 `ppFont`  
 Ukazatel na kontejneru je vedlejším [IFont](http://msdn.microsoft.com/library/windows/desktop/ms680673) rozhraní.  
  
### <a name="return-value"></a>Návratová hodnota  
 Jeden standardní hodnoty HRESULT.  
  
### <a name="remarks"></a>Poznámky  
 Pokud je vlastnost **NULL**, je ukazatel **NULL**. Pokud je ukazatel není **NULL**, volající musí uvolnit ukazatele.  
  
##  <a name="getambientfontdisp"></a>CComControlBase::GetAmbientFontDisp  
 Načte ukazatel do kontejneru je vedlejším **IFontDisp** odesílání rozhraní.  
  
```
HRESULT GetAmbientFontDisp(IFontDisp** ppFont);
```  
  
### <a name="parameters"></a>Parametry  
 `ppFont`  
 Ukazatel na kontejneru je vedlejším [IFontDisp](http://msdn.microsoft.com/library/windows/desktop/ms692695) odesílání rozhraní.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Pokud je vlastnost **NULL**, je ukazatel **NULL**. Pokud je ukazatel není **NULL**, volající musí uvolnit ukazatele.  
  
##  <a name="getambientforecolor"></a>CComControlBase::GetAmbientForeColor  
 Načte **DISPID_AMBIENT_FORECOLOR**, barvu popředí vedlejším pro všechny ovládací prvky definované kontejneru.  
  
```
HRESULT GetAmbientForeColor(OLE_COLOR& ForeColor);
```  
  
### <a name="parameters"></a>Parametry  
 *ForeColor*  
 Vlastnost **DISPID_AMBIENT_FORECOLOR**.  
  
### <a name="return-value"></a>Návratová hodnota  
 Jeden standardní hodnoty HRESULT.  
  
##  <a name="getambientlocaleid"></a>CComControlBase::GetAmbientLocaleID  
 Načte **DISPID_AMBIENT_LOCALEID**, identifikátor jazyka, který používá kontejneru.  
  
```
HRESULT GetAmbientLocaleID(LCID& lcid);
```  
  
### <a name="parameters"></a>Parametry  
 `lcid`  
 Vlastnost **DISPID_AMBIENT_LOCALEID**.  
  
### <a name="return-value"></a>Návratová hodnota  
 Jeden standardní hodnoty HRESULT.  
  
### <a name="remarks"></a>Poznámky  
 Ovládací prvek můžete použít tento identifikátor přizpůsobit jeho uživatelské rozhraní pro různé jazyky.  
  
##  <a name="getambientmessagereflect"></a>CComControlBase::GetAmbientMessageReflect  
 Načte **DISPID_AMBIENT_MESSAGEREFLECT**, příznak označující, zda kontejner chce dostávat zprávy oken (například `WM_DRAWITEM`) jako události.  
  
```
HRESULT GetAmbientMessageReflect(BOOL& bMessageReflect);
```  
  
### <a name="parameters"></a>Parametry  
 `bMessageReflect`  
 Vlastnost **DISPID_AMBIENT_MESSAGEREFLECT**.  
  
### <a name="return-value"></a>Návratová hodnota  
 Jeden standardní hodnoty HRESULT.  
  
##  <a name="getambientpalette"></a>CComControlBase::GetAmbientPalette  
 Načte **DISPID_AMBIENT_PALETTE**používané pro přístup k kontejneru `HPALETTE`.  
  
```
HRESULT GetAmbientPalette(HPALETTE& hPalette);
```  
  
### <a name="parameters"></a>Parametry  
 `hPalette`  
 Vlastnost **DISPID_AMBIENT_PALETTE**.  
  
### <a name="return-value"></a>Návratová hodnota  
 Jeden standardní hodnoty HRESULT.  
  
##  <a name="getambientproperty"></a>CComControlBase::GetAmbientProperty  
 Načte vlastnost kontejneru určeného `dispid`.  
  
```
HRESULT GetAmbientProperty(DISPID dispid, VARIANT& var);
```  
  
### <a name="parameters"></a>Parametry  
 `dispid`  
 Identifikátor vlastnosti kontejneru mají být načteny.  
  
 `var`  
 Proměnná pro příjem vlastnost.  
  
### <a name="return-value"></a>Návratová hodnota  
 Jeden standardní hodnoty HRESULT.  
  
### <a name="remarks"></a>Poznámky  
 ATL poskytl sadu pomocných funkcí se načíst konkrétní vlastnosti, například [CComControlBase::GetAmbientBackColor](#getambientbackcolor). Pokud je k dispozici žádná vhodná metoda, použijte `GetAmbientProperty`.  
  
##  <a name="getambientrighttoleft"></a>CComControlBase::GetAmbientRightToLeft  
 Načte **DISPID_AMBIENT_RIGHTTOLEFT**, směr, ve kterém se zobrazí obsah pomocí kontejneru.  
  
```
HRESULT GetAmbientRightToLeft(BOOL& bRightToLeft);
```  
  
### <a name="parameters"></a>Parametry  
 *bRightToLeft*  
 Vlastnost **DISPID_AMBIENT_RIGHTTOLEFT**. Nastavte na **TRUE** Pokud zprava doleva, se zobrazí obsah **FALSE** Pokud se zobrazí vlevo vpravo.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
##  <a name="getambientscaleunits"></a>CComControlBase::GetAmbientScaleUnits  
 Načte **DISPID_AMBIENT_SCALEUNITS**, kontejneru vedlejším jednotky (například palce nebo cm) pro popisování zobrazí.  
  
```
HRESULT GetAmbientScaleUnits(BSTR& bstrScaleUnits);
```  
  
### <a name="parameters"></a>Parametry  
 *bstrScaleUnits*  
 Vlastnost **DISPID_AMBIENT_SCALEUNITS**.  
  
### <a name="return-value"></a>Návratová hodnota  
 Jeden standardní hodnoty HRESULT.  
  
##  <a name="getambientshowgrabhandles"></a>CComControlBase::GetAmbientShowGrabHandles  
 Načte **DISPID_AMBIENT_SHOWGRABHANDLES**, příznak označující, zda kontejner umožňuje ovládací prvek zobrazí okamžitými výsledky obslužné rutiny pro sebe sama při aktivní.  
  
```
HRESULT GetAmbientShowGrabHandles(BOOL& bShowGrabHandles);
```  
  
### <a name="parameters"></a>Parametry  
 *bShowGrabHandles*  
 Vlastnost **DISPID_AMBIENT_SHOWGRABHANDLES**.  
  
### <a name="return-value"></a>Návratová hodnota  
 Jeden standardní hodnoty HRESULT.  
  
##  <a name="getambientshowhatching"></a>CComControlBase::GetAmbientShowHatching  
 Načte **DISPID_AMBIENT_SHOWHATCHING**, příznak označující, zda umožňuje kontejneru ovládacího prvku zobrazení samotného pomocí šrafované vzoru, když je aktivní uživatelské rozhraní ovládacího prvku.  
  
```
HRESULT GetAmbientShowHatching(BOOL& bShowHatching);
```  
  
### <a name="parameters"></a>Parametry  
 *bShowHatching*  
 Vlastnost **DISPID_AMBIENT_SHOWHATCHING**.  
  
### <a name="return-value"></a>Návratová hodnota  
 Jeden standardní hodnoty HRESULT.  
  
##  <a name="getambientsupportsmnemonics"></a>CComControlBase::GetAmbientSupportsMnemonics  
 Načte **DISPID_AMBIENT_SUPPORTSMNEMONICS**, příznak označující, zda kontejner podporuje klávesové zkratky klávesnice.  
  
```
HRESULT GetAmbientSupportsMnemonics(BOOL& bSupportsMnemonics);
```  
  
### <a name="parameters"></a>Parametry  
 *bSupportsMnemonics*  
 Vlastnost **DISPID_AMBIENT_SUPPORTSMNEMONICS**.  
  
### <a name="return-value"></a>Návratová hodnota  
 Jeden standardní hodnoty HRESULT.  
  
##  <a name="getambienttextalign"></a>CComControlBase::GetAmbientTextAlign  
 Načte **DISPID_AMBIENT_TEXTALIGN**, zarovnání textu preferované kontejnerem: 0 pro obecné zarovnání (vlevo text pravé straně čísla), 1 pro zarovnání vlevo, 2 pro zarovnání na střed a 3 pro zarovnání doprava.  
  
```
HRESULT GetAmbientTextAlign(short& nTextAlign);
```  
  
### <a name="parameters"></a>Parametry  
 *nTextAlign*  
 Vlastnost **DISPID_AMBIENT_TEXTALIGN**.  
  
### <a name="return-value"></a>Návratová hodnota  
 Jeden standardní hodnoty HRESULT.  
  
##  <a name="getambienttoptobottom"></a>CComControlBase::GetAmbientTopToBottom  
 Načte **DISPID_AMBIENT_TOPTOBOTTOM**, směr, ve kterém se zobrazí obsah pomocí kontejneru.  
  
```
HRESULT GetAmbientTopToBottom(BOOL& bTopToBottom);
```  
  
### <a name="parameters"></a>Parametry  
 *bTopToBottom*  
 Vlastnost **DISPID_AMBIENT_TOPTOBOTTOM**. Nastavte na **TRUE** při zobrazení textu shora dolů, **FALSE** Pokud se zobrazí zdola nahoru.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
##  <a name="getambientuidead"></a>CComControlBase::GetAmbientUIDead  
 Načte **DISPID_AMBIENT_UIDEAD**, příznak označující, zda chce kontejneru ovládacího prvku reagovat na akce uživatelského rozhraní.  
  
```
HRESULT GetAmbientUIDead(BOOL& bUIDead);
```  
  
### <a name="parameters"></a>Parametry  
 *bUIDead*  
 Vlastnost **DISPID_AMBIENT_UIDEAD**.  
  
### <a name="return-value"></a>Návratová hodnota  
 Jeden standardní hodnoty HRESULT.  
  
### <a name="remarks"></a>Poznámky  
 Pokud **TRUE**, by neměly odpovídat ovládacího prvku. Tento příznak platí bez ohledu na to **DISPID_AMBIENT_USERMODE** příznak. V tématu [CComControlBase::GetAmbientUserMode](#getambientusermode).  
  
##  <a name="getambientusermode"></a>CComControlBase::GetAmbientUserMode  
 Načte **DISPID_AMBIENT_USERMODE**, příznak určující, zda kontejner je v režimu spuštění ( **TRUE**) nebo v režimu návrhu ( **FALSE**).  
  
```
HRESULT GetAmbientUserMode(BOOL& bUserMode);
```  
  
### <a name="parameters"></a>Parametry  
 `bUserMode`  
 Vlastnost **DISPID_AMBIENT_USERMODE**.  
  
### <a name="return-value"></a>Návratová hodnota  
 Jeden standardní hodnoty HRESULT.  
  
##  <a name="getdirty"></a>CComControlBase::GetDirty  
 Vrátí hodnotu – datový člen `m_bRequiresSave`.  
  
```
BOOL GetDirty();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu – datový člen [m_bRequiresSave](#m_brequiressave).  
  
### <a name="remarks"></a>Poznámky  
 Tato hodnota se nastavuje pomocí [CComControlBase::SetDirty](#setdirty).  
  
##  <a name="getzoominfo"></a>CComControlBase::GetZoomInfo  
 Načte x a y hodnoty čítači a jmenovatel na faktor zvětšování pro ovládací prvek aktivovaný pro místní úpravy.  
  
```
void GetZoomInfo(ATL_DRAWINFO& di);
```  
  
### <a name="parameters"></a>Parametry  
 `di`  
 Struktura, která bude obsahovat čítači a jmenovatel na faktor zvětšování. Další informace najdete v tématu [ATL_DRAWINFO](../../atl/reference/atl-drawinfo-structure.md).  
  
### <a name="remarks"></a>Poznámky  
 Na faktor zvětšování je poměr přirozené velikosti ovládacího prvku na aktuální velikost.  
  
##  <a name="inplaceactivate"></a>CComControlBase::InPlaceActivate  
 Způsobí, že ovládací prvek pro přechod z neaktivní stav ať stavu příkaz v `iVerb` označuje.  
  
```
HRESULT InPlaceActivate(LONG iVerb, const RECT* prcPosRect = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `iVerb`  
 Hodnotu, která určuje akci provedenou [IOleObjectImpl::DoVerb](../../atl/reference/ioleobjectimpl-class.md#doverb).  
  
 *prcPosRect*  
 Ukazatel na pozici ovládacího prvku na místě.  
  
### <a name="return-value"></a>Návratová hodnota  
 Jeden standardní hodnoty HRESULT.  
  
### <a name="remarks"></a>Poznámky  
 Před aktivací tato metoda ověří ovládacího prvku má lokalitu klienta, zkontroluje, kolik ovládacího prvku je viditelná a získá umístění ovládacího prvku v okně nadřazené. Po aktivaci ovládacího prvku, tato metoda aktivuje uživatelské rozhraní ovládacího prvku a informuje kontejneru zpřístupněte ovládacího prvku.  
  
 Tato metoda také načte `IOleInPlaceSite`, **IOleInPlaceSiteEx**, nebo **IOleInPlaceSiteWindowless** ukazatel rozhraní pro ovládací prvek a ukládá je – datový člen třídy ovládacího prvku [CComControlBase::m_spInPlaceSite](#m_spinplacesite). Datové členy třídy ovládacího prvku [CComControlBase::m_bInPlaceSiteEx](#m_binplacesiteex), [CComControlBase::m_bWndLess](#m_bwndless), [CComControlBase::m_bWasOnceWindowless](#m_bwasoncewindowless)a [ CComControlBase::m_bNegotiatedWnd](#m_bnegotiatedwnd) jsou nastaveny na hodnotu true, podle potřeby.  
  
##  <a name="internalgetsite"></a>CComControlBase::InternalGetSite  
 Volejte tuto metodu za účelem dotaz řízení lokality pro ukazatel na zjištěné rozhraní.  
  
```
HRESULT InternalGetSite(REFIID riid, void** ppUnkSite);
```  
  
### <a name="parameters"></a>Parametry  
 `riid`  
 Identifikátory IID ukazatel rozhraní, která má být vrácen v `ppUnkSite`.  
  
 `ppUnkSite`  
 Adresa proměnné ukazatele, která přijímá ukazatel rozhraní požadované v `riid`.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Pokud lokalita podporuje rozhraní požadované v `riid`, ukazatele je vrácený pomocí zprávy `ppUnkSite`. V opačném `ppUnkSite` je nastaven na hodnotu NULL.  
  
##  <a name="m_bautosize"></a>CComControlBase::m_bAutoSize  
 Příznak, což značí, že ovládací prvek nemůže být jiné velikost.  
  
```
unsigned m_bAutoSize:1;
```  
  
### <a name="remarks"></a>Poznámky  
 Tento příznak se ověří pomocí `IOleObjectImpl::SetExtent` a pokud **TRUE**, způsobí, že funkce vrátí **E_FAIL**.  
  
> [!NOTE]
>  Pokud chcete použít tento člen dat v rámci třídy ovládacího prvku, je potřeba deklarovat jako člena dat ve třídě ovládacího. Třídě ovládacího nebude dědění tento člen data ze základní třídy, protože je deklarované v rámci spojení v základní třídě.  
  
 Pokud přidáte **Automatická velikost** možnost [uložené vlastnosti](../../atl/reference/stock-properties-atl-control-wizard.md) kartě Průvodce ovládacím prvkem ATL, průvodce automaticky vytvoří tento člen data ve třídě ovládacího, vytvoří put a získat metody pro vlastnost a podporuje [IPropertyNotifySink](http://msdn.microsoft.com/library/windows/desktop/ms692638) automatické zaslání oznámení kontejneru při změně vlastnosti.  
  
##  <a name="m_bdrawfromnatural"></a>CComControlBase::m_bDrawFromNatural  
 Příznak označující, že `IDataObjectImpl::GetData` a `CComControlBase::GetZoomInfo` měli nastavit velikost ovládacího prvku z `m_sizeNatural` spíše než z `m_sizeExtent`.  
  
```
unsigned m_bDrawFromNatural:1;
```  
  
### <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Pokud chcete použít tento člen dat v rámci třídy ovládacího prvku, je potřeba deklarovat jako člena dat ve třídě ovládacího. Třídě ovládacího nebude dědění tento člen data ze základní třídy, protože je deklarované v rámci spojení v základní třídě.  
  
##  <a name="m_bdrawgetdatainhimetric"></a>CComControlBase::m_bDrawGetDataInHimetric  
 Příznak označující, že `IDataObjectImpl::GetData` měli použít HIMETRIC jednotky a ne pixelů při kreslení.  
  
```
unsigned m_bDrawGetDataInHimetric:1;
```  
  
### <a name="remarks"></a>Poznámky  
 Jednotlivé logické jednotky HIMETRIC je 0,01 milimetru.  
  
> [!NOTE]
>  Pokud chcete použít tento člen dat v rámci třídy ovládacího prvku, je potřeba deklarovat jako člena dat ve třídě ovládacího. Třídě ovládacího nebude dědění tento člen data ze základní třídy, protože je deklarované v rámci spojení v základní třídě.  
  
##  <a name="m_binplaceactive"></a>CComControlBase::m_bInPlaceActive  
 Příznak, což značí, že je na místě aktivní ovládací prvek.  
  
```
unsigned m_bInPlaceActive:1;
```  
  
### <a name="remarks"></a>Poznámky  
 To znamená, že je ovládací prvek viditelný a její okno, pokud existuje, je viditelná, ale jeho nabídek a panelů nástrojů nemusí být aktivní. `m_bUIActive` Příznak označuje ovládacího prvku uživatelského rozhraní, jako jsou nabídky, je také aktivní.  
  
> [!NOTE]
>  Pokud chcete použít tento člen dat v rámci třídy ovládacího prvku, je potřeba deklarovat jako člena dat ve třídě ovládacího. Třídě ovládacího nebude dědění tento člen data ze základní třídy, protože je deklarované v rámci spojení v základní třídě.  
  
##  <a name="m_binplacesiteex"></a>CComControlBase::m_bInPlaceSiteEx  
 Příznak indikující podporuje kontejneru **IOleInPlaceSiteEx** rozhraní a OCX96 řízení funkcí, jako je například bez oken a bez blikání ovládací prvky.  
  
```
unsigned m_bInPlaceSiteEx:1;
```  
  
### <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Pokud chcete použít tento člen dat v rámci třídy ovládacího prvku, je potřeba deklarovat jako člena dat ve třídě ovládacího. Třídě ovládacího nebude dědění tento člen data ze základní třídy, protože je deklarované v rámci spojení v základní třídě.  
  
 Datový člen `m_spInPlaceSite` odkazuje na [IOleInPlaceSite](http://msdn.microsoft.com/library/windows/desktop/ms686586), [IOleInPlaceSiteEx](http://msdn.microsoft.com/library/windows/desktop/ms693461), nebo [IOleInPlaceSiteWindowless](http://msdn.microsoft.com/library/windows/desktop/ms682300) rozhraní, v závislosti na hodnotě `m_bWndLess` a `m_bInPlaceSiteEx` příznaky. (Datový člen `m_bNegotiatedWnd` musí být **TRUE** pro `m_spInPlaceSite` ukazatel platná.)  
  
 Pokud `m_bWndLess` je **FALSE** a `m_bInPlaceSiteEx` je **TRUE**, `m_spInPlaceSite` je **IOleInPlaceSiteEx** ukazatel rozhraní. V tématu [m_spInPlaceSite](#m_spinplacesite) pro tabulka zobrazující vztah mezi tyto tři datových členů.  
  
##  <a name="m_bnegotiatedwnd"></a>CComControlBase::m_bNegotiatedWnd  
 Příznak indikující, zda má ovládací prvek vyjedná se kontejneru o podporu pro funkce řízení OCX96 (například blikání a bez oken ovládací prvky) a zda je ovládací prvek oddílové nebo bez oken.  
  
```
unsigned m_bNegotiatedWnd:1;
```  
  
### <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Pokud chcete použít tento člen dat v rámci třídy ovládacího prvku, je potřeba deklarovat jako člena dat ve třídě ovládacího. Třídě ovládacího nebude dědění tento člen data ze základní třídy, protože je deklarované v rámci spojení v základní třídě.  
  
 `m_bNegotiatedWnd` Musí být příznak **TRUE** pro `m_spInPlaceSite` ukazatel platná.  
  
##  <a name="m_brecomposeonresize"></a>CComControlBase::m_bRecomposeOnResize  
 Příznak, což značí, že chce znovu zalomit jeho prezentace, když se změní velikost zobrazení ovládacího prvku kontejneru ovládacího prvku.  
  
```
unsigned m_bRecomposeOnResize:1;
```  
  
### <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Pokud chcete použít tento člen dat v rámci třídy ovládacího prvku, je potřeba deklarovat jako člena dat ve třídě ovládacího. Třídě ovládacího nebude dědění tento člen data ze základní třídy, protože je deklarované v rámci spojení v základní třídě.  
  
 Tento příznak se ověří pomocí [IOleObjectImpl::SetExtent](../../atl/reference/ioleobjectimpl-class.md#setextent) a pokud **TRUE**, `SetExtent` upozorní kontejneru zobrazení změn. Pokud je nastavený tento příznak, **OLEMISC_RECOMPOSEONRESIZE** bit ve [OLEMISC](http://msdn.microsoft.com/library/windows/desktop/ms678497) výčet musí být také nastavená.  
  
##  <a name="m_brequiressave"></a>CComControlBase::m_bRequiresSave  
 Příznak, což značí, že ovládací prvek se změnil od posledního uložení.  
  
```
unsigned m_bRequiresSave:1;
```  
  
### <a name="remarks"></a>Poznámky  
 Hodnota `m_bRequiresSave` lze nastavit s [CComControlBase::SetDirty](#setdirty) a načtené s [CComControlBase::GetDirty](#getdirty).  
  
> [!NOTE]
>  Pokud chcete použít tento člen dat v rámci třídy ovládacího prvku, je potřeba deklarovat jako člena dat ve třídě ovládacího. Třídě ovládacího nebude dědění tento člen data ze základní třídy, protože je deklarované v rámci spojení v základní třídě.  
  
##  <a name="m_bresizenatural"></a>CComControlBase::m_bResizeNatural  
 Příznak, který udává ovládacího prvku chce změnit velikost jeho přirozené rozsah (jeho bez měřítka fyzické velikost) až kontejneru změní velikost zobrazení ovládacího prvku.  
  
```
unsigned m_bResizeNatural:1;
```  
  
### <a name="remarks"></a>Poznámky  
 Tento příznak se ověří pomocí `IOleObjectImpl::SetExtent` a pokud **TRUE**, velikost předaný do `SetExtent` je přiřazena k `m_sizeNatural`.  
  
 Velikost předaný do `SetExtent` se vždycky přiřazuje `m_sizeExtent`, bez ohledu na to hodnota `m_bResizeNatural`.  
  
> [!NOTE]
>  Pokud chcete použít tento člen dat v rámci třídy ovládacího prvku, je potřeba deklarovat jako člena dat ve třídě ovládacího. Třídě ovládacího nebude dědění tento člen data ze základní třídy, protože je deklarované v rámci spojení v základní třídě.  
  
##  <a name="m_buiactive"></a>CComControlBase::m_bUIActive  
 Příznak, který udává ovládacího prvku uživatelského rozhraní, jako je například nabídek a panelů nástrojů, je aktivní.  
  
```
unsigned m_bUIActive:1;
```  
  
### <a name="remarks"></a>Poznámky  
 `m_bInPlaceActive` Příznak označuje, že je ovládací prvek aktivní, ale ne, svoje uživatelské rozhraní je aktivní.  
  
> [!NOTE]
>  Pokud chcete použít tento člen dat v rámci třídy ovládacího prvku, je potřeba deklarovat jako člena dat ve třídě ovládacího. Třídě ovládacího nebude dědění tento člen data ze základní třídy, protože je deklarované v rámci spojení v základní třídě.  
  
##  <a name="m_busingwindowrgn"></a>CComControlBase::m_bUsingWindowRgn  
 Příznak, což značí, že používá oblasti zadaný kontejner okno ovládacího prvku.  
  
```
unsigned m_bUsingWindowRgn:1;
```  
  
### <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Pokud chcete použít tento člen dat v rámci třídy ovládacího prvku, je potřeba deklarovat jako člena dat ve třídě ovládacího. Třídě ovládacího nebude dědění tento člen data ze základní třídy, protože je deklarované v rámci spojení v základní třídě.  
  
##  <a name="m_bwasoncewindowless"></a>CComControlBase::m_bWasOnceWindowless  
 Příznak označující ovládací prvek byl bez oken, ale může nebo nemusí být nyní bez oken.  
  
```
unsigned m_bWasOnceWindowless:1;
```  
  
### <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Pokud chcete použít tento člen dat v rámci třídy ovládacího prvku, je potřeba deklarovat jako člena dat ve třídě ovládacího. Třídě ovládacího nebude dědění tento člen data ze základní třídy, protože je deklarované v rámci spojení v základní třídě.  
  
##  <a name="m_bwindowonly"></a>CComControlBase::m_bWindowOnly  
 Příznak, což značí, že by měla být i v případě, že kontejner podporuje bez oken řízení oddílové, ovládacího prvku.  
  
```
unsigned m_bWindowOnly:1;
```  
  
### <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Pokud chcete použít tento člen dat v rámci třídy ovládacího prvku, je potřeba deklarovat jako člena dat ve třídě ovládacího. Třídě ovládacího nebude dědění tento člen data ze základní třídy, protože je deklarované v rámci spojení v základní třídě.  
  
##  <a name="m_bwndless"></a>CComControlBase::m_bWndLess  
 Příznak, což značí, že je ovládací prvek bez oken.  
  
```
unsigned m_bWndLess:1;
```  
  
### <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Pokud chcete použít tento člen dat v rámci třídy ovládacího prvku, je potřeba deklarovat jako člena dat ve třídě ovládacího. Třídě ovládacího nebude dědění tento člen data ze základní třídy, protože je deklarované v rámci spojení v základní třídě.  
  
 Datový člen `m_spInPlaceSite` odkazuje na [IOleInPlaceSite](http://msdn.microsoft.com/library/windows/desktop/ms686586), [IOleInPlaceSiteEx](http://msdn.microsoft.com/library/windows/desktop/ms693461), nebo [IOleInPlaceSiteWindowless](http://msdn.microsoft.com/library/windows/desktop/ms682300) rozhraní, v závislosti na hodnotě `m_bWndLess` a [CComControlBase::m_bInPlaceSiteEx](#m_binplacesiteex) příznaky. (Datový člen [CComControlBase::m_bNegotiatedWnd](#m_bnegotiatedwnd) musí být **TRUE** pro [CComControlBase::m_spInPlaceSite](#m_spinplacesite) ukazatel platná.)  
  
 Pokud `m_bWndLess` je **TRUE**, `m_spInPlaceSite` je **IOleInPlaceSiteWindowless** ukazatel rozhraní. V tématu [CComControlBase::m_spInPlaceSite](#m_spinplacesite) pro tabulka zobrazující úplný vztah mezi tyto datové členy.  
  
##  <a name="m_hwndcd"></a>CComControlBase::m_hWndCD  
 Obsahuje odkaz na popisovač okna přidruženého k ovládacímu prvku.  
  
```
HWND& m_hWndCD;
```  
  
### <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Pokud chcete použít tento člen dat v rámci třídy ovládacího prvku, je potřeba deklarovat jako člena dat ve třídě ovládacího. Třídě ovládacího nebude dědění tento člen data ze základní třídy, protože je deklarované v rámci spojení v základní třídě.  
  
##  <a name="m_nfreezeevents"></a>CComControlBase::m_nFreezeEvents  
 Počet kolikrát kontejneru má pozastaveny události (odmítl akceptovat události) bez použité rozmrazení událostí (přijetí událostí).  
  
```
short m_nFreezeEvents;
```  
  
### <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Pokud chcete použít tento člen dat v rámci třídy ovládacího prvku, je potřeba deklarovat jako člena dat ve třídě ovládacího. Třídě ovládacího nebude dědění tento člen data ze základní třídy, protože je deklarované v rámci spojení v základní třídě.  
  
##  <a name="m_rcpos"></a>CComControlBase::m_rcPos  
 Umístění ovládacího prvku, vyjádřené v souřadnicích kontejneru v pixelech.  
  
```
RECT m_rcPos;
```  
  
### <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Pokud chcete použít tento člen dat v rámci třídy ovládacího prvku, je potřeba deklarovat jako člena dat ve třídě ovládacího. Třídě ovládacího nebude dědění tento člen data ze základní třídy, protože je deklarované v rámci spojení v základní třídě.  
  
##  <a name="m_sizeextent"></a>CComControlBase::m_sizeExtent  
 Rozsah ovládacího prvku HIMETRIC jednotky (jednotlivých jednotek je 0,01 milimetry) pro konkrétní zobrazení.  
  
```
SIZE m_sizeExtent;
```  
  
### <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Pokud chcete použít tento člen dat v rámci třídy ovládacího prvku, je potřeba deklarovat jako člena dat ve třídě ovládacího. Třídě ovládacího nebude dědění tento člen data ze základní třídy, protože je deklarované v rámci spojení v základní třídě.  
  
 Tato velikost je škálovat podle zobrazení. Velikost fyzického ovládacího prvku se zadává v `m_sizeNatural` – datový člen a vyřešen.  
  
 Velikost můžete převést na pixelů s globální funkce [AtlHiMetricToPixel](pixel-himetric-conversion-global-functions.md#atlhimetrictopixel).  
  
##  <a name="m_sizenatural"></a>CComControlBase::m_sizeNatural  
 Fyzické velikosti ovládacího prvku HIMETRIC jednotky (jednotlivých jednotek je 0,01 milimetrech).  
  
```
SIZE m_sizeNatural;
```  
  
### <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Pokud chcete použít tento člen dat v rámci třídy ovládacího prvku, je potřeba deklarovat jako člena dat ve třídě ovládacího. Třídě ovládacího nebude dědění tento člen data ze základní třídy, protože je deklarované v rámci spojení v základní třídě.  
  
 Tato velikost vyřešen, při velikosti v `m_sizeExtent` je škálovat podle zobrazení.  
  
 Velikost můžete převést na pixelů s globální funkce [AtlHiMetricToPixel](pixel-himetric-conversion-global-functions.md#atlhimetrictopixel).  
  
##  <a name="m_spadvisesink"></a>CComControlBase::m_spAdviseSink  
 Přímé ukazatel na poradní připojení na kontejneru (kontejneru [IAdviseSink](http://msdn.microsoft.com/library/windows/desktop/ms692513)).  
  
```
CComPtr<IAdviseSink>
    m_spAdviseSink;
```     
  
### <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Pokud chcete použít tento člen dat v rámci třídy ovládacího prvku, je potřeba deklarovat jako člena dat ve třídě ovládacího. Třídě ovládacího nebude dědění tento člen data ze základní třídy, protože je deklarované v rámci spojení v základní třídě.  
  
##  <a name="m_spambientdispatch"></a>CComControlBase::m_spAmbientDispatch  
 A `CComDispatchDriver` objekt, který vám umožní načíst a nastavit vlastnosti objektu prostřednictvím `IDispatch` ukazatel.  
  
```
CComDispatchDriver m_spAmbientDispatch;
```  
  
### <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Pokud chcete použít tento člen dat v rámci třídy ovládacího prvku, je potřeba deklarovat jako člena dat ve třídě ovládacího. Třídě ovládacího nebude dědění tento člen data ze základní třídy, protože je deklarované v rámci spojení v základní třídě.  
  
##  <a name="m_spclientsite"></a>CComControlBase::m_spClientSite  
 Ukazatel na lokality klienta ovládacího prvku v kontejneru.  
  
```
CComPtr<IOleClientSite>
    m_spClientSite;
```     
  
### <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Pokud chcete použít tento člen dat v rámci třídy ovládacího prvku, je potřeba deklarovat jako člena dat ve třídě ovládacího. Třídě ovládacího nebude dědění tento člen data ze základní třídy, protože je deklarované v rámci spojení v základní třídě.  
  
##  <a name="m_spdataadviseholder"></a>CComControlBase::m_spDataAdviseHolder  
 Poskytuje standardní prostředky k uložení poradní připojení mezi datové objekty a poradit jímky.  
  
```
CComPtr<IDataAdviseHolder>
    m_spDataAdviseHolder;
```     
  
### <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Pokud chcete použít tento člen dat v rámci třídy ovládacího prvku, je potřeba deklarovat jako člena dat ve třídě ovládacího. Třídě ovládacího nebude dědění tento člen data ze základní třídy, protože je deklarované v rámci spojení v základní třídě.  
  
 Datový objekt je ovládací prvek, který lze provádět přenos dat a který implementuje [IDataObject](http://msdn.microsoft.com/library/windows/desktop/ms688421), jejichž metody zadejte střední formát a přenos dat.  
  
 Rozhraní `m_spDataAdviseHolder` implementuje [IDataObject::DAdvise](http://msdn.microsoft.com/library/windows/desktop/ms692579) a [IDataObject::DUnadvise](http://msdn.microsoft.com/library/windows/desktop/ms692448) metody pro vytvoření a odstranění poradní připojení ke kontejneru. Kontejneru ovládacího prvku musí implementovat jímky doporučení díky podpoře [IAdviseSink](http://msdn.microsoft.com/library/windows/desktop/ms692513) rozhraní.  
  
##  <a name="m_spinplacesite"></a>CComControlBase::m_spInPlaceSite  
 Ukazatel na kontejneru [IOleInPlaceSite](http://msdn.microsoft.com/library/windows/desktop/ms686586), [IOleInPlaceSiteEx](http://msdn.microsoft.com/library/windows/desktop/ms693461), nebo [IOleInPlaceSiteWindowless](http://msdn.microsoft.com/library/windows/desktop/ms682300) ukazatel rozhraní.  
  
```
CComPtr<IOleInPlaceSiteWindowless>
    m_spInPlaceSite;
```     
  
### <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Pokud chcete použít tento člen dat v rámci třídy ovládacího prvku, je potřeba deklarovat jako člena dat ve třídě ovládacího. Třídě ovládacího nebude dědění tento člen data ze základní třídy, protože je deklarované v rámci spojení v základní třídě.  
  
 `m_spInPlaceSite` Ukazatel je platná pouze v případě [m_bNegotiatedWnd](#m_bnegotiatedwnd) je příznak **TRUE**.  
  
 Následující tabulka ilustruje jak `m_spInPlaceSite` ukazatel typu závisí na [m_bWndLess](#m_bwndless) a [m_bInPlaceSiteEx](#m_binplacesiteex) data člena příznaky:  
  
|m_spInPlaceSite typu|m_bWndLess hodnota|m_bInPlaceSiteEx hodnota|  
|---------------------------|-----------------------|-----------------------------|  
|**IOleInPlaceSiteWindowless**|**HODNOTA TRUE**|**Hodnota TRUE,** nebo **FALSE**|  
|**IOleInPlaceSiteEx**|**FALSE**|**HODNOTA TRUE**|  
|`IOleInPlaceSite`|**FALSE**|**FALSE**|  
  
##  <a name="m_spoleadviseholder"></a>CComControlBase::m_spOleAdviseHolder  
 Poskytuje standardní implementace způsob, jak uložení poradní připojení.  
  
```
CComPtr<IOleAdviseHolder>
    m_spOleAdviseHolder;
```     
  
### <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Pokud chcete použít tento člen dat v rámci třídy ovládacího prvku, je potřeba deklarovat jako člena dat ve třídě ovládacího. Třídě ovládacího nebude dědění tento člen data ze základní třídy, protože je deklarované v rámci spojení v základní třídě.  
  
 Rozhraní `m_spOleAdviseHolder` implementuje [IOleObject::Advise](http://msdn.microsoft.com/library/windows/desktop/ms686573) a [IOleObject::Unadvise](http://msdn.microsoft.com/library/windows/desktop/ms693749) metody pro vytvoření a odstranění poradní připojení ke kontejneru. Kontejneru ovládacího prvku musí implementovat jímky doporučení díky podpoře [IAdviseSink](http://msdn.microsoft.com/library/windows/desktop/ms692513) rozhraní.  
  
##  <a name="ondraw"></a>CComControlBase::OnDraw  
 Potlačí tuto metodu k vykreslení ovládacího prvku.  
  
```
virtual HRESULT OnDraw(ATL_DRAWINFO& di);
```  
  
### <a name="parameters"></a>Parametry  
 `di`  
 Odkaz na [ATL_DRAWINFO](../../atl/reference/atl-drawinfo-structure.md) struktura, která obsahuje kreslení informace, například kreslení aspekt, řízení hranice, a jestli je optimalizovaná výkresu nebo ne.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT` hodnotu.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí hodnota `OnDraw` odstraní nebo obnoví kontextu zařízení nebo se nic nestane, v závislosti na příznaky nastavit [CComControlBase::OnDrawAdvanced](#ondrawadvanced).  
  
 `OnDraw` Metody se automaticky přidá do vaší třídy ovládací prvek při vytváření vlastního ovládacího prvku pomocí Průvodce ovládacím prvkem ATL. V Průvodci výchozí `OnDraw` nevykresluje obdélníku s popiskem "ATL 8.0".  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [CComControlBase::GetAmbientAppearance](#getambientappearance).  
  
##  <a name="ondrawadvanced"></a>CComControlBase::OnDrawAdvanced  
 Výchozí hodnota `OnDrawAdvanced` připraví kontextu normalizovaný zařízení pro vykreslování a potom volá třída ovládacích prvků `OnDraw` metoda.  
  
```
virtual HRESULT OnDrawAdvanced(ATL_DRAWINFO& di);
```  
  
### <a name="parameters"></a>Parametry  
 `di`  
 Odkaz na [ATL_DRAWINFO](../../atl/reference/atl-drawinfo-structure.md) struktura, která obsahuje kreslení informace, například kreslení aspekt, řízení hranice, a jestli je optimalizovaná výkresu nebo ne.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT` hodnotu.  
  
### <a name="remarks"></a>Poznámky  
 Potlačí tuto metodu, pokud chcete přijímat kontextu zařízení bez normalizace, je předaná kontejneru.  
  
 V tématu [CComControlBase::OnDraw](#ondraw) další podrobnosti.  
  
##  <a name="onkillfocus"></a>CComControlBase::OnKillFocus  
 Kontroluje, zda ovládací prvek je aktivní na místě a má platný řízení lokality, a kontejneru informuje, že ovládací prvek ztratil fokus.  
  
```
LRESULT OnKillFocus(UINT /* nMsg */,
    WPARAM /* wParam */,
    LPARAM /* lParam */,
    BOOL& bHandled);
```  
  
### <a name="parameters"></a>Parametry  
 `nMsg`  
 Vyhrazena.  
  
 `wParam`  
 Vyhrazena.  
  
 `lParam`  
 Vyhrazena.  
  
 `bHandled`  
 Příznak, který indikuje, zda byla úspěšně zpracována zpráv oken. Výchozí hodnota je `FALSE`.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vždy vrátí hodnotu 1.  
  
##  <a name="onmouseactivate"></a>CComControlBase::OnMouseActivate  
 Kontroluje, zda je v uživatelském režimu uživatelského rozhraní, a aktivuje ovládacího prvku.  
  
```
LRESULT OnMouseActivate(UINT /* nMsg */,
    WPARAM /* wParam */,
    LPARAM /* lParam */,
    BOOL& bHandled);
```  
  
### <a name="parameters"></a>Parametry  
 `nMsg`  
 Vyhrazena.  
  
 `wParam`  
 Vyhrazena.  
  
 `lParam`  
 Vyhrazena.  
  
 `bHandled`  
 Příznak, který indikuje, zda byla úspěšně zpracována zpráv oken. Výchozí hodnota je `FALSE`.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vždy vrátí hodnotu 1.  
  
##  <a name="onpaint"></a>CComControlBase::OnPaint  
 Připraví kontejneru pro malování, získá ovládacího prvku klientské oblasti a pak zavolá třídu ovládacího prvku `OnDrawAdvanced` metoda.  
  
```
LRESULT OnPaint(UINT /* nMsg */,
    WPARAM wParam,
    LPARAM /* lParam */,
    BOOL& /* lResult */);
```  
  
### <a name="parameters"></a>Parametry  
 `nMsg`  
 Vyhrazena.  
  
 `wParam`  
 Existující HDC.  
  
 `lParam`  
 Vyhrazena.  
  
 `lResult`  
 Vyhrazena.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vždy vrátí hodnotu nula.  
  
### <a name="remarks"></a>Poznámky  
 Pokud `wParam` nemá hodnotu NULL, `OnPaint` předpokládá neobsahuje platný HDC a používá se místo [CComControlBase::m_hWndCD](#m_hwndcd).  
  
##  <a name="onsetfocus"></a>CComControlBase::OnSetFocus  
 Kontroluje, zda ovládací prvek je aktivní na místě a má platný řízení lokality, a informuje kontejneru ovládacího prvku si získávají fokus.  
  
```
LRESULT OnSetFocus(UINT /* nMsg */,
    WPARAM /* wParam */,
    LPARAM /* lParam */,
    BOOL& bHandled);
```  
  
### <a name="parameters"></a>Parametry  
 `nMsg`  
 Vyhrazena.  
  
 `wParam`  
 Vyhrazena.  
  
 `lParam`  
 Vyhrazena.  
  
 `bHandled`  
 Příznak, který indikuje, zda byla úspěšně zpracována zpráv oken. Výchozí hodnota je `FALSE`.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vždy vrátí hodnotu 1.  
  
### <a name="remarks"></a>Poznámky  
 Odešle oznámení do kontejneru, ovládacího prvku přijal fokus.  
  
##  <a name="pretranslateaccelerator"></a>CComControlBase::PreTranslateAccelerator  
 Potlačí tuto metodu poskytnout vlastní klávesnice akcelerátoru obslužné rutiny.  
  
```
BOOL PreTranslateAccelerator(LPMSG /* pMsg */,
    HRESULT& /* hRet */);
```  
  
### <a name="parameters"></a>Parametry  
 `pMsg`  
 Vyhrazena.  
  
 *hRet*  
 Vyhrazena.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ve výchozím nastavení vrací **FALSE**.  
  
##  <a name="sendonclose"></a>CComControlBase::SendOnClose  
 Oznámí všechny poradní jímky zaregistrována držitele doporučení, že byla uzavřena ovládacího prvku.  
  
```
HRESULT SendOnClose();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Odešle oznámení, že ovládací prvek zavřel jeho poradní jímky.  
  
##  <a name="sendondatachange"></a>CComControlBase::SendOnDataChange  
 Oznámí všechny poradní jímky zaregistrována držitele doporučení, které se změnily data ovládacího prvku.  
  
```
HRESULT SendOnDataChange(DWORD advf = 0);
```  
  
### <a name="parameters"></a>Parametry  
 *advf*  
 Pomocné příznaky, které určují, jak volání [IAdviseSink::OnDataChange](http://msdn.microsoft.com/library/windows/desktop/ms687283) Přišla žádost. Hodnoty jsou od [ADVF](http://msdn.microsoft.com/library/windows/desktop/ms693742) výčtu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
##  <a name="sendonrename"></a>CComControlBase::SendOnRename  
 Oznámí všechny poradní jímky zaregistrována držitele doporučení, že ovládací prvek má nové přezdívka.  
  
```
HRESULT SendOnRename(IMoniker* pmk);
```  
  
### <a name="parameters"></a>Parametry  
 *životnosti klíče PMK*  
 Ukazatel na nové Přezdívka ovládacího prvku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Odešle oznámení, že došlo ke změně Přezdívka pro ovládací prvek.  
  
##  <a name="sendonsave"></a>CComControlBase::SendOnSave  
 Oznámí všechny poradní jímky zaregistrována držitele doporučení, která byla uložena ovládacího prvku.  
  
```
HRESULT SendOnSave();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Odešle oznámení, že ovládací prvek právě uchránila jeho data.  
  
##  <a name="sendonviewchange"></a>CComControlBase::SendOnViewChange  
 Upozorní, že všechny registrované poradní jímky, které došlo ke změně zobrazení ovládacího prvku.  
  
```
HRESULT SendOnViewChange(DWORD dwAspect, LONG lindex = -1);
```  
  
### <a name="parameters"></a>Parametry  
 `dwAspect`  
 Aspekt nebo zobrazení ovládacího prvku.  
  
 *index*  
 Část zobrazení, které se změnily. Je platný pouze hodnotu -1.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
### <a name="remarks"></a>Poznámky  
 `SendOnViewChange`volání [IAdviseSink::OnViewChange](http://msdn.microsoft.com/library/windows/desktop/ms694337). Pouze hodnota *index* aktuálně podporována. je -1, která označuje, že je celého zobrazení zájmu.  
  
##  <a name="setcontrolfocus"></a>CComControlBase::SetControlFocus  
 Nastaví nebo odebere fokus klávesnice do nebo z ovládacího prvku.  
  
```
BOOL SetControlFocus(BOOL bGrab);
```  
  
### <a name="parameters"></a>Parametry  
 *bGrab*  
 Pokud **TRUE**, nastaví fokus klávesnice do ovládacího prvku volání. Pokud **FALSE**, odebere fokus klávesnice z ovládacího prvku volání zadaný má fokus.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí **TRUE** Pokud ovládací prvek úspěšně přijme fokus; jinak **FALSE**.  
  
### <a name="remarks"></a>Poznámky  
 Pro ovládacího prvku oddílové funkce rozhraní API systému Windows [SetFocus](http://msdn.microsoft.com/library/windows/desktop/ms646312) je volána. Bez oken ovládacího prvku [IOleInPlaceSiteWindowless::SetFocus](http://msdn.microsoft.com/library/windows/desktop/ms679745) je volána. Pomocí tohoto volání ovládacího prvku bez oken získá fokus klávesnice a může reagovat na okno zprávy.  
  
##  <a name="setdirty"></a>CComControlBase::SetDirty  
 Nastaví datový člen `m_bRequiresSave` na hodnotu v `bDirty`.  
  
```
void SetDirty(BOOL bDirty);
```  
  
### <a name="parameters"></a>Parametry  
 `bDirty`  
 Hodnota člena dat [CComControlBase::m_bRequiresSave](#m_brequiressave).  
  
### <a name="remarks"></a>Poznámky  
 **SetDirty(TRUE)** by měla být volána k příznak, že se od posledního uložení změnila ovládacího prvku. Hodnota `m_bRequiresSave` získává spolu s [CComControlBase::GetDirty](#getdirty).  
  
## <a name="see-also"></a>Viz také  
 [CComControl – třída](../../atl/reference/ccomcontrol-class.md)   
 [Přehled třídy](../../atl/atl-class-overview.md)
