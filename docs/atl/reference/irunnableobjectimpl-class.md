---
title: IRunnableObjectImpl Class
ms.date: 11/04/2016
f1_keywords:
- IRunnableObjectImpl
- ATLCTL/ATL::IRunnableObjectImpl
- ATLCTL/ATL::IRunnableObjectImpl::GetRunningClass
- ATLCTL/ATL::IRunnableObjectImpl::IsRunning
- ATLCTL/ATL::IRunnableObjectImpl::LockRunning
- ATLCTL/ATL::IRunnableObjectImpl::Run
- ATLCTL/ATL::IRunnableObjectImpl::SetContainedObject
helpviewer_keywords:
- containers, running controls
- IRunnableObjectImpl class
- IRunnableObject, ATL implementation
- controls [ATL], running
- controls [C++], container running in ATL
ms.assetid: 305c7c3b-889e-49dd-aca1-34379c1b9931
ms.openlocfilehash: 44b1e0ae1b72a40b45abe0650eb69a279b5a84d1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62200333"
---
# <a name="irunnableobjectimpl-class"></a>IRunnableObjectImpl Class

Tato třída implementuje `IUnknown` a poskytuje výchozí implementaci třídy [IRunnableObject](/windows/desktop/api/objidl/nn-objidl-irunnableobject) rozhraní.

> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<class T>
class IRunnableObjectImpl
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Vaše třída odvozena od `IRunnableObjectImpl`.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[IRunnableObjectImpl::GetRunningClass](#getrunningclass)|Vrátí identifikátor CLSID ovládacího prvku spuštěné. Implementace knihovny ATL nastaví identifikátor CLSID GUID_NULL a vrátí e_unexpected, je.|
|[IRunnableObjectImpl::IsRunning](#isrunning)|Určuje, zda je spuštěn ovládacího prvku. Implementace knihovny ATL vrátí hodnotu TRUE.|
|[IRunnableObjectImpl::LockRunning](#lockrunning)|Zamkne ovládacího prvku do stavu spuštěno. Implementace knihovny ATL vrátí hodnotu S_OK.|
|[IRunnableObjectImpl::Run](#run)|Vynutí spuštění ovládacího prvku. Implementace knihovny ATL vrátí hodnotu S_OK.|
|[IRunnableObjectImpl::SetContainedObject](#setcontainedobject)|Určuje, který je vložený ovládacího prvku. Implementace knihovny ATL vrátí hodnotu S_OK.|

## <a name="remarks"></a>Poznámky

[IRunnableObject](/windows/desktop/api/objidl/nn-objidl-irunnableobject) rozhraní umožňuje kontejneru, chcete-li zjistit, zda je spuštěna ovládacího prvku, vynutit jeho spuštění, nebo uzamčení do stavu spuštěno. Třída `IRunnableObjectImpl` poskytuje výchozí implementaci tohoto rozhraní a implementuje `IUnknown` posíláním informací o k výpisu paměti zařízení v ladění sestavení.

**Související články** [ATL – tutoriál](../../atl/active-template-library-atl-tutorial.md), [vytvoření projektu ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`IRunnableObject`

`IRunnableObjectImpl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlctl.h

##  <a name="getrunningclass"></a>  IRunnableObjectImpl::GetRunningClass

Vrátí identifikátor CLSID ovládacího prvku spuštěné.

```
HRESULT GetRunningClass(LPCLSID lpClsid);
```

### <a name="return-value"></a>Návratová hodnota

Implementace sady ATL \* *lpClsid* GUID_NULL a vrátí e_unexpected, je.

### <a name="remarks"></a>Poznámky

Zobrazit [IRunnableObject::GetRunningClass](/windows/desktop/api/objidl/nf-objidl-irunnableobject-getrunningclass) ve Windows SDK.

##  <a name="isrunning"></a>  IRunnableObjectImpl::IsRunning

Určuje, zda je spuštěn ovládacího prvku.

```
virtual BOOL IsRunning();
```

### <a name="return-value"></a>Návratová hodnota

Implementace knihovny ATL vrátí hodnotu TRUE.

### <a name="remarks"></a>Poznámky

Zobrazit [IRunnableObject::IsRunning](/windows/desktop/api/objidl/nf-objidl-irunnableobject-isrunning) ve Windows SDK.

##  <a name="lockrunning"></a>  IRunnableObjectImpl::LockRunning

Zamkne ovládacího prvku do stavu spuštěno.

```
HRESULT LockRunning(BOOL fLock, BOOL fLastUnlockCloses);
```

### <a name="return-value"></a>Návratová hodnota

Implementace knihovny ATL vrátí hodnotu S_OK.

### <a name="remarks"></a>Poznámky

Zobrazit [IRunnableObject::LockRunning](/windows/desktop/api/objidl/nf-objidl-irunnableobject-lockrunning) ve Windows SDK.

##  <a name="run"></a>  IRunnableObjectImpl::Run

Vynutí spuštění ovládacího prvku.

```
HRESULT Run(LPBINDCTX lpbc);
```

### <a name="return-value"></a>Návratová hodnota

Implementace knihovny ATL vrátí hodnotu S_OK.

### <a name="remarks"></a>Poznámky

Zobrazit [IRunnableObject::Run](/windows/desktop/api/objidl/nf-objidl-irunnableobject-run) ve Windows SDK.

##  <a name="setcontainedobject"></a>  IRunnableObjectImpl::SetContainedObject

Určuje, který je vložený ovládacího prvku.

```
HRESULT SetContainedObject(BOOL fContained);
```

### <a name="return-value"></a>Návratová hodnota

Implementace knihovny ATL vrátí hodnotu S_OK.

### <a name="remarks"></a>Poznámky

Zobrazit [IRunnableObject::SetContainedObject](/windows/desktop/api/objidl/nf-objidl-irunnableobject-setcontainedobject) ve Windows SDK.

## <a name="see-also"></a>Viz také:

[CComControl – třída](../../atl/reference/ccomcontrol-class.md)<br/>
[Přehled tříd](../../atl/atl-class-overview.md)
