---
title: RemoveIUnknown – třída
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::RemoveIUnknown
ms.assetid: 998e711a-7d1a-44c6-a016-e6167aa40863
ms.openlocfilehash: bfe397f64650caedab1408f1f74fabd005dd98cf
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2019
ms.locfileid: "54334753"
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

|Název|Popis|
|----------|-----------------|
|`ReturnType`|Synonymum pro typ, který se rovná parametru šablony *T* , ale má nevirtuální `IUnknown` členy.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`T`

`RemoveIUnknown`

## <a name="requirements"></a>Požadavky

**Záhlaví:** client.h

**Namespace:** Microsoft::WRL::Details

## <a name="see-also"></a>Viz také

[Microsoft::WRL::Details – obor názvů](microsoft-wrl-details-namespace.md)