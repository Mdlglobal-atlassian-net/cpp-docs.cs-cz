---
title: IRunnableObjectImpl – třída
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
ms.openlocfilehash: 6b1af7c21c6f5028ad6d3a228cb22650fa3cef42
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495672"
---
# <a name="irunnableobjectimpl-class"></a>IRunnableObjectImpl – třída

Tato třída implementuje `IUnknown` a poskytuje výchozí implementaci rozhraní [IRunnableObject](/windows/win32/api/objidl/nn-objidl-irunnableobject) .

> [!IMPORTANT]
>  Tato třída a její členové nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<class T>
class IRunnableObjectImpl
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Vaše třída, která je `IRunnableObjectImpl`odvozena z.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[IRunnableObjectImpl::GetRunningClass](#getrunningclass)|Vrátí CLSID běžícího ovládacího prvku. Implementace ATL nastaví identifikátor CLSID na GUID_NULL a vrátí E_UNEXPECTED.|
|[IRunnableObjectImpl::IsRunning](#isrunning)|Určuje, zda je ovládací prvek spuštěn. Implementace ATL vrátí hodnotu TRUE.|
|[IRunnableObjectImpl::LockRunning](#lockrunning)|Zamkne ovládací prvek do běžícího stavu. Implementace ATL vrací S_OK.|
|[IRunnableObjectImpl:: Run](#run)|Vynutí spuštění ovládacího prvku. Implementace ATL vrací S_OK.|
|[IRunnableObjectImpl::SetContainedObject](#setcontainedobject)|Indikuje, že ovládací prvek je vložený. Implementace ATL vrací S_OK.|

## <a name="remarks"></a>Poznámky

Rozhraní [IRunnableObject](/windows/win32/api/objidl/nn-objidl-irunnableobject) umožňuje kontejneru určit, jestli je ovládací prvek spuštěný, vynutí jeho spuštění nebo ho zamknout do běžícího stavu. Třída `IRunnableObjectImpl` poskytuje výchozí implementaci tohoto rozhraní a implementuje `IUnknown` odesláním informací do zařízení výpisu paměti v sestaveních pro ladění.

**Související články** [Kurz ATL](../../atl/active-template-library-atl-tutorial.md), [Vytvoření projektu ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`IRunnableObject`

`IRunnableObjectImpl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlctl. h

##  <a name="getrunningclass"></a>  IRunnableObjectImpl::GetRunningClass

Vrátí CLSID běžícího ovládacího prvku.

```
HRESULT GetRunningClass(LPCLSID lpClsid);
```

### <a name="return-value"></a>Návratová hodnota

Implementace knihovny ATL nastaví \* *lpClsid* na GUID_NULL a vrátí E_UNEXPECTED.

### <a name="remarks"></a>Poznámky

Viz [IRunnableObject:: GetRunningClass](/windows/win32/api/objidl/nf-objidl-irunnableobject-getrunningclass) v Windows SDK.

##  <a name="isrunning"></a>IRunnableObjectImpl:: inrunning

Určuje, zda je ovládací prvek spuštěn.

```
virtual BOOL IsRunning();
```

### <a name="return-value"></a>Návratová hodnota

Implementace ATL vrátí hodnotu TRUE.

### <a name="remarks"></a>Poznámky

Viz [IRunnableObject::-Running](/windows/win32/api/objidl/nf-objidl-irunnableobject-isrunning) v Windows SDK.

##  <a name="lockrunning"></a>  IRunnableObjectImpl::LockRunning

Zamkne ovládací prvek do běžícího stavu.

```
HRESULT LockRunning(BOOL fLock, BOOL fLastUnlockCloses);
```

### <a name="return-value"></a>Návratová hodnota

Implementace ATL vrací S_OK.

### <a name="remarks"></a>Poznámky

Viz [IRunnableObject:: LockRunning](/windows/win32/api/objidl/nf-objidl-irunnableobject-lockrunning) v Windows SDK.

##  <a name="run"></a>IRunnableObjectImpl:: Run

Vynutí spuštění ovládacího prvku.

```
HRESULT Run(LPBINDCTX lpbc);
```

### <a name="return-value"></a>Návratová hodnota

Implementace ATL vrací S_OK.

### <a name="remarks"></a>Poznámky

Viz [IRunnableObject:: Run](/windows/win32/api/objidl/nf-objidl-irunnableobject-run) in the Windows SDK.

##  <a name="setcontainedobject"></a>IRunnableObjectImpl::SetContainedObject

Indikuje, že ovládací prvek je vložený.

```
HRESULT SetContainedObject(BOOL fContained);
```

### <a name="return-value"></a>Návratová hodnota

Implementace ATL vrací S_OK.

### <a name="remarks"></a>Poznámky

Viz [IRunnableObject:: SetContainedObject](/windows/win32/api/objidl/nf-objidl-irunnableobject-setcontainedobject) v Windows SDK.

## <a name="see-also"></a>Viz také:

[CComControl – třída](../../atl/reference/ccomcontrol-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
