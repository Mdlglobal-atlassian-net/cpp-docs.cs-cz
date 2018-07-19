---
title: Ipointerinactiveimpl – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IPointerInactiveImpl
- ATLCTL/ATL::IPointerInactiveImpl
- ATLCTL/ATL::IPointerInactiveImpl::GetActivationPolicy
- ATLCTL/ATL::IPointerInactiveImpl::OnInactiveMouseMove
- ATLCTL/ATL::IPointerInactiveImpl::OnInactiveSetCursor
dev_langs:
- C++
helpviewer_keywords:
- IPointerInactive ATL implementation
- inactive objects
- IPointerInactiveImpl class
ms.assetid: e1fe9ea6-d38a-4527-9112-eb344771e0b7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d916d2e2f8f42a4162966a1d0ddc7de55eb6bd4b
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/06/2018
ms.locfileid: "37883577"
---
# <a name="ipointerinactiveimpl-class"></a>Ipointerinactiveimpl – třída
Tato třída implementuje `IUnknown` a [IPointerInactive](http://msdn.microsoft.com/library/windows/desktop/ms693712) metody rozhraní.  
  
> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<class T>
class IPointerInactiveImpl
```  
  
#### <a name="parameters"></a>Parametry  
 *T*  
 Vaše třída odvozena od `IPointerInactiveImpl`.  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[IPointerInactiveImpl::GetActivationPolicy](#getactivationpolicy)|Načte aktuální zásady aktivace pro objekt. Implementace knihovny ATL vrátí E_NOTIMPL.|  
|[IPointerInactiveImpl::OnInactiveMouseMove](#oninactivemousemove)|Upozorní, že objekt, který se přesunul ukazatel myši nad ním, označující objekt může vyvolat události myši. Implementace knihovny ATL vrátí E_NOTIMPL.|  
|[IPointerInactiveImpl::OnInactiveSetCursor](#oninactivesetcursor)|Nastaví ukazatel myši pro aktivní objekt. Implementace knihovny ATL vrátí E_NOTIMPL.|  
  
## <a name="remarks"></a>Poznámky  
 Neaktivním objektem je takový, který je jednoduše načíst nebo spuštěné. Na rozdíl od aktivního objektu neaktivním objektem nemůže přijímat zprávy myši a klávesnice Windows. Díky tomu se neaktivní objekty používají méně prostředků a jsou obvykle mnohem efektivnější.  
  
 [IPointerInactive](http://msdn.microsoft.com/library/windows/desktop/ms693712) rozhraní umožňuje podporu minimální úroveň interakce s myší zbývající neaktivní. Tato funkce je zvláště užitečná pro ovládací prvky.  
  
 Třída `IPointerInactiveImpl` implementuje `IPointerInactive` metody jednoduše vrácením E_NOTIMPL. Nicméně, implementuje `IUnknown` posíláním informací o k výpisu paměti zařízení v ladění sestavení.  
  
 **Související články** [ATL – tutoriál](../../atl/active-template-library-atl-tutorial.md), [vytvoření projektu ATL](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `IPointerInactive`  
  
 `IPointerInactiveImpl`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlctl.h  
  
##  <a name="getactivationpolicy"></a>  IPointerInactiveImpl::GetActivationPolicy  
 Načte aktuální zásady aktivace pro objekt.  
  
```
HRESULT GetActivationPolicy(DWORD* pdwPolicy);
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí E_NOTIMPL.  
  
### <a name="remarks"></a>Poznámky  
 Zobrazit [IPointerInactive::GetActivationPolicy](http://msdn.microsoft.com/library/windows/desktop/ms692470) ve Windows SDK.  
  
##  <a name="oninactivemousemove"></a>  IPointerInactiveImpl::OnInactiveMouseMove  
 Upozorní, že objekt, který se přesunul ukazatel myši nad ním, označující objekt může vyvolat události myši.  
  
```
HRESULT OnInactiveMouseMove(
    LPCRECT pRectBounds,
    long x,
    long y,
    DWORD dwMouseMsg);
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí E_NOTIMPL.  
  
### <a name="remarks"></a>Poznámky  
 Zobrazit [IPointerInactive::OnInactiveMouseMove](http://msdn.microsoft.com/library/windows/desktop/ms693374) ve Windows SDK.  
  
##  <a name="oninactivesetcursor"></a>  IPointerInactiveImpl::OnInactiveSetCursor  
 Nastaví ukazatel myši pro aktivní objekt.  
  
```
HRESULT OnInactiveSetCursor(
    LPCRECT pRectBounds,
    long x,
    long y,
    DWORD dwMouseMsg,
    BOOL fSetAlways);
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí E_NOTIMPL.  
  
### <a name="remarks"></a>Poznámky  
 Zobrazit [IPointerInactive::OnInactiveSetCursor](http://msdn.microsoft.com/library/windows/desktop/ms694336) ve Windows SDK.  
  
## <a name="see-also"></a>Viz také  
 [Přehled tříd](../../atl/atl-class-overview.md)
