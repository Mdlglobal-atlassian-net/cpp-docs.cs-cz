---
title: "Třída IPointerInactiveImpl | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IPointerInactiveImpl
- ATLCTL/ATL::IPointerInactiveImpl
- ATLCTL/ATL::IPointerInactiveImpl::GetActivationPolicy
- ATLCTL/ATL::IPointerInactiveImpl::OnInactiveMouseMove
- ATLCTL/ATL::IPointerInactiveImpl::OnInactiveSetCursor
dev_langs: C++
helpviewer_keywords:
- IPointerInactive ATL implementation
- inactive objects
- IPointerInactiveImpl class
ms.assetid: e1fe9ea6-d38a-4527-9112-eb344771e0b7
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: fe45700a941a8a59439b816124728f43e5f54f44
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="ipointerinactiveimpl-class"></a>IPointerInactiveImpl – třída
Tato třída implementuje **IUnknown** a [IPointerInactive](http://msdn.microsoft.com/library/windows/desktop/ms693712) metody rozhraní.  
  
> [!IMPORTANT]
>  Tato třída a její členy nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<class T>
class IPointerInactiveImpl
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Vlastní třídy odvozené od `IPointerInactiveImpl`.  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[IPointerInactiveImpl::GetActivationPolicy](#getactivationpolicy)|Načte aktuální zásady aktivace pro objekt. Implementace ATL vrátí **E_NOTIMPL**.|  
|[IPointerInactiveImpl::OnInactiveMouseMove](#oninactivemousemove)|Upozorní, že objekt, který se přesunul ukazatel myši nad ním, označující objekt můžete aktivovat události myši. Implementace ATL vrátí **E_NOTIMPL**.|  
|[IPointerInactiveImpl::OnInactiveSetCursor](#oninactivesetcursor)|Nastaví ukazatel myši pro objekt neaktivní. Implementace ATL vrátí **E_NOTIMPL**.|  
  
## <a name="remarks"></a>Poznámky  
 Neaktivní objekt je ten, který je jednoduše načíst nebo spuštěné. Na rozdíl od active objekt, a nemůže přijímat objekt neaktivní myši a klávesnice zpráv systému Windows. Proto neaktivní objekty využívat méně prostředků a jsou obvykle efektivnější.  
  
 [IPointerInactive](http://msdn.microsoft.com/library/windows/desktop/ms693712) rozhraní, které umožňuje objekt pro podporu minimální úroveň interakce s myší zbývající neaktivní. Tato funkce je obzvláště užitečná pro ovládací prvky.  
  
 Třída `IPointerInactiveImpl` implementuje `IPointerInactive` metody jednoduše vrácením **E_NOTIMPL**. Ale implementuje **IUnknown** posíláním informací o k výpisu zařízení ladění sestavení.  
  
 **Související články** [ATL – tutoriál](../../atl/active-template-library-atl-tutorial.md), [vytváření projektu knihovny ATL](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `IPointerInactive`  
  
 `IPointerInactiveImpl`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlctl.h  
  
##  <a name="getactivationpolicy"></a>IPointerInactiveImpl::GetActivationPolicy  
 Načte aktuální zásady aktivace pro objekt.  
  
```
HRESULT GetActivationPolicy(DWORD* pdwPolicy);
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí **E_NOTIMPL**.  
  
### <a name="remarks"></a>Poznámky  
 V tématu [IPointerInactive::GetActivationPolicy](http://msdn.microsoft.com/library/windows/desktop/ms692470) ve Windows SDK.  
  
##  <a name="oninactivemousemove"></a>IPointerInactiveImpl::OnInactiveMouseMove  
 Upozorní, že objekt, který se přesunul ukazatel myši nad ním, označující objekt můžete aktivovat události myši.  
  
```
HRESULT OnInactiveMouseMove(
    LPCRECT pRectBounds,
    long x,
    long y,
    DWORD dwMouseMsg);
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí **E_NOTIMPL**.  
  
### <a name="remarks"></a>Poznámky  
 V tématu [IPointerInactive::OnInactiveMouseMove](http://msdn.microsoft.com/library/windows/desktop/ms693374) ve Windows SDK.  
  
##  <a name="oninactivesetcursor"></a>IPointerInactiveImpl::OnInactiveSetCursor  
 Nastaví ukazatel myši pro objekt neaktivní.  
  
```
HRESULT OnInactiveSetCursor(
    LPCRECT pRectBounds,
    long x,
    long y,
    DWORD dwMouseMsg,
    BOOL fSetAlways);
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí **E_NOTIMPL**.  
  
### <a name="remarks"></a>Poznámky  
 V tématu [IPointerInactive::OnInactiveSetCursor](http://msdn.microsoft.com/library/windows/desktop/ms694336) ve Windows SDK.  
  
## <a name="see-also"></a>Viz také  
 [Přehled třídy](../../atl/atl-class-overview.md)
