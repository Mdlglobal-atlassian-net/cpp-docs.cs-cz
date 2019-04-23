---
title: RemoveIUnknown – třída
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::RemoveIUnknown
ms.assetid: 998e711a-7d1a-44c6-a016-e6167aa40863
ms.openlocfilehash: 3b54f6a3072d82d40db4ac698503f0939e745472
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59036770"
---
# <a name="removeiunknown-class"></a>RemoveIUnknown – třída

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

## <a name="syntax"></a>Syntaxe

```cpp
template <typename T>
struct RemoveIUnknown;

template <typename T>
class RemoveIUnknown : public T;
```

### <a name="parameters"></a>Parametry

*T*<br/>
Třída.

## <a name="remarks"></a>Poznámky

Vytvoří typ, který je ekvivalentní `IUnknown`– podle typu, ale má nevirtuální `QueryInterface`, `AddRef`, a `Release` členské funkce.

Ve výchozím nastavení, poskytují virtuální metody modelu COM `QueryInterface`, `AddRef`, a `Release` metody. Ale `ComPtr` nevyžaduje režijní náklady na virtuální metody. `RemoveIUnknown` Eliminuje režijní náklady na tento tím, že poskytuje privátní, nevirtuální `QueryInterface`, `AddRef`, a `Release` metody.

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice TypeDef

|Name|Popis|
|----------|-----------------|
|`ReturnType`|Synonymum pro typ, který se rovná parametru šablony *T* , ale má nevirtuální `IUnknown` členy.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`T`

`RemoveIUnknown`

## <a name="requirements"></a>Požadavky

**Záhlaví:** client.h

**Namespace:** Microsoft::WRL::Details

## <a name="see-also"></a>Viz také:

[Microsoft::WRL::Details – obor názvů](microsoft-wrl-details-namespace.md)