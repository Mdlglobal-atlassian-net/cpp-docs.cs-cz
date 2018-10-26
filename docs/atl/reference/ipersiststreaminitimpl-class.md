---
title: Ipersiststreaminitimpl – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IPersistStreamInitImpl
- ATLCOM/ATL::IPersistStreamInitImpl
- ATLCOM/ATL::IPersistStreamInitImpl::GetClassID
- ATLCOM/ATL::IPersistStreamInitImpl::GetSizeMax
- ATLCOM/ATL::IPersistStreamInitImpl::InitNew
- ATLCOM/ATL::IPersistStreamInitImpl::IsDirty
- ATLCOM/ATL::IPersistStreamInitImpl::Load
- ATLCOM/ATL::IPersistStreamInitImpl::Save
dev_langs:
- C++
helpviewer_keywords:
- IPersistStreamInit ATL implementation
- IPersistStreamInitImpl class
- streams, ATL
ms.assetid: ef217c3c-020f-4cf8-871e-ef68e57865b8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0deea6b4657b4b116b79c8472724f7c9d34dade8
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50075603"
---
# <a name="ipersiststreaminitimpl-class"></a>Ipersiststreaminitimpl – třída

Tato třída implementuje `IUnknown` a poskytuje výchozí implementaci třídy [IPersistStreamInit](/windows/desktop/api/ocidl/nn-ocidl-ipersiststreaminit) rozhraní.

> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<class T>
class ATL_NO_VTABLE IPersistStreamInitImpl
   : public IPersistStreamInit
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Vaše třída odvozena od `IPersistStreamInitImpl`.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[IPersistStreamInitImpl::GetClassID](#getclassid)|Načte identifikátor CLSID objektu.|
|[IPersistStreamInitImpl::GetSizeMax](#getsizemax)|Získá velikost streamu potřebné k uložení dat tohoto objektu. Implementace knihovny ATL vrátí E_NOTIMPL.|
|[IPersistStreamInitImpl::InitNew](#initnew)|Inicializuje nově vytvořený objekt.|
|[IPersistStreamInitImpl::IsDirty](#isdirty)|Kontroluje, zda data objektu se změnila od posledního uložení.|
|[IPersistStreamInitImpl::Load](#load)|Načte vlastnosti objektu ze zadaného datového proudu.|
|[IPersistStreamInitImpl::Save](#save)|Uloží vlastností objektu do zadaného datového proudu.|

## <a name="remarks"></a>Poznámky

[IPersistStreamInit](/windows/desktop/api/ocidl/nn-ocidl-ipersiststreaminit) rozhraní umožňuje klientovi vyžadovat, aby váš objekt načte a uloží jeho trvalá data do jednoho datového proudu. Třída `IPersistStreamInitImpl` poskytuje výchozí implementaci tohoto rozhraní a implementuje `IUnknown` posíláním informací o k výpisu paměti zařízení v ladění sestavení.

**Související články** [ATL – tutoriál](../../atl/active-template-library-atl-tutorial.md), [vytvoření projektu ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`IPersistStreamInit`

`IPersistStreamInitImpl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom

##  <a name="getclassid"></a>  IPersistStreamInitImpl::GetClassID

Načte identifikátor CLSID objektu.

```
STDMETHOD(GetClassID)(CLSID* pClassID);
```

### <a name="remarks"></a>Poznámky

Zobrazit [IPersist::GetClassID](/windows/desktop/api/objidl/nf-objidl-ipersist-getclassid) ve Windows SDK.

##  <a name="getsizemax"></a>  IPersistStreamInitImpl::GetSizeMax

Získá velikost streamu potřebné k uložení dat tohoto objektu.

```
STDMETHOD(GetSizeMax)(ULARGE_INTEGER FAR* pcbSize);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí E_NOTIMPL.

### <a name="remarks"></a>Poznámky

Zobrazit [IPersistStreamInit::GetSizeMax](/windows/desktop/api/ocidl/nf-ocidl-ipersiststreaminit-getsizemax) ve Windows SDK.

##  <a name="initnew"></a>  IPersistStreamInitImpl::InitNew

Inicializuje nově vytvořený objekt.

```
STDMETHOD(InitNew)();
```

### <a name="remarks"></a>Poznámky

Zobrazit [IPersistStreamInit::InitNew](/windows/desktop/api/ocidl/nf-ocidl-ipersiststreaminit-initnew) ve Windows SDK.

##  <a name="isdirty"></a>  IPersistStreamInitImpl::IsDirty

Kontroluje, zda data objektu se změnila od posledního uložení.

```
STDMETHOD(IsDirty)();
```

### <a name="remarks"></a>Poznámky

Zobrazit [IPersistStreamInit::IsDirty](/windows/desktop/api/ocidl/nf-ocidl-ipersiststreaminit-isdirty) ve Windows SDK.

##  <a name="load"></a>  IPersistStreamInitImpl::Load

Načte vlastnosti objektu ze zadaného datového proudu.

```
STDMETHOD(Load)(LPSTREAM pStm);
```

### <a name="remarks"></a>Poznámky

Mapy vlastností objektu ATL používá pro načtení těchto informací.

Zobrazit [IPersistStreamInit::Load](/windows/desktop/api/ocidl/nf-ocidl-ipersiststreaminit-load) ve Windows SDK.

##  <a name="save"></a>  IPersistStreamInitImpl::Save

Uloží vlastností objektu do zadaného datového proudu.

```
STDMETHOD(Save)(LPSTREAM pStm, BOOL fClearDirty);
```

### <a name="remarks"></a>Poznámky

Mapy vlastností objektu ATL používá k ukládání příslušných informací.

Zobrazit [IPersistStreamInit::Save](/windows/desktop/api/ocidl/nf-ocidl-ipersiststreaminit-save) ve Windows SDK.

## <a name="see-also"></a>Viz také

[Úložiště a datové proudy](/windows/desktop/Stg/storages-and-streams)<br/>
[Přehled tříd](../../atl/atl-class-overview.md)
