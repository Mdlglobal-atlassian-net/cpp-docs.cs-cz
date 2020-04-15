---
title: Třída IRunnableObjectImpl
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
ms.openlocfilehash: 2843c0c25a5c104ffbdff72255ac5d85cf53b1ee
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329450"
---
# <a name="irunnableobjectimpl-class"></a>Třída IRunnableObjectImpl

Tato třída `IUnknown` implementuje a poskytuje výchozí implementaci rozhraní [IRunnableObject.](/windows/win32/api/objidl/nn-objidl-irunnableobject)

> [!IMPORTANT]
> Tuto třídu a její členy nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<class T>
class IRunnableObjectImpl
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Vaše třída, odvozená z `IRunnableObjectImpl`.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[IRunnableObjectImpl::GetRunningClass](#getrunningclass)|Vrátí clsid spuštěného ovládacího prvku. Implementace ATL nastaví CLSID na GUID_NULL a vrátí E_UNEXPECTED.|
|[IRunnableObjectImpl::Jespuštěno](#isrunning)|Určuje, zda je ovládací prvek spuštěn. Implementace ATL vrátí hodnotu PRAVDA.|
|[IRunnableObjectImpl::LockRunning](#lockrunning)|Zamkne ovládací prvek do spuštěného stavu. Implementace ATL vrátí S_OK.|
|[IRunnableObjectImpl::Spustit](#run)|Vynutí spuštění ovládacího prvku. Implementace ATL vrátí S_OK.|
|[IRunnableObjectImpl::SetContainedObject](#setcontainedobject)|Označuje, že ovládací prvek je vložen. Implementace ATL vrátí S_OK.|

## <a name="remarks"></a>Poznámky

[Rozhraní IRunnableObject](/windows/win32/api/objidl/nn-objidl-irunnableobject) umožňuje kontejneru určit, pokud je spuštěn ovládací prvek, vynutit jej spustit nebo zamknout do spuštěného stavu. Třída `IRunnableObjectImpl` poskytuje výchozí implementaci tohoto rozhraní `IUnknown` a implementuje odesláním informací do zařízení s výpisem stavu paměti v sestavení ladění.

**Související články** [ATL Výuka](../../atl/active-template-library-atl-tutorial.md), [Vytvoření projektu ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`IRunnableObject`

`IRunnableObjectImpl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlctl.h

## <a name="irunnableobjectimplgetrunningclass"></a><a name="getrunningclass"></a>IRunnableObjectImpl::GetRunningClass

Vrátí clsid spuštěného ovládacího prvku.

```
HRESULT GetRunningClass(LPCLSID lpClsid);
```

### <a name="return-value"></a>Návratová hodnota

Implementace ATL \* nastaví *lpClsid* na GUID_NULL a vrátí E_UNEXPECTED.

### <a name="remarks"></a>Poznámky

Viz [IRunnableObject::GetRunningClass](/windows/win32/api/objidl/nf-objidl-irunnableobject-getrunningclass) v sadě Windows SDK.

## <a name="irunnableobjectimplisrunning"></a><a name="isrunning"></a>IRunnableObjectImpl::Jespuštěno

Určuje, zda je ovládací prvek spuštěn.

```
virtual BOOL IsRunning();
```

### <a name="return-value"></a>Návratová hodnota

Implementace ATL vrátí hodnotu PRAVDA.

### <a name="remarks"></a>Poznámky

Viz [IRunnableObject::IsRunning](/windows/win32/api/objidl/nf-objidl-irunnableobject-isrunning) v sadě Windows SDK.

## <a name="irunnableobjectimpllockrunning"></a><a name="lockrunning"></a>IRunnableObjectImpl::LockRunning

Zamkne ovládací prvek do spuštěného stavu.

```
HRESULT LockRunning(BOOL fLock, BOOL fLastUnlockCloses);
```

### <a name="return-value"></a>Návratová hodnota

Implementace ATL vrátí S_OK.

### <a name="remarks"></a>Poznámky

Viz [IRunnableObject::LockRunning](/windows/win32/api/objidl/nf-objidl-irunnableobject-lockrunning) v sadě Windows SDK.

## <a name="irunnableobjectimplrun"></a><a name="run"></a>IRunnableObjectImpl::Spustit

Vynutí spuštění ovládacího prvku.

```
HRESULT Run(LPBINDCTX lpbc);
```

### <a name="return-value"></a>Návratová hodnota

Implementace ATL vrátí S_OK.

### <a name="remarks"></a>Poznámky

Viz [IRunnableObject::Run](/windows/win32/api/objidl/nf-objidl-irunnableobject-run) in the Windows SDK.

## <a name="irunnableobjectimplsetcontainedobject"></a><a name="setcontainedobject"></a>IRunnableObjectImpl::SetContainedObject

Označuje, že ovládací prvek je vložen.

```
HRESULT SetContainedObject(BOOL fContained);
```

### <a name="return-value"></a>Návratová hodnota

Implementace ATL vrátí S_OK.

### <a name="remarks"></a>Poznámky

Viz [IRunnableObject::SetContainedObject](/windows/win32/api/objidl/nf-objidl-irunnableobject-setcontainedobject) v sadě Windows SDK.

## <a name="see-also"></a>Viz také

[Třída CComControl](../../atl/reference/ccomcontrol-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
