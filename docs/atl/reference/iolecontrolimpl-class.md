---
title: Iolecontrolimpl – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IOleControlImpl
- ATLCTL/ATL::IOleControlImpl
- ATLCTL/ATL::IOleControlImpl::FreezeEvents
- ATLCTL/ATL::IOleControlImpl::GetControlInfo
- ATLCTL/ATL::IOleControlImpl::OnAmbientPropertyChange
- ATLCTL/ATL::IOleControlImpl::OnMnemonic
dev_langs:
- C++
helpviewer_keywords:
- IOleControlImpl class
ms.assetid: 5a4255ad-ede4-49ca-ba9a-07c2e919fa85
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 34bdb0af5965b300e77a02858af3708c90fa63d0
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/06/2018
ms.locfileid: "37879280"
---
# <a name="iolecontrolimpl-class"></a>Iolecontrolimpl – třída
Tato třída poskytuje výchozí implementaci třídy `IOleControl` rozhraní a implementuje `IUnknown`.  
  
> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<class T>
class IOleControlImpl
```   
  
#### <a name="parameters"></a>Parametry  
 *T*  
 Vaše třída odvozena od `IOleControlImpl`.  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[IOleControlImpl::FreezeEvents](#freezeevents)|Označuje, zda kontejner ignoruje nebo přijímá události z ovládacího prvku.|  
|[IOleControlImpl::GetControlInfo](#getcontrolinfo)|Vyplní informace o chování klávesnice ovládacího prvku. Implementace knihovny ATL vrátí E_NOTIMPL.|  
|[IOleControlImpl::OnAmbientPropertyChange](#onambientpropertychange)|Informuje o ovládací prvek, jeden nebo více vedlejším vlastnostem kontejneru se změnila. Implementace knihovny ATL vrátí hodnotu S_OK.|  
|[IOleControlImpl::OnMnemonic](#onmnemonic)|Informuje o ovládací prvek, že uživatel stiskl zadané stisk klávesy. Implementace knihovny ATL vrátí E_NOTIMPL.|  
  
## <a name="remarks"></a>Poznámky  
 Třída `IOleControlImpl` poskytuje výchozí implementaci třídy [IOleControl](http://msdn.microsoft.com/library/windows/desktop/ms694320) rozhraní a implementuje `IUnknown` posíláním informací o k výpisu paměti zařízení v ladění sestavení.  
  
 **Související články** [ATL – tutoriál](../../atl/active-template-library-atl-tutorial.md), [vytvoření projektu ATL](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `IOleControl`  
  
 `IOleControlImpl`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlctl.h  
  
##  <a name="freezeevents"></a>  IOleControlImpl::FreezeEvents  
 V implementaci ATL `FreezeEvents` zvýší třídy ovládacího prvku `m_nFreezeEvents` datový člen Pokud `bFreeze` má hodnotu TRUE a sníží `m_nFreezeEvents` Pokud `bFreeze` je FALSE.  
  
```
HRESULT FreezeEvents(BOOL bFreeze);
```  
  
### <a name="remarks"></a>Poznámky  
 `FreezeEvents` Vrátí hodnotu S_OK.  
  
 Zobrazit [: IOleControl::FreezeEvents](http://msdn.microsoft.com/library/windows/desktop/ms678482) ve Windows SDK.  
  
##  <a name="getcontrolinfo"></a>  IOleControlImpl::GetControlInfo  
 Vyplní informace o chování klávesnice ovládacího prvku.  
  
```
HRESULT GetControlInfo(LPCONTROLINFO pCI);
```  
  
### <a name="remarks"></a>Poznámky  
 Zobrazit [IOleControl:GetControlInfo](http://msdn.microsoft.com/library/windows/desktop/ms693730) ve Windows SDK.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí E_NOTIMPL.  
  
##  <a name="onambientpropertychange"></a>  IOleControlImpl::OnAmbientPropertyChange  
 Informuje o ovládací prvek, jeden nebo více vedlejším vlastnostem kontejneru se změnila.  
  
```
HRESULT OnAmbientPropertyChange(DISPID dispid);
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu S_OK.  
  
### <a name="remarks"></a>Poznámky  
 Zobrazit [IOleControl::OnAmbientPropertyChange](http://msdn.microsoft.com/library/windows/desktop/ms690175) ve Windows SDK.  
  
##  <a name="onmnemonic"></a>  IOleControlImpl::OnMnemonic  
 Informuje o ovládací prvek, že uživatel stiskl zadané stisk klávesy.  
  
```
HRESULT OnMnemonic(LPMSG pMsg);
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí E_NOTIMPL.  
  
### <a name="remarks"></a>Poznámky  
 Zobrazit [IOleControl::OnMnemonic](http://msdn.microsoft.com/library/windows/desktop/ms680699) ve Windows SDK.  
  
## <a name="see-also"></a>Viz také  
 [Ioleobjectimpl – třída](../../atl/reference/ioleobjectimpl-class.md)   
 [Rozhraní – ovládací prvky ActiveX](http://msdn.microsoft.com/library/windows/desktop/ms692724)   
 [Přehled tříd](../../atl/atl-class-overview.md)
