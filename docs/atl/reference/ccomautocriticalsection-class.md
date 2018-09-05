---
title: Ccomautocriticalsection – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComAutoCriticalSection
- ATLCORE/ATL::CComAutoCriticalSection
- ATLCORE/ATL::CComAutoCriticalSection::CComAutoCriticalSection
dev_langs:
- C++
helpviewer_keywords:
- CComAutoCriticalSection class
ms.assetid: 491a9d90-3398-4f90-88f5-fd2172a46b30
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 91d52b51de263be8f6de82a38e4d774c669dbef9
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43753581"
---
# <a name="ccomautocriticalsection-class"></a>Ccomautocriticalsection – třída

`CComAutoCriticalSection` poskytuje metody pro získání a uvolnění vlastnictví objektu kritický oddíl.

## <a name="syntax"></a>Syntaxe

```
class CComAutoCriticalSection : public CComCriticalSection
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CComAutoCriticalSection::CComAutoCriticalSection](#ccomautocriticalsection)|Konstruktor|
|[Ccomautocriticalsection –:: ~ ccomautocriticalsection –](#dtor)|Destruktor.|

## <a name="remarks"></a>Poznámky

`CComAutoCriticalSection` je podobný třídě [ccomautocriticalsection –](../../atl/reference/ccomcriticalsection-class.md), s výjimkou `CComAutoCriticalSection` automaticky inicializuje objekt kritický oddíl v konstruktoru.

Obvykle použijete `CComAutoCriticalSection` prostřednictvím `typedef` název [AutoCriticalSection](ccommultithreadmodel-class.md#autocriticalsection). Tento název se odkazuje `CComAutoCriticalSection` při [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) je používán.  

`Init` a `Term` metody ze [ccomautocriticalsection –](../../atl/reference/ccomcriticalsection-class.md) nejsou k dispozici při použití této třídy.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Ccomautocriticalsection –](../../atl/reference/ccomcriticalsection-class.md)

`CComAutoCriticalSection`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcore.h

##  <a name="ccomautocriticalsection"></a>  CComAutoCriticalSection::CComAutoCriticalSection

Konstruktor

```
CComAutoCriticalSection();
```

### <a name="remarks"></a>Poznámky

Volá funkci Win32 [InitializeCriticalSection](/windows/desktop/api/synchapi/nf-synchapi-initializecriticalsection), který inicializuje objekt kritický oddíl.

##  <a name="dtor"></a>  Ccomautocriticalsection –:: ~ ccomautocriticalsection –

Destruktor.

```
~CComAutoCriticalSection() throw();
```

### <a name="remarks"></a>Poznámky

Volání destruktoru [DeleteCriticalSection](/windows/desktop/api/synchapi/nf-synchapi-deletecriticalsection), což uvolní všechny systémové prostředky používané tímto objektem kritický oddíl.

## <a name="see-also"></a>Viz také

[Ccomfakecriticalsection – třída](../../atl/reference/ccomfakecriticalsection-class.md)   
[Přehled tříd](../../atl/atl-class-overview.md)   
[CComAutoCriticalSection – třída](../../atl/reference/ccomcriticalsection-class.md)
