---
title: Třída IPersistStreamInitImpl
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
ms.openlocfilehash: 0d6ac4639ac0cfb97416ca80b7a2ec3903d7b8e6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326465"
---
# <a name="ipersiststreaminitimpl-class"></a>Třída IPersistStreamInitImpl

Tato třída `IUnknown` implementuje a poskytuje výchozí implementaci rozhraní [IPersistStreamInit.](/windows/win32/api/ocidl/nn-ocidl-ipersiststreaminit)

> [!IMPORTANT]
> Tuto třídu a její členy nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<class T>
class ATL_NO_VTABLE IPersistStreamInitImpl
   : public IPersistStreamInit
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Vaše třída, odvozená z `IPersistStreamInitImpl`.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[IPersistStreamInitImpl::GetClassID](#getclassid)|Načte identifikátor CLSID objektu.|
|[IPersistStreamInitImpl::GetSizeMax](#getsizemax)|Načte velikost datového proudu potřebnék uložení dat objektu. Implementace ATL vrátí E_NOTIMPL.|
|[IPersistStreamInitImpl::InitNew](#initnew)|Inicializuje nově vytvořený objekt.|
|[IPersistStreamInitImpl::JeDirty](#isdirty)|Zkontroluje, zda se data objektu od posledního uložení změnila.|
|[IPersistStreamInitImpl::Načíst](#load)|Načte vlastnosti objektu ze zadaného datového proudu.|
|[IPersistStreamInitImpl::Uložit](#save)|Uloží vlastnosti objektu do zadaného datového proudu.|

## <a name="remarks"></a>Poznámky

[Rozhraní IPersistStreamInit](/windows/win32/api/ocidl/nn-ocidl-ipersiststreaminit) umožňuje klientovi požadovat, aby se objekt načte a uložil jeho trvalá data do jednoho datového proudu. Třída `IPersistStreamInitImpl` poskytuje výchozí implementaci tohoto rozhraní `IUnknown` a implementuje odesláním informací do zařízení s výpisem stavu paměti v sestavení ladění.

**Související články** [ATL Výuka](../../atl/active-template-library-atl-tutorial.md), [Vytvoření projektu ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`IPersistStreamInit`

`IPersistStreamInitImpl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom.h

## <a name="ipersiststreaminitimplgetclassid"></a><a name="getclassid"></a>IPersistStreamInitImpl::GetClassID

Načte identifikátor CLSID objektu.

```
STDMETHOD(GetClassID)(CLSID* pClassID);
```

### <a name="remarks"></a>Poznámky

Viz [iPersist::GetClassID](/windows/win32/api/objidl/nf-objidl-ipersist-getclassid) v sadě Windows SDK.

## <a name="ipersiststreaminitimplgetsizemax"></a><a name="getsizemax"></a>IPersistStreamInitImpl::GetSizeMax

Načte velikost datového proudu potřebnék uložení dat objektu.

```
STDMETHOD(GetSizeMax)(ULARGE_INTEGER FAR* pcbSize);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí E_NOTIMPL.

### <a name="remarks"></a>Poznámky

Viz [iPersistStreamInit::GetSizeMax](/windows/win32/api/ocidl/nf-ocidl-ipersiststreaminit-getsizemax) v sadě Windows SDK.

## <a name="ipersiststreaminitimplinitnew"></a><a name="initnew"></a>IPersistStreamInitImpl::InitNew

Inicializuje nově vytvořený objekt.

```
STDMETHOD(InitNew)();
```

### <a name="remarks"></a>Poznámky

Viz [iPersistStreamInit::InitNew](/windows/win32/api/ocidl/nf-ocidl-ipersiststreaminit-initnew) v sadě Windows SDK.

## <a name="ipersiststreaminitimplisdirty"></a><a name="isdirty"></a>IPersistStreamInitImpl::JeDirty

Zkontroluje, zda se data objektu od posledního uložení změnila.

```
STDMETHOD(IsDirty)();
```

### <a name="remarks"></a>Poznámky

Viz [iPersistStreamInit::IsDirty](/windows/win32/api/ocidl/nf-ocidl-ipersiststreaminit-isdirty) v sadě Windows SDK.

## <a name="ipersiststreaminitimplload"></a><a name="load"></a>IPersistStreamInitImpl::Načíst

Načte vlastnosti objektu ze zadaného datového proudu.

```
STDMETHOD(Load)(LPSTREAM pStm);
```

### <a name="remarks"></a>Poznámky

Knihovna ATL používá mapu vlastností objektu k načtení těchto informací.

Viz [IPersistStreamInit::Load](/windows/win32/api/ocidl/nf-ocidl-ipersiststreaminit-load) in the Windows SDK.

## <a name="ipersiststreaminitimplsave"></a><a name="save"></a>IPersistStreamInitImpl::Uložit

Uloží vlastnosti objektu do zadaného datového proudu.

```
STDMETHOD(Save)(LPSTREAM pStm, BOOL fClearDirty);
```

### <a name="remarks"></a>Poznámky

Knihovna ATL používá k ukládání těchto informací mapu vlastností objektu.

Viz [iPersistStreamInit::Save](/windows/win32/api/ocidl/nf-ocidl-ipersiststreaminit-save) v sadě Windows SDK.

## <a name="see-also"></a>Viz také

[Úložiště a datové proudy](/windows/win32/Stg/storages-and-streams)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
