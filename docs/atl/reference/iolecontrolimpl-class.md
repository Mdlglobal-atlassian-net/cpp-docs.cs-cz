---
title: Třída IOleControlImpl | Microsoft Docs
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
ms.openlocfilehash: 5a54067f53e83d78f063ae5f3694460452e24b26
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="iolecontrolimpl-class"></a>IOleControlImpl – třída
Tato třída poskytuje výchozí implementaci třídy **IOleControl** rozhraní a implementuje **IUnknown**.  
  
> [!IMPORTANT]
>  Tato třída a její členy nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<class T>
class IOleControlImpl
```   
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Vlastní třídy odvozené od `IOleControlImpl`.  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[IOleControlImpl::FreezeEvents](#freezeevents)|Určuje, zda kontejner ignoruje nebo přijímá události z ovládacího prvku.|  
|[IOleControlImpl::GetControlInfo](#getcontrolinfo)|Vyplní informace o chování klávesnice ovládacího prvku. Implementace ATL vrátí **E_NOTIMPL**.|  
|[IOleControlImpl::OnAmbientPropertyChange](#onambientpropertychange)|Informuje o ovládacího prvku, že jeden nebo více vedlejším vlastnostem kontejneru se změnila. Implementace ATL vrátí `S_OK`.|  
|[IOleControlImpl::OnMnemonic](#onmnemonic)|Informuje o ovládacího prvku, že uživatel má stisknutí zadaný klávesu. Implementace ATL vrátí **E_NOTIMPL**.|  
  
## <a name="remarks"></a>Poznámky  
 Třída `IOleControlImpl` poskytuje výchozí implementaci třídy [IOleControl](http://msdn.microsoft.com/library/windows/desktop/ms694320) rozhraní a implementuje **IUnknown** posíláním informací o k výpisu zařízení ladění sestavení.  
  
 **Související články** [ATL – tutoriál](../../atl/active-template-library-atl-tutorial.md), [vytváření projektu knihovny ATL](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `IOleControl`  
  
 `IOleControlImpl`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlctl.h  
  
##  <a name="freezeevents"></a>  IOleControlImpl::FreezeEvents  
 V implementaci společnosti ATL `FreezeEvents` zvýší třída ovládacích prvků `m_nFreezeEvents` – datový člen Pokud `bFreeze` je **TRUE**a snižuje `m_nFreezeEvents` Pokud `bFreeze` je **FALSE**.  
  
```
HRESULT FreezeEvents(BOOL bFreeze);
```  
  
### <a name="remarks"></a>Poznámky  
 `FreezeEvents` Vrátí `S_OK`.  
  
 V tématu [IOleControl::FreezeEvents](http://msdn.microsoft.com/library/windows/desktop/ms678482) ve Windows SDK.  
  
##  <a name="getcontrolinfo"></a>  IOleControlImpl::GetControlInfo  
 Vyplní informace o chování klávesnice ovládacího prvku.  
  
```
HRESULT GetControlInfo(LPCONTROLINFO pCI);
```  
  
### <a name="remarks"></a>Poznámky  
 V tématu [IOleControl:GetControlInfo](http://msdn.microsoft.com/library/windows/desktop/ms693730) ve Windows SDK.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí **E_NOTIMPL**.  
  
##  <a name="onambientpropertychange"></a>  IOleControlImpl::OnAmbientPropertyChange  
 Informuje o ovládacího prvku, že jeden nebo více vedlejším vlastnostem kontejneru se změnila.  
  
```
HRESULT OnAmbientPropertyChange(DISPID dispid);
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `S_OK`.  
  
### <a name="remarks"></a>Poznámky  
 V tématu [IOleControl::OnAmbientPropertyChange](http://msdn.microsoft.com/library/windows/desktop/ms690175) ve Windows SDK.  
  
##  <a name="onmnemonic"></a>  IOleControlImpl::OnMnemonic  
 Informuje o ovládacího prvku, že uživatel má stisknutí zadaný klávesu.  
  
```
HRESULT OnMnemonic(LPMSG pMsg);
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí **E_NOTIMPL**.  
  
### <a name="remarks"></a>Poznámky  
 V tématu [IOleControl::OnMnemonic](http://msdn.microsoft.com/library/windows/desktop/ms680699) ve Windows SDK.  
  
## <a name="see-also"></a>Viz také  
 [IOleObjectImpl – třída](../../atl/reference/ioleobjectimpl-class.md)   
 [Rozhraní ovládací prvky ActiveX](http://msdn.microsoft.com/library/windows/desktop/ms692724)   
 [Přehled třídy](../../atl/atl-class-overview.md)
