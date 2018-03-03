---
title: "Třída IOleObjectImpl | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IOleObjectImpl
- ATLCTL/ATL::IOleObjectImpl
- ATLCTL/ATL::IOleObjectImpl::Advise
- ATLCTL/ATL::IOleObjectImpl::Close
- ATLCTL/ATL::IOleObjectImpl::DoVerb
- ATLCTL/ATL::IOleObjectImpl::DoVerbDiscardUndo
- ATLCTL/ATL::IOleObjectImpl::DoVerbHide
- ATLCTL/ATL::IOleObjectImpl::DoVerbInPlaceActivate
- ATLCTL/ATL::IOleObjectImpl::DoVerbOpen
- ATLCTL/ATL::IOleObjectImpl::DoVerbPrimary
- ATLCTL/ATL::IOleObjectImpl::DoVerbShow
- ATLCTL/ATL::IOleObjectImpl::DoVerbUIActivate
- ATLCTL/ATL::IOleObjectImpl::EnumAdvise
- ATLCTL/ATL::IOleObjectImpl::EnumVerbs
- ATLCTL/ATL::IOleObjectImpl::GetClientSite
- ATLCTL/ATL::IOleObjectImpl::GetClipboardData
- ATLCTL/ATL::IOleObjectImpl::GetExtent
- ATLCTL/ATL::IOleObjectImpl::GetMiscStatus
- ATLCTL/ATL::IOleObjectImpl::GetMoniker
- ATLCTL/ATL::IOleObjectImpl::GetUserClassID
- ATLCTL/ATL::IOleObjectImpl::GetUserType
- ATLCTL/ATL::IOleObjectImpl::InitFromData
- ATLCTL/ATL::IOleObjectImpl::IsUpToDate
- ATLCTL/ATL::IOleObjectImpl::OnPostVerbDiscardUndo
- ATLCTL/ATL::IOleObjectImpl::OnPostVerbHide
- ATLCTL/ATL::IOleObjectImpl::OnPostVerbInPlaceActivate
- ATLCTL/ATL::IOleObjectImpl::OnPostVerbOpen
- ATLCTL/ATL::IOleObjectImpl::OnPostVerbShow
- ATLCTL/ATL::IOleObjectImpl::OnPostVerbUIActivate
- ATLCTL/ATL::IOleObjectImpl::OnPreVerbDiscardUndo
- ATLCTL/ATL::IOleObjectImpl::OnPreVerbHide
- ATLCTL/ATL::IOleObjectImpl::OnPreVerbInPlaceActivate
- ATLCTL/ATL::IOleObjectImpl::OnPreVerbOpen
- ATLCTL/ATL::IOleObjectImpl::OnPreVerbShow
- ATLCTL/ATL::IOleObjectImpl::OnPreVerbUIActivate
- ATLCTL/ATL::IOleObjectImpl::SetClientSite
- ATLCTL/ATL::IOleObjectImpl::SetColorScheme
- ATLCTL/ATL::IOleObjectImpl::SetExtent
- ATLCTL/ATL::IOleObjectImpl::SetHostNames
- ATLCTL/ATL::IOleObjectImpl::SetMoniker
- ATLCTL/ATL::IOleObjectImpl::Unadvise
- ATLCTL/ATL::IOleObjectImpl::Update
dev_langs:
- C++
helpviewer_keywords:
- ActiveX controls [C++], communication between container and control
- IOleObject, ATL implementation
- IOleObjectImpl class
ms.assetid: 59750b2d-1633-4a51-a4c2-6455b6b90c45
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f710953a32ccb32c63742ab28e84818f3a330336
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="ioleobjectimpl-class"></a>IOleObjectImpl – třída
Tato třída implementuje **IUnknown** a je hlavní rozhraní, pomocí které kontejner komunikuje s ovládacím prvkem.  
  
