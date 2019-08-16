---
title: IPersistStreamInitImpl – třída
ms.date: 11/04/2016
f1_keywords:
- IPersistStreamInitImpl
- ATLCOM/ATL::IPersistStreamInitImpl
- ATLCOM/ATL::IPersistStreamInitImpl::GetClassID
- ATLCOM/ATL::IPersistStreamInitImpl::GetSizeMax
- ATLCOM/ATL::IPersistStreamInitImpl::InitNew
- ATLCOM/ATL::IPersistStreamInitImpl::IsDirty
- ATLCOM/ATL::IPersistStreamInitImpl::Load
- ATLCOM/ATL::IPersistStreamInitImpl::Save
helpviewer_keywords:
- IPersistStreamInit ATL implementation
- IPersistStreamInitImpl class
- streams, ATL
ms.assetid: ef217c3c-020f-4cf8-871e-ef68e57865b8
ms.openlocfilehash: 7a350a4349cb825795a18dd860a2482952b04dcb
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496143"
---
# <a name="ipersiststreaminitimpl-class"></a>IPersistStreamInitImpl – třída

Tato třída implementuje `IUnknown` a poskytuje výchozí implementaci rozhraní [IPersistStreamInit](/windows/win32/api/ocidl/nn-ocidl-ipersiststreaminit) .

> [!IMPORTANT]
>  Tato třída a její členové nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<class T>
class ATL_NO_VTABLE IPersistStreamInitImpl
   : public IPersistStreamInit
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Vaše třída, která je `IPersistStreamInitImpl`odvozena z.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[IPersistStreamInitImpl::GetClassID](#getclassid)|Načte CLSID objektu.|
|[IPersistStreamInitImpl::GetSizeMax](#getsizemax)|Načte velikost datového proudu potřebného pro uložení dat objektu. Implementace ATL Vrátí E_NOTIMPL.|
|[IPersistStreamInitImpl::InitNew](#initnew)|Inicializuje nově vytvořený objekt.|
|[IPersistStreamInitImpl::IsDirty](#isdirty)|Kontroluje, zda data objektu byla od posledního uložení změněna.|
|[IPersistStreamInitImpl::Load](#load)|Načte vlastnosti objektu ze zadaného datového proudu.|
|[IPersistStreamInitImpl::Save](#save)|Uloží vlastnosti objektu do zadaného datového proudu.|

## <a name="remarks"></a>Poznámky

Rozhraní [IPersistStreamInit](/windows/win32/api/ocidl/nn-ocidl-ipersiststreaminit) umožňuje klientovi požádat, aby se váš objekt načetl a uloží jeho trvalá data do jediného datového proudu. Třída `IPersistStreamInitImpl` poskytuje výchozí implementaci tohoto rozhraní a implementuje `IUnknown` odesláním informací do zařízení výpisu paměti v sestaveních pro ladění.

**Související články** [Kurz ATL](../../atl/active-template-library-atl-tutorial.md), [Vytvoření projektu ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`IPersistStreamInit`

`IPersistStreamInitImpl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom. h

##  <a name="getclassid"></a>IPersistStreamInitImpl:: GetClassID

Načte CLSID objektu.

```
STDMETHOD(GetClassID)(CLSID* pClassID);
```

### <a name="remarks"></a>Poznámky

Viz [IPersist:: GetClassID](/windows/win32/api/objidl/nf-objidl-ipersist-getclassid) v Windows SDK.

##  <a name="getsizemax"></a>IPersistStreamInitImpl::GetSizeMax

Načte velikost datového proudu potřebného pro uložení dat objektu.

```
STDMETHOD(GetSizeMax)(ULARGE_INTEGER FAR* pcbSize);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí E_NOTIMPL.

### <a name="remarks"></a>Poznámky

Viz [IPersistStreamInit:: GetSizeMax](/windows/win32/api/ocidl/nf-ocidl-ipersiststreaminit-getsizemax) v Windows SDK.

##  <a name="initnew"></a>  IPersistStreamInitImpl::InitNew

Inicializuje nově vytvořený objekt.

```
STDMETHOD(InitNew)();
```

### <a name="remarks"></a>Poznámky

Viz [IPersistStreamInit:: InitNew](/windows/win32/api/ocidl/nf-ocidl-ipersiststreaminit-initnew) v Windows SDK.

##  <a name="isdirty"></a>IPersistStreamInitImpl::-Dirty

Kontroluje, zda data objektu byla od posledního uložení změněna.

```
STDMETHOD(IsDirty)();
```

### <a name="remarks"></a>Poznámky

Viz [IPersistStreamInit::](/windows/win32/api/ocidl/nf-ocidl-ipersiststreaminit-isdirty) dedirty v Windows SDK.

##  <a name="load"></a>IPersistStreamInitImpl:: Load

Načte vlastnosti objektu ze zadaného datového proudu.

```
STDMETHOD(Load)(LPSTREAM pStm);
```

### <a name="remarks"></a>Poznámky

Knihovna ATL používá k načtení těchto informací mapu vlastností objektu.

Viz [IPersistStreamInit:: Load](/windows/win32/api/ocidl/nf-ocidl-ipersiststreaminit-load) in Windows SDK.

##  <a name="save"></a>IPersistStreamInitImpl:: Save

Uloží vlastnosti objektu do zadaného datového proudu.

```
STDMETHOD(Save)(LPSTREAM pStm, BOOL fClearDirty);
```

### <a name="remarks"></a>Poznámky

ATL používá mapu vlastností objektu k uložení těchto informací.

Viz [IPersistStreamInit:: Save](/windows/win32/api/ocidl/nf-ocidl-ipersiststreaminit-save) in Windows SDK.

## <a name="see-also"></a>Viz také:

[Úložiště a datové proudy](/windows/win32/Stg/storages-and-streams)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
