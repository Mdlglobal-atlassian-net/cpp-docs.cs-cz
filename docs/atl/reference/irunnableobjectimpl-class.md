---
title: "Třída IRunnableObjectImpl | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IRunnableObjectImpl
- ATLCTL/ATL::IRunnableObjectImpl
- ATLCTL/ATL::IRunnableObjectImpl::GetRunningClass
- ATLCTL/ATL::IRunnableObjectImpl::IsRunning
- ATLCTL/ATL::IRunnableObjectImpl::LockRunning
- ATLCTL/ATL::IRunnableObjectImpl::Run
- ATLCTL/ATL::IRunnableObjectImpl::SetContainedObject
dev_langs: C++
helpviewer_keywords:
- containers, running controls
- IRunnableObjectImpl class
- IRunnableObject, ATL implementation
- controls [ATL], running
- controls [C++], container running in ATL
ms.assetid: 305c7c3b-889e-49dd-aca1-34379c1b9931
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 9be7c3924b940040c97be7a51228cb0456ee3207
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="irunnableobjectimpl-class"></a>IRunnableObjectImpl – třída
Tato třída implementuje **IUnknown** a poskytuje výchozí implementaci třídy [IRunnableObject](http://msdn.microsoft.com/library/windows/desktop/ms692783) rozhraní.  
  
> [!IMPORTANT]
>  Tato třída a její členy nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<class T>  
class IRunnableObjectImpl
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Vlastní třídy odvozené od `IRunnableObjectImpl`.  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[IRunnableObjectImpl::GetRunningClass](#getrunningclass)|Vrátí CLSID spuštěné ovládacího prvku. Implementace ATL nastaví identifikátor CLSID na `GUID_NULL` a vrátí **E_UNEXPECTED**.|  
|[IRunnableObjectImpl::IsRunning](#isrunning)|Určuje, zda je spuštěn ovládacího prvku. Implementace ATL vrátí **TRUE**.|  
|[IRunnableObjectImpl::LockRunning](#lockrunning)|Zamkne ovládacího prvku do stavu spuštěno. Implementace ATL vrátí `S_OK`.|  
|[IRunnableObjectImpl::Run](#run)|Vynutí spuštění ovládacího prvku. Implementace ATL vrátí `S_OK`.|  
|[IRunnableObjectImpl::SetContainedObject](#setcontainedobject)|Určuje, který je vložený ovládacího prvku. Implementace ATL vrátí `S_OK`.|  
  
## <a name="remarks"></a>Poznámky  
 [IRunnableObject](http://msdn.microsoft.com/library/windows/desktop/ms692783) rozhraní umožňuje kontejner lze určit, zda je spuštěn ovládacího prvku, vynutit, aby spustit nebo uzamkne ji do stavu spuštěno. Třída `IRunnableObjectImpl` poskytuje výchozí implementaci tohoto rozhraní a implementuje **IUnknown** posíláním informací o k výpisu zařízení ladění sestavení.  
  
 **Související články** [ATL – tutoriál](../../atl/active-template-library-atl-tutorial.md), [vytváření projektu knihovny ATL](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `IRunnableObject`  
  
 `IRunnableObjectImpl`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlctl.h  
  
##  <a name="getrunningclass"></a>IRunnableObjectImpl::GetRunningClass  
 Vrátí CLSID spuštěné ovládacího prvku.  
  
```
HRESULT GetRunningClass(LPCLSID lpClsid);
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Implementace sady ATL \* *lpClsid* k `GUID_NULL` a vrátí **E_UNEXPECTED**.  
  
### <a name="remarks"></a>Poznámky  
 V tématu [IRunnableObject::GetRunningClass](http://msdn.microsoft.com/library/windows/desktop/ms693734) ve Windows SDK.  
  
##  <a name="isrunning"></a>IRunnableObjectImpl::IsRunning  
 Určuje, zda je spuštěn ovládacího prvku.  
  
```
virtual BOOL IsRunning();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Implementace ATL vrátí **TRUE**.  
  
### <a name="remarks"></a>Poznámky  
 V tématu [IRunnableObject::IsRunning](http://msdn.microsoft.com/library/windows/desktop/ms678496) ve Windows SDK.  
  
##  <a name="lockrunning"></a>IRunnableObjectImpl::LockRunning  
 Zamkne ovládacího prvku do stavu spuštěno.  
  
```
HRESULT LockRunning(BOOL fLock, BOOL fLastUnlockCloses);
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Implementace ATL vrátí `S_OK`.  
  
### <a name="remarks"></a>Poznámky  
 V tématu [IRunnableObject::LockRunning](http://msdn.microsoft.com/library/windows/desktop/ms693361) ve Windows SDK.  
  
##  <a name="run"></a>IRunnableObjectImpl::Run  
 Vynutí spuštění ovládacího prvku.  
  
```
HRESULT Run(LPBINDCTX lpbc);
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Implementace ATL vrátí `S_OK`.  
  
### <a name="remarks"></a>Poznámky  
 V tématu [IRunnableObject::Run](http://msdn.microsoft.com/library/windows/desktop/ms694517) ve Windows SDK.  
  
##  <a name="setcontainedobject"></a>IRunnableObjectImpl::SetContainedObject  
 Určuje, který je vložený ovládacího prvku.  
  
```
HRESULT SetContainedObject(BOOL fContained);
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Implementace ATL vrátí `S_OK`.  
  
### <a name="remarks"></a>Poznámky  
 V tématu [IRunnableObject::SetContainedObject](http://msdn.microsoft.com/library/windows/desktop/ms693710) ve Windows SDK.  
  
## <a name="see-also"></a>Viz také  
 [CComControl – třída](../../atl/reference/ccomcontrol-class.md)   
 [Přehled třídy](../../atl/atl-class-overview.md)
