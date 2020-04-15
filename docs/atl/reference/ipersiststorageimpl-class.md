---
title: Třída IPersistStorageImpl
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
ms.openlocfilehash: b235b190f237293932705e4d290ac963088722f3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326472"
---
# <a name="ipersiststorageimpl-class"></a>Třída IPersistStorageImpl

Tato třída implementuje rozhraní [IPersistStorage.](/windows/win32/api/objidl/nn-objidl-ipersiststorage)

> [!IMPORTANT]
> Tuto třídu a její členy nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <class T>
class ATL_NO_VTABLE IPersistStorageImpl : public IPersistStorage
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Vaše třída, odvozená z `IPersistStorageImpl`.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[ipersistStorageimpl::GetClassID](#getclassid)|Načte identifikátor CLSID objektu.|
|[iPersistStorageImpl::HandsoffStorage](#handsoffstorage)|Instruuje objekt, aby uvolnil všechny objekty úložiště a přepěl do režimu HandsOff. Implementace ATL vrátí S_OK.|
|[IPersistStorageImpl::InitNew](#initnew)|Inicializuje nové úložiště.|
|[iPersistStorageImpl::IsDirty](#isdirty)|Zkontroluje, zda se data objektu od posledního uložení změnila.|
|[iPersistStorageImpl::Načíst](#load)|Načte vlastnosti objektu ze zadaného úložiště.|
|[IPersistStorageImpl::Uložit](#save)|Uloží vlastnosti objektu do zadaného úložiště.|
|[iPersistStorageImpl::Uložitdokončeno](#savecompleted)|Upozorní objekt, který se může vrátit do normálního režimu a zapisovat do svého objektu úložiště. Implementace ATL vrátí S_OK.|

## <a name="remarks"></a>Poznámky

`IPersistStorageImpl`implementuje rozhraní [IPersistStorage,](/windows/win32/api/objidl/nn-objidl-ipersiststorage) které umožňuje klientovi požadovat, aby se objekt načetl a uložil jeho trvalá data pomocí úložiště.

Implementace této třídy `T` vyžaduje třídu zpřístupnit `IPersistStreamInit` implementaci `QueryInterface`rozhraní prostřednictvím . Obvykle to znamená, `T` že třída by měla být odvozena `IPersistStreamInit` z [IPersistStreamInitImpl](../../atl/reference/ipersiststreaminitimpl-class.md), poskytnout položku v mapě [COM](com-map-macros.md)a použít [mapu vlastností](property-map-macros.md) k popisu trvalých dat třídy.

**Související články** [ATL Výuka](../../atl/active-template-library-atl-tutorial.md), [Vytvoření projektu ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`IPersistStorage`

`IPersistStorageImpl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom.h

## <a name="ipersiststorageimplgetclassid"></a><a name="getclassid"></a>ipersistStorageimpl::GetClassID

Načte identifikátor CLSID objektu.

```
STDMETHOD(GetClassID)(CLSID* pClassID);
```

### <a name="remarks"></a>Poznámky

Viz [iPersist::GetClassID](/windows/win32/api/objidl/nf-objidl-ipersist-getclassid) v sadě Windows SDK.

## <a name="ipersiststorageimplhandsoffstorage"></a><a name="handsoffstorage"></a>iPersistStorageImpl::HandsoffStorage

Instruuje objekt, aby uvolnil všechny objekty úložiště a přepěl do režimu HandsOff.

```
STDMETHOD(HandsOffStorage)(void);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK.

### <a name="remarks"></a>Poznámky

Viz [iPersistStorage::HandsOffStorage](/windows/win32/api/objidl/nf-objidl-ipersiststorage-handsoffstorage) v sadě Windows SDK.

## <a name="ipersiststorageimplinitnew"></a><a name="initnew"></a>IPersistStorageImpl::InitNew

Inicializuje nové úložiště.

```
STDMETHOD(InitNew)(IStorage*);
```

### <a name="remarks"></a>Poznámky

Implementace KNIHOVNY ATL deleguje rozhraní [IPersistStreamInit.](/windows/win32/api/ocidl/nn-ocidl-ipersiststreaminit)

Viz [iPersistStorage:InitNew](/windows/win32/api/objidl/nf-objidl-ipersiststorage-initnew) v sadě Windows SDK.

## <a name="ipersiststorageimplisdirty"></a><a name="isdirty"></a>iPersistStorageImpl::IsDirty

Zkontroluje, zda se data objektu od posledního uložení změnila.

```
STDMETHOD(IsDirty)(void);
```

### <a name="remarks"></a>Poznámky

Implementace KNIHOVNY ATL deleguje rozhraní [IPersistStreamInit.](/windows/win32/api/ocidl/nn-ocidl-ipersiststreaminit)

Viz [IPersistStorage:IsDirty](/windows/win32/api/objidl/nf-objidl-ipersiststorage-isdirty) v sadě Windows SDK.

## <a name="ipersiststorageimplload"></a><a name="load"></a>iPersistStorageImpl::Načíst

Načte vlastnosti objektu ze zadaného úložiště.

```
STDMETHOD(Load)(IStorage* pStorage);
```

### <a name="remarks"></a>Poznámky

Implementace KNIHOVNY ATL deleguje rozhraní [IPersistStreamInit.](/windows/win32/api/ocidl/nn-ocidl-ipersiststreaminit) `Load`používá datový proud s názvem "Obsah" k načtení dat objektu. Save [Save](#save) Metoda původně vytvoří tento datový proud.

Viz [IPersistStorage:Load](/windows/win32/api/objidl/nf-objidl-ipersiststorage-load) in the Windows SDK.

## <a name="ipersiststorageimplsave"></a><a name="save"></a>IPersistStorageImpl::Uložit

Uloží vlastnosti objektu do zadaného úložiště.

```
STDMETHOD(Save)(IStorage* pStorage, BOOL fSameAsLoad);
```

### <a name="remarks"></a>Poznámky

Implementace KNIHOVNY ATL deleguje rozhraní [IPersistStreamInit.](/windows/win32/api/ocidl/nn-ocidl-ipersiststreaminit) Při `Save` prvním volání vytvoří datový proud s názvem "Obsah" na zadaném úložišti. Tento datový proud se pak `Save` používá v pozdějších voláních a volání [načíst](#load).

Viz [IPersistStorage:Uložit](/windows/win32/api/objidl/nf-objidl-ipersiststorage-save) v sadě Windows SDK.

## <a name="ipersiststorageimplsavecompleted"></a><a name="savecompleted"></a>iPersistStorageImpl::Uložitdokončeno

Upozorní objekt, který se může vrátit do normálního režimu a zapisovat do svého objektu úložiště.

```
STDMETHOD(SaveCompleted)(IStorage*);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK.

### <a name="remarks"></a>Poznámky

Viz [IPersistStorage:SaveCompleted](/windows/win32/api/objidl/nf-objidl-ipersiststorage-savecompleted) v sadě Windows SDK.

## <a name="see-also"></a>Viz také

[Úložiště a datové proudy](/windows/win32/Stg/storages-and-streams)<br/>
[Třída IPersistStreamInitImpl](../../atl/reference/ipersiststreaminitimpl-class.md)<br/>
[Třída IPersistPropertyBagImpl](../../atl/reference/ipersistpropertybagimpl-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
