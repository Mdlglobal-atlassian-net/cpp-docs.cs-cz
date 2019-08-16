---
title: IPersistStorageImpl – třída
ms.date: 11/04/2016
f1_keywords:
- IPersistStorageImpl
- ATLCOM/ATL::IPersistStorageImpl
- ATLCOM/ATL::IPersistStorageImpl::GetClassID
- ATLCOM/ATL::IPersistStorageImpl::HandsOffStorage
- ATLCOM/ATL::IPersistStorageImpl::InitNew
- ATLCOM/ATL::IPersistStorageImpl::IsDirty
- ATLCOM/ATL::IPersistStorageImpl::Load
- ATLCOM/ATL::IPersistStorageImpl::Save
- ATLCOM/ATL::IPersistStorageImpl::SaveCompleted
helpviewer_keywords:
- storage, ATL
- IPersistStorageImpl class
ms.assetid: d652f02c-239c-47c7-9a50-3e9fc3014fff
ms.openlocfilehash: a5b5dd4e5be43d01f00687ed9b96a3f27abcad0f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495694"
---
# <a name="ipersiststorageimpl-class"></a>IPersistStorageImpl – třída

Tato třída implementuje rozhraní [IPersistStorage](/windows/win32/api/objidl/nn-objidl-ipersiststorage) .

