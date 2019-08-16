---
title: CComAutoCriticalSection – třída
ms.date: 11/04/2016
f1_keywords:
- CComAutoCriticalSection
- ATLCORE/ATL::CComAutoCriticalSection
- ATLCORE/ATL::CComAutoCriticalSection::CComAutoCriticalSection
helpviewer_keywords:
- CComAutoCriticalSection class
ms.assetid: 491a9d90-3398-4f90-88f5-fd2172a46b30
ms.openlocfilehash: 116c550f45bf622e7620b3a6f552339b4bcc24a7
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497934"
---
# <a name="ccomautocriticalsection-class"></a>CComAutoCriticalSection – třída

`CComAutoCriticalSection`poskytuje metody pro získání a uvolnění vlastnictví objektu kritického oddílu.

## <a name="syntax"></a>Syntaxe

```
class CComAutoCriticalSection : public CComCriticalSection
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CComAutoCriticalSection::CComAutoCriticalSection](#ccomautocriticalsection)|Konstruktor|
|[CComAutoCriticalSection::~CComAutoCriticalSection](#dtor)|Destruktor.|

## <a name="remarks"></a>Poznámky

`CComAutoCriticalSection`je podobná třídě [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md), s `CComAutoCriticalSection` výjimkou automaticky inicializuje objekt kritické části v konstruktoru.

Obvykle se používá `CComAutoCriticalSection` `typedef` přes název [AutoCriticalSection](ccommultithreadmodel-class.md#autocriticalsection). Tento název odkazuje `CComAutoCriticalSection` na použití [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) .

Metody `Init` a `Term` z [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md) nejsou při použití této třídy k dispozici.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)

`CComAutoCriticalSection`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcore. h

##  <a name="ccomautocriticalsection"></a>CComAutoCriticalSection::CComAutoCriticalSection

Konstruktor

```
CComAutoCriticalSection();
```

### <a name="remarks"></a>Poznámky

Zavolá funkci Win32 [InitializeCriticalSection](/windows/win32/api/synchapi/nf-synchapi-initializecriticalsection), která inicializuje objekt kritické části.

##  <a name="dtor"></a>CComAutoCriticalSection:: ~ CComAutoCriticalSection

Destruktor.

```
~CComAutoCriticalSection() throw();
```

### <a name="remarks"></a>Poznámky

Destruktor volá [DeleteCriticalSection](/windows/win32/api/synchapi/nf-synchapi-deletecriticalsection), který uvolní všechny systémové prostředky používané objektem kritické části.

## <a name="see-also"></a>Viz také:

[CComFakeCriticalSection – třída](../../atl/reference/ccomfakecriticalsection-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)<br/>
[CComAutoCriticalSection – třída](../../atl/reference/ccomcriticalsection-class.md)
