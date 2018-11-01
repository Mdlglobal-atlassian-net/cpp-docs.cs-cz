---
title: Ipersiststorageimpl – třída
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
ms.openlocfilehash: 320ef54c6148adf5354a6a7b1860a84e118dc6de
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50668985"
---
# <a name="ipersiststorageimpl-class"></a>Ipersiststorageimpl – třída

Tato třída implementuje [IPersistStorage](/windows/desktop/api/objidl/nn-objidl-ipersiststorage) rozhraní.

> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <class T>
class ATL_NO_VTABLE IPersistStorageImpl : public IPersistStorage
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Vaše třída odvozena od `IPersistStorageImpl`.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[IPersistStorageImpl::GetClassID](#getclassid)|Načte identifikátor CLSID objektu.|
|[IPersistStorageImpl::HandsOffStorage](#handsoffstorage)|Nastaví objekt, který chcete uvolnit všechny objekty úložiště a HandsOff režimu. Implementace knihovny ATL vrátí hodnotu S_OK.|
|[IPersistStorageImpl::InitNew](#initnew)|Inicializuje nové úložiště.|
|[IPersistStorageImpl::IsDirty](#isdirty)|Kontroluje, zda data objektu se změnila od posledního uložení.|
|[IPersistStorageImpl::Load](#load)|Načte vlastnosti objektu ze zadané úložiště.|
|[IPersistStorageImpl::Save](#save)|Uloží do zadané úložiště vlastností objektu.|
|[IPersistStorageImpl::SaveCompleted](#savecompleted)|Upozorní objekt, který může vrátit do normálního režimu pro zápis do jeho objekt úložiště. Implementace knihovny ATL vrátí hodnotu S_OK.|

## <a name="remarks"></a>Poznámky

`IPersistStorageImpl` implementuje [IPersistStorage](/windows/desktop/api/objidl/nn-objidl-ipersiststorage) rozhraní, která umožňuje klientovi požadavek, aby objekt zatížení a uložte trvalá data pomocí úložiště.

Implementaci této třídy vyžaduje třídu `T` provést implementaci `IPersistStreamInit` rozhraní, které jsou k dispozici prostřednictvím `QueryInterface`. Obvykle to znamená, že třída `T` by měl být odvozen z [ipersiststreaminitimpl –](../../atl/reference/ipersiststreaminitimpl-class.md), zadejte položku pro `IPersistStreamInit` v [mapy modelu COM.](com-map-macros.md)a použít [mapování](property-map-macros.md) k popisu třídy trvalá data.

**Související články** [ATL – tutoriál](../../atl/active-template-library-atl-tutorial.md), [vytvoření projektu ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`IPersistStorage`

`IPersistStorageImpl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom

##  <a name="getclassid"></a>  IPersistStorageImpl::GetClassID

Načte identifikátor CLSID objektu.

```
STDMETHOD(GetClassID)(CLSID* pClassID);
```

### <a name="remarks"></a>Poznámky

Zobrazit [IPersist::GetClassID](/windows/desktop/api/objidl/nf-objidl-ipersist-getclassid) ve Windows SDK.

##  <a name="handsoffstorage"></a>  IPersistStorageImpl::HandsOffStorage

Nastaví objekt, který chcete uvolnit všechny objekty úložiště a HandsOff režimu.

```
STDMETHOD(HandsOffStorage)(void);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK.

### <a name="remarks"></a>Poznámky

Zobrazit [IPersistStorage::HandsOffStorage](/windows/desktop/api/objidl/nf-objidl-ipersiststorage-handsoffstorage) ve Windows SDK.

##  <a name="initnew"></a>  IPersistStorageImpl::InitNew

Inicializuje nové úložiště.

```
STDMETHOD(InitNew)(IStorage*);
```

### <a name="remarks"></a>Poznámky

Implementace knihovny ATL delegoval vůči [IPersistStreamInit](/windows/desktop/api/ocidl/nn-ocidl-ipersiststreaminit) rozhraní.

Zobrazit [IPersistStorage:InitNew](/windows/desktop/api/objidl/nf-objidl-ipersiststorage-initnew) ve Windows SDK.

##  <a name="isdirty"></a>  IPersistStorageImpl::IsDirty

Kontroluje, zda data objektu se změnila od posledního uložení.

```
STDMETHOD(IsDirty)(void);
```

### <a name="remarks"></a>Poznámky

Implementace knihovny ATL delegoval vůči [IPersistStreamInit](/windows/desktop/api/ocidl/nn-ocidl-ipersiststreaminit) rozhraní.

Zobrazit [IPersistStorage:IsDirty](/windows/desktop/api/objidl/nf-objidl-ipersiststorage-isdirty) ve Windows SDK.

##  <a name="load"></a>  IPersistStorageImpl::Load

Načte vlastnosti objektu ze zadané úložiště.

```
STDMETHOD(Load)(IStorage* pStorage);
```

### <a name="remarks"></a>Poznámky

Implementace knihovny ATL delegoval vůči [IPersistStreamInit](/windows/desktop/api/ocidl/nn-ocidl-ipersiststreaminit) rozhraní. `Load` datový proud s názvem "Obsah" se používá k načtení dat tohoto objektu. [Uložit](#save) metoda původně vytvoří tento datový proud.

Zobrazit [IPersistStorage:Load](/windows/desktop/api/objidl/nf-objidl-ipersiststorage-load) ve Windows SDK.

##  <a name="save"></a>  IPersistStorageImpl::Save

Uloží do zadané úložiště vlastností objektu.

```
STDMETHOD(Save)(IStorage* pStorage, BOOL fSameAsLoad);
```

### <a name="remarks"></a>Poznámky

Implementace knihovny ATL delegoval vůči [IPersistStreamInit](/windows/desktop/api/ocidl/nn-ocidl-ipersiststreaminit) rozhraní. Když `Save` je první volání vytvoří datový proud s názvem "Obsah" na zadané úložiště. Tento datový proud se pak použije v pozdější volání `Save` a ve voláních [zatížení](#load).

Zobrazit [IPersistStorage:Save](/windows/desktop/api/objidl/nf-objidl-ipersiststorage-save) ve Windows SDK.

##  <a name="savecompleted"></a>  IPersistStorageImpl::SaveCompleted

Upozorní objekt, který může vrátit do normálního režimu pro zápis do jeho objekt úložiště.

```
STDMETHOD(SaveCompleted)(IStorage*);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK.

### <a name="remarks"></a>Poznámky

Zobrazit [IPersistStorage:SaveCompleted](/windows/desktop/api/objidl/nf-objidl-ipersiststorage-savecompleted) ve Windows SDK.

## <a name="see-also"></a>Viz také

[Úložiště a datové proudy](/windows/desktop/Stg/storages-and-streams)<br/>
[IPersistStreamInitImpl – třída](../../atl/reference/ipersiststreaminitimpl-class.md)<br/>
[IPersistPropertyBagImpl – třída](../../atl/reference/ipersistpropertybagimpl-class.md)<br/>
[Přehled tříd](../../atl/atl-class-overview.md)