> [!IMPORTANT]
>  Tato třída a její členové nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <class T>
class ATL_NO_VTABLE IPersistStorageImpl : public IPersistStorage
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Vaše třída, která je `IPersistStorageImpl`odvozena z.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[IPersistStorageImpl:: GetClassID](#getclassid)|Načte CLSID objektu.|
|[IPersistStorageImpl::HandsOffStorage](#handsoffstorage)|Vydá pokyn objektu k uvolnění všech objektů úložiště a vstupu do režimu HandsOff. Implementace ATL vrací S_OK.|
|[IPersistStorageImpl::InitNew](#initnew)|Inicializuje nové úložiště.|
|[IPersistStorageImpl::IsDirty](#isdirty)|Kontroluje, zda data objektu byla od posledního uložení změněna.|
|[IPersistStorageImpl::Load](#load)|Načte vlastnosti objektu ze zadaného úložiště.|
|[IPersistStorageImpl::Save](#save)|Uloží vlastnosti objektu do určeného úložiště.|
|[IPersistStorageImpl::SaveCompleted](#savecompleted)|Upozorní objekt, že se může vrátit do normálního režimu, který zapíše do objektu úložiště. Implementace ATL vrací S_OK.|

## <a name="remarks"></a>Poznámky

`IPersistStorageImpl`implementuje rozhraní [IPersistStorage](/windows/win32/api/objidl/nn-objidl-ipersiststorage) , které klientovi umožňuje požádat, aby se objekt načetl a ušetřil jeho trvalá data pomocí úložiště.

Implementace této třídy vyžaduje třídu `T` , aby bylo možné implementovat rozhraní, které je `IPersistStreamInit` k dispozici prostřednictvím `QueryInterface`. Obvykle to znamená, že `T` třída by měla odvozovat z [IPersistStreamInitImpl](../../atl/reference/ipersiststreaminitimpl-class.md), poskytnout `IPersistStreamInit` položku pro v [mapě modelu COM](com-map-macros.md)a použít [mapu vlastností](property-map-macros.md) k popisu trvalých dat třídy.

**Související články** [Kurz ATL](../../atl/active-template-library-atl-tutorial.md), [Vytvoření projektu ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`IPersistStorage`

`IPersistStorageImpl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom. h

##  <a name="getclassid"></a>IPersistStorageImpl:: GetClassID

Načte CLSID objektu.

```
STDMETHOD(GetClassID)(CLSID* pClassID);
```

### <a name="remarks"></a>Poznámky

Viz [IPersist:: GetClassID](/windows/win32/api/objidl/nf-objidl-ipersist-getclassid) v Windows SDK.

##  <a name="handsoffstorage"></a>IPersistStorageImpl::HandsOffStorage

Vydá pokyn objektu k uvolnění všech objektů úložiště a vstupu do režimu HandsOff.

```
STDMETHOD(HandsOffStorage)(void);
```

### <a name="return-value"></a>Návratová hodnota

Vrací hodnotu S_OK.

### <a name="remarks"></a>Poznámky

Viz [IPersistStorage:: HandsOffStorage](/windows/win32/api/objidl/nf-objidl-ipersiststorage-handsoffstorage) v Windows SDK.

##  <a name="initnew"></a>  IPersistStorageImpl::InitNew

Inicializuje nové úložiště.

```
STDMETHOD(InitNew)(IStorage*);
```

### <a name="remarks"></a>Poznámky

Implementace knihovny ATL deleguje rozhraní [IPersistStreamInit](/windows/win32/api/ocidl/nn-ocidl-ipersiststreaminit) .

Viz [IPersistStorage: InitNew](/windows/win32/api/objidl/nf-objidl-ipersiststorage-initnew) v Windows SDK.

##  <a name="isdirty"></a>  IPersistStorageImpl::IsDirty

Kontroluje, zda data objektu byla od posledního uložení změněna.

```
STDMETHOD(IsDirty)(void);
```

### <a name="remarks"></a>Poznámky

Implementace knihovny ATL deleguje rozhraní [IPersistStreamInit](/windows/win32/api/ocidl/nn-ocidl-ipersiststreaminit) .

Viz [IPersistStorage: Dirty](/windows/win32/api/objidl/nf-objidl-ipersiststorage-isdirty) v Windows SDK.

##  <a name="load"></a>IPersistStorageImpl:: Load

Načte vlastnosti objektu ze zadaného úložiště.

```
STDMETHOD(Load)(IStorage* pStorage);
```

### <a name="remarks"></a>Poznámky

Implementace knihovny ATL deleguje rozhraní [IPersistStreamInit](/windows/win32/api/ocidl/nn-ocidl-ipersiststreaminit) . `Load`k načtení dat objektu používá datový proud s názvem "obsah". Metoda [Save](#save) původně vytvořila tento datový proud.

Viz [IPersistStorage: Load](/windows/win32/api/objidl/nf-objidl-ipersiststorage-load) in Windows SDK.

##  <a name="save"></a>IPersistStorageImpl:: Save

Uloží vlastnosti objektu do určeného úložiště.

```
STDMETHOD(Save)(IStorage* pStorage, BOOL fSameAsLoad);
```

### <a name="remarks"></a>Poznámky

Implementace knihovny ATL deleguje rozhraní [IPersistStreamInit](/windows/win32/api/ocidl/nn-ocidl-ipersiststreaminit) . Při `Save` prvním volání vytvoří datový proud s názvem "obsah" v zadaném úložišti. Tento Stream se pak použije v pozdějších voláních `Save` a v voláních [metody Load](#load).

Viz [IPersistStorage: Save](/windows/win32/api/objidl/nf-objidl-ipersiststorage-save) in the Windows SDK.

##  <a name="savecompleted"></a>IPersistStorageImpl::SaveCompleted

Upozorní objekt, že se může vrátit do normálního režimu, který zapíše do objektu úložiště.

```
STDMETHOD(SaveCompleted)(IStorage*);
```

### <a name="return-value"></a>Návratová hodnota

Vrací hodnotu S_OK.

### <a name="remarks"></a>Poznámky

Viz [IPersistStorage: SaveCompleted](/windows/win32/api/objidl/nf-objidl-ipersiststorage-savecompleted) v Windows SDK.

## <a name="see-also"></a>Viz také:

[Úložiště a datové proudy](/windows/win32/Stg/storages-and-streams)<br/>
[IPersistStreamInitImpl – třída](../../atl/reference/ipersiststreaminitimpl-class.md)<br/>
[IPersistPropertyBagImpl – třída](../../atl/reference/ipersistpropertybagimpl-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
