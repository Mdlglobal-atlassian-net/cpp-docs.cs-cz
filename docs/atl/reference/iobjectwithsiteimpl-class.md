---
title: Třída IObjectWithSiteImpl | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IObjectWithSiteImpl
- ATLCOM/ATL::IObjectWithSiteImpl
- ATLCOM/ATL::IObjectWithSiteImpl::GetSite
- ATLCOM/ATL::IObjectWithSiteImpl::SetChildSite
- ATLCOM/ATL::IObjectWithSiteImpl::SetSite
- ATLCOM/ATL::IObjectWithSiteImpl::m_spUnkSite
dev_langs:
- C++
helpviewer_keywords:
- IObjectWithSiteImpl class
ms.assetid: 4e1f774f-bc3d-45ee-9a1c-c3533a511588
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6c626db62a02fba70f926776ea214e664d2f7f82
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="iobjectwithsiteimpl-class"></a>IObjectWithSiteImpl – třída
Tato třída poskytuje metody, které umožní objekt pro komunikaci se svou lokalitou.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class T>
    class ATL_NO_VTABLE IObjectWithSiteImpl :
    public IObjectWithSite
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Vlastní třídy odvozené od `IObjectWithSiteImpl`.  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[IObjectWithSiteImpl::GetSite](#getsite)|Dotazuje webu pro ukazatele rozhraní.|  
|[IObjectWithSiteImpl::SetChildSite](#setchildsite)|Poskytuje objekt lokality **IUnknown** ukazatel.|  
|[IObjectWithSiteImpl::SetSite](#setsite)|Poskytuje objekt lokality **IUnknown** ukazatel.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[IObjectWithSiteImpl::m_spUnkSite](#m_spunksite)|Spravuje lokality **IUnknown** ukazatel.|  
  
## <a name="remarks"></a>Poznámky  
 [IObjectWithSite](http://msdn.microsoft.com/library/windows/desktop/ms693765) rozhraní, které umožňuje objekt pro komunikaci se svou lokalitou. Třída `IObjectWithSiteImpl` poskytuje výchozí implementaci tohoto rozhraní a implementuje **IUnknown** posíláním informací o k výpisu zařízení ladění sestavení.  
  
 `IObjectWithSiteImpl` Určuje dvě metody. První volání klienta `SetSite`, předávání lokality **IUnknown** ukazatel. Tento ukazatel je uložit do objektu a později se dají získat pomocí volání `GetSite`.  
  
 Obvykle odvozujete třídě z `IObjectWithSiteImpl` při vytváření objektu, není ovládacího prvku. Pro ovládací prvky, odvozena třídě z [IOleObjectImpl](../../atl/reference/ioleobjectimpl-class.md), který poskytuje také ukazatel lokality. Třídě není odvozen z obou `IObjectWithSiteImpl` a `IOleObjectImpl`.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `IObjectWithSite`  
  
 `IObjectWithSiteImpl`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcom  
  
##  <a name="getsite"></a>  IObjectWithSiteImpl::GetSite  
 Dotazuje webu pro ukazatel na rozhraní identifikovaný `riid`.  
  
```
STDMETHOD(GetSite)(
    REFIID riid,
    void** ppvSite);
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud lokalita podporuje toto rozhraní, vrátí se ukazatel myši prostřednictvím `ppvSite`. V opačném `ppvSite` je nastaven na **NULL**.  
  
 V tématu [IObjectWithSite::GetSite](http://msdn.microsoft.com/library/windows/desktop/ms694452) ve Windows SDK.  
  
##  <a name="m_spunksite"></a>  IObjectWithSiteImpl::m_spUnkSite  
 Spravuje lokality **IUnknown** ukazatel.  
  
```
CComPtr<IUnknown> m_spUnkSite;
```  
  
### <a name="remarks"></a>Poznámky  
 `m_spUnkSite` nejprve obdrží tento ukazatel prostřednictvím volání [setsite –](#setsite).  
  
##  <a name="setchildsite"></a>  IObjectWithSiteImpl::SetChildSite  
 Poskytuje objekt lokality **IUnknown** ukazatel.  
  
```
HRESULT SetChildSite(IUnknown* pUnkSite);
```  
  
### <a name="parameters"></a>Parametry  
 *pUnkSite*  
 [v] Ukazatel **IUnknown** ukazatel rozhraní lokality Správa tento objekt. Pokud hodnotu NULL, by měly volat objekt `IUnknown::Release` na existující webový server v tomto okamžiku objekt již zná jeho lokality.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `S_OK`.  
  
##  <a name="setsite"></a>  IObjectWithSiteImpl::SetSite  
 Poskytuje objekt lokality **IUnknown** ukazatel.  
  
```
STDMETHOD(SetSite)(IUnknown* pUnkSite);
```  
  
### <a name="remarks"></a>Poznámky  
 V tématu [IObjectWithSite::SetSite](http://msdn.microsoft.com/library/windows/desktop/ms683869) ve Windows SDK.  
  
## <a name="see-also"></a>Viz také  
 [Přehled třídy](../../atl/atl-class-overview.md)
