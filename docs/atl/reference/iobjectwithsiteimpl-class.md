---
title: IObjectWithSiteImpl – třída | Dokumentace Microsoftu
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
ms.openlocfilehash: 3a9403ed1a4ba82a1e60c42ed0e57e975e73d1dd
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/06/2018
ms.locfileid: "37883785"
---
# <a name="iobjectwithsiteimpl-class"></a>IObjectWithSiteImpl – třída
Tato třída poskytuje metody umožňující objekt ke komunikaci se svou lokalitou.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class T>
    class ATL_NO_VTABLE IObjectWithSiteImpl :
    public IObjectWithSite
```  
  
#### <a name="parameters"></a>Parametry  
 *T*  
 Vaše třída odvozena od `IObjectWithSiteImpl`.  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[IObjectWithSiteImpl::GetSite](#getsite)|Dotazy webu pro ukazatel rozhraní.|  
|[IObjectWithSiteImpl::SetChildSite](#setchildsite)|Poskytuje objekt lokality `IUnknown` ukazatele.|  
|[IObjectWithSiteImpl::SetSite](#setsite)|Poskytuje objekt lokality `IUnknown` ukazatele.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[IObjectWithSiteImpl::m_spUnkSite](#m_spunksite)|Spravuje lokality `IUnknown` ukazatele.|  
  
## <a name="remarks"></a>Poznámky  
 [IObjectWithSite](http://msdn.microsoft.com/library/windows/desktop/ms693765) rozhraní umožňuje komunikaci se svou lokalitou. Třída `IObjectWithSiteImpl` poskytuje výchozí implementaci tohoto rozhraní a implementuje `IUnknown` posíláním informací o k výpisu paměti zařízení v ladění sestavení.  
  
 `IObjectWithSiteImpl` Určuje dvěma způsoby. První volání klienta `SetSite`, předávání lokality `IUnknown` ukazatele. Tento ukazatel je uložen v rámci objektu a později se dají získat pomocí volání `GetSite`.  
  
 Obvykle jsou odvozeny z vaší třídy `IObjectWithSiteImpl` při vytváření objektu, který není ovládací prvek. Pro ovládací prvky, odvodit třídu z [ioleobjectimpl –](../../atl/reference/ioleobjectimpl-class.md), která navíc poskytuje ukazatel webu. Vaše třída není odvozena od obou `IObjectWithSiteImpl` a `IOleObjectImpl`.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `IObjectWithSite`  
  
 `IObjectWithSiteImpl`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcom  
  
##  <a name="getsite"></a>  IObjectWithSiteImpl::GetSite  
 Dotazy webu pro ukazatel rozhraní identifikovaný `riid`.  
  
```
STDMETHOD(GetSite)(
    REFIID riid,
    void** ppvSite);
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud lokalita podporuje toto rozhraní, je vrácený ukazatel přes `ppvSite`. V opačném případě `ppvSite` nastaven na hodnotu NULL.  
  
 Zobrazit [IObjectWithSite::GetSite](http://msdn.microsoft.com/library/windows/desktop/ms694452) ve Windows SDK.  
  
##  <a name="m_spunksite"></a>  IObjectWithSiteImpl::m_spUnkSite  
 Spravuje lokality `IUnknown` ukazatele.  
  
```
CComPtr<IUnknown> m_spUnkSite;
```  
  
### <a name="remarks"></a>Poznámky  
 `m_spUnkSite` nejprve obdrží tento ukazatel přímo pomocí volání [setsite –](#setsite).  
  
##  <a name="setchildsite"></a>  IObjectWithSiteImpl::SetChildSite  
 Poskytuje objekt lokality `IUnknown` ukazatele.  
  
```
HRESULT SetChildSite(IUnknown* pUnkSite);
```  
  
### <a name="parameters"></a>Parametry  
 *pUnkSite*  
 [in] Ukazatel `IUnknown` ukazatel rozhraní webu správy tohoto objektu. Pokud má hodnotu NULL, objekt by měly volat `IUnknown::Release` na žádné existující lokality v tomto okamžiku objekt už zná jeho lokality.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu S_OK.  
  
##  <a name="setsite"></a>  IObjectWithSiteImpl::SetSite  
 Poskytuje objekt lokality `IUnknown` ukazatele.  
  
```
STDMETHOD(SetSite)(IUnknown* pUnkSite);
```  
  
### <a name="remarks"></a>Poznámky  
 Zobrazit [IObjectWithSite::SetSite](http://msdn.microsoft.com/library/windows/desktop/ms683869) ve Windows SDK.  
  
## <a name="see-also"></a>Viz také  
 [Přehled tříd](../../atl/atl-class-overview.md)