> [!IMPORTANT]
>  Tato třída a její členy nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<class T>  
class ATL_NO_VTABLE IOleObjectImpl : public IOleObject
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Vlastní třídy odvozené od `IOleObjectImpl`.  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[IOleObjectImpl::Advise](#advise)|Vytvoří poradní připojení pomocí ovládacího prvku.|  
|[IOleObjectImpl::Close](#close)|Změnit stav ovládacího prvku ve spuštění načíst.|  
|[IOleObjectImpl::DoVerb](#doverb)|Říká ovládacímu prvku provést jednu z jeho výčtové akce.|  
|[IOleObjectImpl::DoVerbDiscardUndo](#doverbdiscardundo)|Říká ovládacímu prvku vyřadí všechny operace vrácení zpět stavu, ve kterém se udržuje.|  
|[IOleObjectImpl::DoVerbHide](#doverbhide)|Říká ovládacímu prvku odebrat svoje uživatelské rozhraní ze zobrazení.|  
|[IOleObjectImpl::DoVerbInPlaceActivate](#doverbinplaceactivate)|Spustí ovládacího prvku a nainstaluje její okno, ale nenainstaluje uživatelské rozhraní ovládacího prvku.|  
|[IOleObjectImpl::DoVerbOpen](#doverbopen)|Způsobí, že ovládací prvek být upravit otevřené v samostatném okně.|  
|[IOleObjectImpl::DoVerbPrimary](#doverbprimary)|Provede zadanou akci při poklepání ovládacího prvku. Ovládací prvek definuje akce, obvykle k aktivaci ovládacího prvku na místě.|  
|[IOleObjectImpl::DoVerbShow](#doverbshow)|Ukazuje nově vloženou ovládací prvek pro uživatele.|  
|[IOleObjectImpl::DoVerbUIActivate](#doverbuiactivate)|Zobrazuje uživatelské rozhraní ovládacího prvku, jako je například nabídek a panelů nástrojů a aktivuje ovládacího prvku na místě.|  
|[IOleObjectImpl::EnumAdvise](#enumadvise)|Vytvoří výčet poradní připojení ovládacího prvku.|  
|[IOleObjectImpl::EnumVerbs](#enumverbs)|Vytvoří výčet akce pro ovládací prvek.|  
|[IOleObjectImpl::GetClientSite](#getclientsite)|Načte ovládacího prvku lokality klienta.|  
|[IOleObjectImpl::GetClipboardData](#getclipboarddata)|Načte data ze schránky. Implementace ATL vrátí **E_NOTIMPL**.|  
|[IOleObjectImpl::GetExtent](#getextent)|Načte rozsah oblasti zobrazení ovládacího prvku.|  
|[IOleObjectImpl::GetMiscStatus](#getmiscstatus)|Načte stav ovládacího prvku.|  
|[IOleObjectImpl::GetMoniker](#getmoniker)|Načte Přezdívka ovládacího prvku. Implementace ATL vrátí **E_NOTIMPL**.|  
|[IOleObjectImpl::GetUserClassID](#getuserclassid)|Načte identifikátor třídy ovládacího prvku.|  
|[IOleObjectImpl::GetUserType](#getusertype)|Načte název uživatele – typ ovládacího prvku.|  
|[IOleObjectImpl::InitFromData](#initfromdata)|Inicializuje z vybraných dat ovládacího prvku. Implementace ATL vrátí **E_NOTIMPL**.|  
|[IOleObjectImpl::IsUpToDate](#isuptodate)|Ověří, zda je aktuální ovládací prvek. Implementace ATL vrátí `S_OK`.|  
|[IOleObjectImpl::OnPostVerbDiscardUndo](#onpostverbdiscardundo)|Voláno rozhraním [DoVerbDiscardUndo](#doverbdiscardundo) po stavu vrácení zpět se zahodí.|  
|[IOleObjectImpl::OnPostVerbHide](#onpostverbhide)|Voláno rozhraním [DoVerbHide](#doverbhide) po je skrytý ovládací prvek.|  
|[IOleObjectImpl::OnPostVerbInPlaceActivate](#onpostverbinplaceactivate)|Voláno rozhraním [DoVerbInPlaceActivate](#doverbinplaceactivate) po aktivaci ovládacího prvku na místě.|  
|[IOleObjectImpl::OnPostVerbOpen](#onpostverbopen)|Voláno rozhraním [DoVerbOpen](#doverbopen) po otevření ovládací prvek pro úpravy v samostatném okně.|  
|[IOleObjectImpl::OnPostVerbShow](#onpostverbshow)|Voláno rozhraním [DoVerbShow](#doverbshow) po ovládacího prvku viditelné.|  
|[IOleObjectImpl::OnPostVerbUIActivate](#onpostverbuiactivate)|Voláno rozhraním [DoVerbUIActivate](#doverbuiactivate) po aktivaci ovládacího prvku uživatelského rozhraní.|  
|[IOleObjectImpl::OnPreVerbDiscardUndo](#onpreverbdiscardundo)|Voláno rozhraním [DoVerbDiscardUndo](#doverbdiscardundo) před vrácení zpět se zahodí stavu.|  
|[IOleObjectImpl::OnPreVerbHide](#onpreverbhide)|Voláno rozhraním [DoVerbHide](#doverbhide) předtím, než je skrytý ovládací prvek.|  
|[IOleObjectImpl::OnPreVerbInPlaceActivate](#onpreverbinplaceactivate)|Voláno rozhraním [DoVerbInPlaceActivate](#doverbinplaceactivate) před aktivací ovládacího prvku na místě.|  
|[IOleObjectImpl::OnPreVerbOpen](#onpreverbopen)|Voláno rozhraním [DoVerbOpen](#doverbopen) před otevřel ovládací prvek pro úpravy v samostatném okně.|  
|[IOleObjectImpl::OnPreVerbShow](#onpreverbshow)|Voláno rozhraním [DoVerbShow](#doverbshow) před ovládacího prvku provedl se viditelné.|  
|[IOleObjectImpl::OnPreVerbUIActivate](#onpreverbuiactivate)|Voláno rozhraním [DoVerbUIActivate](#doverbuiactivate) před aktivoval uživatelské rozhraní ovládacího prvku.|  
|[IOleObjectImpl::SetClientSite](#setclientsite)|Informuje o jeho lokality klienta v kontejneru ovládacího prvku.|  
|[IOleObjectImpl::SetColorScheme](#setcolorscheme)|Doporučuje barevné schéma do ovládacího prvku aplikace, pokud existuje. Implementace ATL vrátí **E_NOTIMPL**.|  
|[IOleObjectImpl::SetExtent](#setextent)|Nastaví rozsah oblasti zobrazení ovládacího prvku.|  
|[IOleObjectImpl::SetHostNames](#sethostnames)|Říká ovládacímu prvku názvy aplikace kontejnerů a kontejner dokumentu.|  
|[IOleObjectImpl::SetMoniker](#setmoniker)|Co je jeho Přezdívka říká ovládacímu prvku. Implementace ATL vrátí **E_NOTIMPL**.|  
|[IOleObjectImpl::Unadvise](#unadvise)|Odstraní připojení k poradní pomocí ovládacího prvku.|  
|[IOleObjectImpl::Update](#update)|Aktualizuje ovládacího prvku. Implementace ATL vrátí `S_OK`.|  
  
## <a name="remarks"></a>Poznámky  
 [IOleObject](http://msdn.microsoft.com/library/windows/desktop/dd542709) rozhraní je hlavní rozhraní, pomocí které kontejner komunikuje s ovládacím prvkem. Třída `IOleObjectImpl` poskytuje výchozí implementaci tohoto rozhraní a implementuje **IUnknown** posíláním informací o k výpisu zařízení ladění sestavení.  
  
 **Související články** [ATL – tutoriál](../../atl/active-template-library-atl-tutorial.md), [vytváření projektu knihovny ATL](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `IOleObject`  
  
 `IOleObjectImpl`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlctl.h  
  
##  <a name="advise"></a>IOleObjectImpl::Advise  
 Vytvoří poradní připojení pomocí ovládacího prvku.  
  
```
STDMETHOD(Advise)(
    IAdviseSink* pAdvSink,
    DWORD* pdwConnection);
```  
  
### <a name="remarks"></a>Poznámky  
 V tématu [IOleObject::Advise](http://msdn.microsoft.com/library/windows/desktop/ms686573) ve Windows SDK.  
  
##  <a name="close"></a>IOleObjectImpl::Close  
 Změnit stav ovládacího prvku ve spuštění načíst.  
  
```
STDMETHOD(Close)(DWORD dwSaveOption);
```  
  
### <a name="remarks"></a>Poznámky  
 Deaktivuje ovládacího prvku a zničí okně řízení, pokud existuje. Pokud – datový člen třídy ovládacího prvku [CComControlBase::m_bRequiresSave](../../atl/reference/ccomcontrolbase-class.md#m_brequiressave) je **TRUE** a `dwSaveOption` parametr je buď `OLECLOSE_SAVEIFDIRTY` nebo `OLECLOSE_PROMPTSAVE`, se uloží vlastnosti ovládacích prvků Před zavřením.  
  
 Následující ukazatele uchovávat v datové členy třídy ovládacího prvku [CComControlBase::m_spInPlaceSite](../../atl/reference/ccomcontrolbase-class.md#m_spinplacesite) a [CComControlBase::m_spAdviseSink](../../atl/reference/ccomcontrolbase-class.md#m_spadvisesink) vydání a datových členů [CComControlBase:: m_bNegotiatedWnd](../../atl/reference/ccomcontrolbase-class.md#m_bnegotiatedwnd), [CComControlBase::m_bWndless](../../atl/reference/ccomcontrolbase-class.md#m_bwndless), a [CComControlBase::m_bInPlaceSiteEx](../../atl/reference/ccomcontrolbase-class.md#m_binplacesiteex) jsou nastaveny na **FALSE**.  
  
 V tématu [IOleObject::Close](http://msdn.microsoft.com/library/windows/desktop/ms683922) ve Windows SDK.  
  
##  <a name="doverb"></a>IOleObjectImpl::DoVerb  
 Říká ovládacímu prvku provést jednu z jeho výčtové akce.  
  
```
STDMETHOD(DoVerb)(
    LONG iVerb,
    LPMSG /* pMsg */,
    IOleClientSite* pActiveSite,
    LONG /* lindex */,
    HWND hwndParent,
    LPCRECT lprcPosRect);
```  
  
### <a name="remarks"></a>Poznámky  
 V závislosti na hodnotě `iVerb`, jeden z knihovny ATL `DoVerb` podpůrné funkce je volána následujícím způsobem:  
  
|*iVerb* hodnota|Volaná funkce DoVerb pomocné funkce|  
|-------------------|-----------------------------------|  
|**OLEIVERB_DISCARDUNDOSTATE**|[DoVerbDiscardUndo](#doverbdiscardundo)|  
|`OLEIVERB_HIDE`|[DoVerbHide](#doverbhide)|  
|**OLEIVERB_INPLACEACTIVATE**|[DoVerbInPlaceActivate](#doverbinplaceactivate)|  
|`OLEIVERB_OPEN`|[DoVerbOpen](#doverbopen)|  
|`OLEIVERB_PRIMARY`|[DoVerbPrimary](#doverbprimary)|  
|**OLEIVERB_PROPERTIES**|[CComControlBase::DoVerbProperties](../../atl/reference/ccomcontrolbase-class.md#doverbproperties)|  
|`OLEIVERB_SHOW`|[DoVerbShow](#doverbshow)|  
|`OLEIVERB_UIACTIVATE`|[DoVerbUIActivate](#doverbuiactivate)|  
  
 V tématu [Funkce IOleObject::DoVerb](http://msdn.microsoft.com/library/windows/desktop/ms694508) ve Windows SDK.  
  
##  <a name="doverbdiscardundo"></a>IOleObjectImpl::DoVerbDiscardUndo  
 Říká ovládacímu prvku vyřadí všechny operace vrácení zpět stavu, ve kterém se udržuje.  
  
```
HRESULT DoVerbDiscardUndo(LPCRECT /* prcPosRect */, HWND /* hwndParent */);
```  
  
### <a name="parameters"></a>Parametry  
 `prcPosRec`  
 [v] Ukazatel na rámeček kontejneru chce, aby se k vykreslení do ovládacího prvku.  
  
 *hwndParent*  
 [v] Popisovač okna obsahující ovládacího prvku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `S_OK`.  
  
##  <a name="doverbhide"></a>IOleObjectImpl::DoVerbHide  
 Deaktivuje a odebere uživatelské rozhraní ovládacího prvku a skryje ovládacího prvku.  
  
```
HRESULT DoVerbHide(LPCRECT /* prcPosRect */, HWND /* hwndParent */);
```  
  
### <a name="parameters"></a>Parametry  
 `prcPosRec`  
 [v] Ukazatel na rámeček kontejneru chce, aby se k vykreslení do ovládacího prvku.  
  
 *hwndParent*  
 [v] Popisovač okna obsahující ovládacího prvku. Nepoužívá se v implementaci ATL.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `S_OK`.  
  
##  <a name="doverbinplaceactivate"></a>IOleObjectImpl::DoVerbInPlaceActivate  
 Spustí ovládacího prvku a nainstaluje její okno, ale nenainstaluje uživatelské rozhraní ovládacího prvku.  
  
```
HRESULT DoVerbInPlaceActivate(LPCRECT prcPosRect, HWND /* hwndParent */);
```  
  
### <a name="parameters"></a>Parametry  
 `prcPosRec`  
 [v] Ukazatel na rámeček kontejneru chce, aby se k vykreslení do ovládacího prvku.  
  
 *hwndParent*  
 [v] Popisovač okna obsahující ovládacího prvku. Nepoužívá se v implementaci ATL.  
  
### <a name="return-value"></a>Návratová hodnota  
 Jeden standardní `HRESULT` hodnoty.  
  
### <a name="remarks"></a>Poznámky  
 Aktivuje ovládacího prvku na místě voláním [CComControlBase::InPlaceActivate](../../atl/reference/ccomcontrolbase-class.md#inplaceactivate). Pokud – datový člen třídy ovládacího prvku `m_bWindowOnly` je **TRUE**, `DoVerbInPlaceActivate` se nejprve pokusí o aktivaci ovládacího prvku jako bez oken (možné pouze v případě, že kontejner podporuje [IOleInPlaceSiteWindowless ](http://msdn.microsoft.com/library/windows/desktop/ms682300)). Pokud to nepomůže, funkce se pokusí aktivovat ovládacího prvku s rozšířené funkce (možné pouze v případě, že kontejner podporuje [IOleInPlaceSiteEx](http://msdn.microsoft.com/library/windows/desktop/ms693461)). Pokud to nepomůže, funkce se pokusí aktivovat ovládacího prvku s žádné rozšířené funkce (možné pouze v případě, že kontejner podporuje [IOleInPlaceSite](http://msdn.microsoft.com/library/windows/desktop/ms686586)). Pokud je aktivace úspěšná, funkce oznamuje kontejneru že ovládacího prvku byl aktivován.  
  
##  <a name="doverbopen"></a>IOleObjectImpl::DoVerbOpen  
 Způsobí, že ovládací prvek být upravit otevřené v samostatném okně.  
  
```
HRESULT DoVerbOpen(LPCRECT /* prcPosRect */, HWND /* hwndParent */);
```  
  
### <a name="parameters"></a>Parametry  
 `prcPosRec`  
 [v] Ukazatel na rámeček kontejneru chce, aby se k vykreslení do ovládacího prvku.  
  
 *hwndParent*  
 [v] Popisovač okna obsahující ovládacího prvku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `S_OK`.  
  
##  <a name="doverbprimary"></a>IOleObjectImpl::DoVerbPrimary  
 Definuje akce při poklepání ovládacího prvku.  
  
```
HRESULT DoVerbPrimary(LPCRECT prcPosRect, HWND hwndParent);
```  
  
### <a name="parameters"></a>Parametry  
 `prcPosRec`  
 [v] Ukazatel na rámeček kontejneru chce, aby se k vykreslení do ovládacího prvku.  
  
 *hwndParent*  
 [v] Popisovač okna obsahující ovládacího prvku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Jeden standardní `HRESULT` hodnoty.  
  
### <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení k zobrazení stránky vlastností. Toto můžete přepsat ve třídě ovládacího k vyvolání různé chování v poklikejte na soubor; například přehrávání videa nebo přejděte na místě aktivní.  
  
##  <a name="doverbshow"></a>IOleObjectImpl::DoVerbShow  
 Informuje kontejneru zpřístupněte ovládacího prvku.  
  
```
HRESULT DoVerbShow(LPCRECT prcPosRect, HWND /* hwndParent */);
```  
  
### <a name="parameters"></a>Parametry  
 `prcPosRec`  
 [v] Ukazatel na rámeček kontejneru chce, aby se k vykreslení do ovládacího prvku.  
  
 *hwndParent*  
 [v] Popisovač okna obsahující ovládacího prvku. Nepoužívá se v implementaci ATL.  
  
### <a name="return-value"></a>Návratová hodnota  
 Jeden standardní `HRESULT` hodnoty.  
  
##  <a name="doverbuiactivate"></a>IOleObjectImpl::DoVerbUIActivate  
 Aktivuje uživatelské rozhraní ovládacího prvku a kontejneru upozorní, že jeho nabídky se nahrazují složené nabídky.  
  
```
HRESULT DoVerbUIActivate(LPCRECT prcPosRect, HWND /* hwndParent */);
```  
  
### <a name="parameters"></a>Parametry  
 `prcPosRec`  
 [v] Ukazatel na rámeček kontejneru chce, aby se k vykreslení do ovládacího prvku.  
  
 *hwndParent*  
 [v] Popisovač okna obsahující ovládacího prvku. Nepoužívá se v implementaci ATL.  
  
### <a name="return-value"></a>Návratová hodnota  
 Jeden standardní `HRESULT` hodnoty.  
  
##  <a name="enumadvise"></a>IOleObjectImpl::EnumAdvise  
 Poskytuje výčet registrované poradní připojení pro tento ovládací prvek.  
  
```
STDMETHOD(EnumAdvise)(IEnumSTATDATA** ppenumAdvise);
```  
  
### <a name="remarks"></a>Poznámky  
 V tématu [IOleObject::EnumAdvise](http://msdn.microsoft.com/library/windows/desktop/ms682355) ve Windows SDK.  
  
##  <a name="enumverbs"></a>IOleObjectImpl::EnumVerbs  
 Poskytuje výčet registrovaných akcí (operace) pro tento ovládací prvek voláním **OleRegEnumVerbs**.  
  
```
STDMETHOD(EnumVerbs)(IEnumOLEVERB** ppEnumOleVerb);
```  
  
### <a name="remarks"></a>Poznámky  
 Příkazy můžete přidat do souboru .rgs vašeho projektu. Například v tématu CIRCCTL. RGS v [str](../../visual-cpp-samples.md) ukázka.  
  
 V tématu [IOleObject::EnumVerbs](http://msdn.microsoft.com/library/windows/desktop/ms692781) ve Windows SDK.  
  
##  <a name="getclientsite"></a>IOleObjectImpl::GetClientSite  
 Vloží ukazatel myši ovládací prvek – datový člen třídy [CComControlBase::m_spClientSite](../../atl/reference/ccomcontrolbase-class.md#m_spclientsite) do *ppClientSite* a zvýší počet odkazů na ukazatele.  
  
```
STDMETHOD(GetClientSite)(IOleClientSite** ppClientSite);
```  
  
### <a name="remarks"></a>Poznámky  
 V tématu [IOleObject::GetClientSite](http://msdn.microsoft.com/library/windows/desktop/ms692603) ve Windows SDK.  
  
##  <a name="getclipboarddata"></a>IOleObjectImpl::GetClipboardData  
 Načte data ze schránky.  
  
```
STDMETHOD(GetClipboardData)(    
    DWORD /* dwReserved */,
    IDataObject** /* ppDataObject */);
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí **E_NOTIMPL**.  
  
### <a name="remarks"></a>Poznámky  
 V tématu [IOleObject::GetClipboardData](http://msdn.microsoft.com/library/windows/desktop/ms682288) ve Windows SDK.  
  
##  <a name="getextent"></a>IOleObjectImpl::GetExtent  
 Načte spuštěné řízení zobrazovanou velikostí mezi HIMETRIC jednotky (0,01 milimetru na jednotku).  
  
```
STDMETHOD(GetExtent)(
    DWORD dwDrawAspect,
    SIZEL* psizel);
```  
  
### <a name="remarks"></a>Poznámky  
 Velikost je uložen v datový člen třídy ovládacího prvku [CComControlBase::m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent).  
  
 V tématu [IOleObject::GetExtent](http://msdn.microsoft.com/library/windows/desktop/ms692325) ve Windows SDK.  
  
##  <a name="getmiscstatus"></a>IOleObjectImpl::GetMiscStatus  
 Vrací ukazatel na informace o registrovaných stavu pro ovládací prvek voláním **OleRegGetMiscStatus**.  
  
```
STDMETHOD(GetMiscStatus)(
    DWORD dwAspect,
    DWORD* pdwStatus);
```  
  
### <a name="remarks"></a>Poznámky  
 Informace o stavu zahrnuje chování podporuje ovládací prvek a prezentační data. Informace o stavu můžete přidat do souboru .rgs vašeho projektu.  
  
 V tématu [IOleObject::GetMiscStatus](http://msdn.microsoft.com/library/windows/desktop/ms678521) ve Windows SDK.  
  
##  <a name="getmoniker"></a>IOleObjectImpl::GetMoniker  
 Načte Přezdívka ovládacího prvku.  
  
```
STDMETHOD(GetMoniker)(
    DWORD /* dwAssign */,
    DWORD /* dwWhichMoniker */,
    IMoniker** /* ppmk */);
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí **E_NOTIMPL**.  
  
### <a name="remarks"></a>Poznámky  
 V tématu [IOleObject::GetMoniker](http://msdn.microsoft.com/library/windows/desktop/ms686576) ve Windows SDK.  
  
##  <a name="getuserclassid"></a>IOleObjectImpl::GetUserClassID  
 Vrátí identifikátor třídy ovládacího prvku.  
  
```
STDMETHOD(GetUserClassID)(CLSID* pClsid);
```  
  
### <a name="remarks"></a>Poznámky  
 V tématu [IOleObject::GetUserClassID](http://msdn.microsoft.com/library/windows/desktop/ms682313) ve Windows SDK.  
  
##  <a name="getusertype"></a>IOleObjectImpl::GetUserType  
 Vrací název uživatele – typ ovládacího prvku voláním **OleRegGetUserType**.  
  
```
STDMETHOD(GetUserType)(
    DWORD dwFormOfType,
    LPOLESTR* pszUserType);
```  
  
### <a name="remarks"></a>Poznámky  
 Název typu uživatele se používá pro zobrazení v prvky uživatelského rozhraní, jako jsou například nabídky a dialogová okna. Můžete změnit název typ uživatele v souboru .rgs vašeho projektu.  
  
 V tématu [IOleObject::GetUserType](http://msdn.microsoft.com/library/windows/desktop/ms688643) ve Windows SDK.  
  
##  <a name="initfromdata"></a>IOleObjectImpl::InitFromData  
 Inicializuje z vybraných dat ovládacího prvku.  
  
```
STDMETHOD(InitFromData)(
    IDataObject* /* pDataObject */,
    BOOL /* fCreation */,
    DWORD /* dwReserved */);
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí **E_NOTIMPL**.  
  
### <a name="remarks"></a>Poznámky  
 V tématu [IOleObject::InitFromData](http://msdn.microsoft.com/library/windows/desktop/ms688510) ve Windows SDK.  
  
##  <a name="isuptodate"></a>IOleObjectImpl::IsUpToDate  
 Ověří, zda je aktuální ovládací prvek.  
  
```
STDMETHOD(IsUpToDate)(void);
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `S_OK`.  
  
### <a name="remarks"></a>Poznámky  
 V tématu [IOleObject::IsUpToDate](http://msdn.microsoft.com/library/windows/desktop/ms686624) ve Windows SDK.  
  
##  <a name="onpostverbdiscardundo"></a>IOleObjectImpl::OnPostVerbDiscardUndo  
 Voláno rozhraním [DoVerbDiscardUndo](#doverbdiscardundo) po stavu vrácení zpět se zahodí.  
  
```
HRESULT OnPostVerbDiscardUndo();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `S_OK`.  
  
### <a name="remarks"></a>Poznámky  
 Potlačí tuto metodu s kódem, který má být proveden po stavu vrácení zpět se zahodí.  
  
##  <a name="onpostverbhide"></a>IOleObjectImpl::OnPostVerbHide  
 Voláno rozhraním [DoVerbHide](#doverbhide) po je skrytý ovládací prvek.  
  
```
HRESULT OnPostVerbHide();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `S_OK`.  
  
### <a name="remarks"></a>Poznámky  
 Potlačí tuto metodu s kódem, který má být proveden po je skrytý ovládací prvek.  
  
##  <a name="onpostverbinplaceactivate"></a>IOleObjectImpl::OnPostVerbInPlaceActivate  
 Voláno rozhraním [DoVerbInPlaceActivate](#doverbinplaceactivate) po aktivaci ovládacího prvku na místě.  
  
```
HRESULT OnPostVerbInPlaceActivate();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `S_OK`.  
  
### <a name="remarks"></a>Poznámky  
 Potlačí tuto metodu s kódem, který má být proveden po aktivaci ovládacího prvku na místě.  
  
##  <a name="onpostverbopen"></a>IOleObjectImpl::OnPostVerbOpen  
 Voláno rozhraním [DoVerbOpen](#doverbopen) po otevření ovládací prvek pro úpravy v samostatném okně.  
  
```
HRESULT OnPostVerbOpen();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `S_OK`.  
  
### <a name="remarks"></a>Poznámky  
 Potlačí tuto metodu s kódem, který má být proveden po otevření ovládací prvek pro úpravy v samostatném okně.  
  
##  <a name="onpostverbshow"></a>IOleObjectImpl::OnPostVerbShow  
 Voláno rozhraním [DoVerbShow](#doverbshow) po ovládacího prvku viditelné.  
  
```
HRESULT OnPostVerbShow();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `S_OK`.  
  
### <a name="remarks"></a>Poznámky  
 Potlačí tuto metodu s kódem, který má být proveden po ovládacího prvku viditelné.  
  
##  <a name="onpostverbuiactivate"></a>IOleObjectImpl::OnPostVerbUIActivate  
 Voláno rozhraním [DoVerbUIActivate](#doverbuiactivate) po aktivaci ovládacího prvku uživatelského rozhraní.  
  
```
HRESULT OnPostVerbUIActivate();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `S_OK`.  
  
### <a name="remarks"></a>Poznámky  
 Potlačí tuto metodu s kódem, který má být proveden po aktivaci ovládacího prvku uživatelského rozhraní.  
  
##  <a name="onpreverbdiscardundo"></a>IOleObjectImpl::OnPreVerbDiscardUndo  
 Voláno rozhraním [DoVerbDiscardUndo](#doverbdiscardundo) před vrácení zpět se zahodí stavu.  
  
```
HRESULT OnPreVerbDiscardUndo();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `S_OK`.  
  
### <a name="remarks"></a>Poznámky  
 Abyste zabránili stavu zpět budou odstraněny, přepište tuto metodu a vrátí chybu HRESULT.  
  
##  <a name="onpreverbhide"></a>IOleObjectImpl::OnPreVerbHide  
 Voláno rozhraním [DoVerbHide](#doverbhide) předtím, než je skrytý ovládací prvek.  
  
```
HRESULT OnPreVerbHide();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `S_OK`.  
  
### <a name="remarks"></a>Poznámky  
 Abyste zabránili skryté ovládacího prvku, přepište tuto metodu a vrátí chybu HRESULT.  
  
##  <a name="onpreverbinplaceactivate"></a>IOleObjectImpl::OnPreVerbInPlaceActivate  
 Voláno rozhraním [DoVerbInPlaceActivate](#doverbinplaceactivate) před aktivací ovládacího prvku na místě.  
  
```
HRESULT OnPreVerbInPlaceActivate();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `S_OK`.  
  
### <a name="remarks"></a>Poznámky  
 Aby se zabránilo ovládacího prvku aktivace na místě, přepište tuto metodu a vrátí chybu HRESULT.  
  
##  <a name="onpreverbopen"></a>IOleObjectImpl::OnPreVerbOpen  
 Voláno rozhraním [DoVerbOpen](#doverbopen) před otevřel ovládací prvek pro úpravy v samostatném okně.  
  
```
HRESULT OnPreVerbOpen();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `S_OK`.  
  
### <a name="remarks"></a>Poznámky  
 Abyste zabránili ovládacího prvku se po otevření k úpravám v samostatném okně, přepište tuto metodu a vrátí chybu HRESULT.  
  
##  <a name="onpreverbshow"></a>IOleObjectImpl::OnPreVerbShow  
 Voláno rozhraním [DoVerbShow](#doverbshow) před ovládacího prvku provedl se viditelné.  
  
```
HRESULT OnPreVerbShow();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `S_OK`.  
  
### <a name="remarks"></a>Poznámky  
 Abyste zabránili prováděné viditelné ovládacího prvku, přepište tuto metodu a vrátí chybu HRESULT.  
  
##  <a name="onpreverbuiactivate"></a>IOleObjectImpl::OnPreVerbUIActivate  
 Voláno rozhraním [DoVerbUIActivate](#doverbuiactivate) před aktivoval uživatelské rozhraní ovládacího prvku.  
  
```
HRESULT OnPreVerbUIActivate();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `S_OK`.  
  
### <a name="remarks"></a>Poznámky  
 Abyste zabránili aktivované uživatelské rozhraní ovládacího prvku, přepište tuto metodu a vrátí chybu HRESULT.  
  
##  <a name="setclientsite"></a>IOleObjectImpl::SetClientSite  
 Informuje o jeho lokality klienta v kontejneru ovládacího prvku.  
  
```
STDMETHOD(SetClientSite)(IOleClientSite* pClientSite);
```  
  
### <a name="remarks"></a>Poznámky  
 Metoda pak vrátí `S_OK`.  
  
 V tématu [IOleObject::SetClientSite](http://msdn.microsoft.com/library/windows/desktop/ms684013) ve Windows SDK.  
  
##  <a name="setcolorscheme"></a>IOleObjectImpl::SetColorScheme  
 Doporučuje barevné schéma do ovládacího prvku aplikace, pokud existuje.  
  
```
STDMETHOD(SetColorScheme)(LOGPALETTE* /* pLogPal */);
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí **E_NOTIMPL**.  
  
### <a name="remarks"></a>Poznámky  
 V tématu [IOleObject::SetColorScheme](http://msdn.microsoft.com/library/windows/desktop/ms683971) ve Windows SDK.  
  
##  <a name="setextent"></a>IOleObjectImpl::SetExtent  
 Nastaví rozsah oblasti zobrazení ovládacího prvku.  
  
```
STDMETHOD(SetExtent)(
    DWORD dwDrawAspect,
    SIZEL* psizel);
```  
  
### <a name="remarks"></a>Poznámky  
 V opačném `SetExtent` ukládá hodnotu, na kterou odkazuje `psizel` v datový člen třídy ovládacího prvku [CComControlBase::m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent). Tato hodnota je v jednotkách HIMETRIC (0,01 milimetru na jednotku).  
  
 Pokud – datový člen třídy ovládacího prvku [CComControlBase::m_bResizeNatural](../../atl/reference/ccomcontrolbase-class.md#m_bresizenatural) je **TRUE**, `SetExtent` také ukládá hodnotu, na kterou odkazuje `psizel` v datový člen třídy ovládacího prvku [CComControlBase::m_sizeNatural](../../atl/reference/ccomcontrolbase-class.md#m_sizenatural).  
  
 Pokud – datový člen třídy ovládacího prvku [CComControlBase::m_bRecomposeOnResize](../../atl/reference/ccomcontrolbase-class.md#m_brecomposeonresize) je **TRUE**, `SetExtent` volání `SendOnDataChange` a `SendOnViewChange` upozornit všechny poradní jímky zaregistrována Poraďte držitel, že došlo ke změně velikosti ovládacího prvku.  
  
 V tématu [IOleObject::SetExtent](http://msdn.microsoft.com/library/windows/desktop/ms694330) ve Windows SDK.  
  
##  <a name="sethostnames"></a>IOleObjectImpl::SetHostNames  
 Říká ovládacímu prvku názvy aplikace kontejnerů a kontejner dokumentu.  
  
```
STDMETHOD(SetHostNames)(LPCOLESTR /* szContainerApp */, LPCOLESTR /* szContainerObj */);
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `S_OK`.  
  
### <a name="remarks"></a>Poznámky  
 V tématu [IOleObject::SetHostNames](http://msdn.microsoft.com/library/windows/desktop/ms680642) ve Windows SDK.  
  
##  <a name="setmoniker"></a>IOleObjectImpl::SetMoniker  
 Co je jeho Přezdívka říká ovládacímu prvku.  
  
```
STDMETHOD(SetMoniker)(
    DWORD /* dwWhichMoniker */,
    IMoniker** /* pmk */);
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí **E_NOTIMPL**.  
  
### <a name="remarks"></a>Poznámky  
 V tématu [IOleObject::SetMoniker](http://msdn.microsoft.com/library/windows/desktop/ms679671) ve Windows SDK.  
  
##  <a name="unadvise"></a>IOleObjectImpl::Unadvise  
 Odstraní poradní připojení uložené ve třídě ovládacího prvku `m_spOleAdviseHolder` – datový člen.  
  
```
STDMETHOD(Unadvise)(DWORD dwConnection);
```  
  
### <a name="remarks"></a>Poznámky  
 V tématu [IOleObject::Unadvise](http://msdn.microsoft.com/library/windows/desktop/ms693749) ve Windows SDK.  
  
##  <a name="update"></a>IOleObjectImpl::Update  
 Aktualizuje ovládacího prvku.  
  
```
STDMETHOD(Update)(void);
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `S_OK`.  
  
### <a name="remarks"></a>Poznámky  
 V tématu [IOleObject::Update](http://msdn.microsoft.com/library/windows/desktop/ms679699) ve Windows SDK.  
  
## <a name="see-also"></a>Viz také  
 [CComControl – třída](../../atl/reference/ccomcontrol-class.md)   
 [Rozhraní ovládací prvky ActiveX](http://msdn.microsoft.com/library/windows/desktop/ms692724)   
 [Přehled třídy](../../atl/atl-class-overview.md)
