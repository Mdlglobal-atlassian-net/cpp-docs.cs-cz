---
title: RemoveIUnknown – třída
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::RemoveIUnknown
ms.assetid: 998e711a-7d1a-44c6-a016-e6167aa40863
ms.openlocfilehash: cfcdefbb8d7cd12d2ebf99710f595fdd2fc16f76
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213613"
---
# <a name="removeiunknown-class"></a>RemoveIUnknown – třída

Podporuje infrastrukturu WRL a není určena pro použití přímo v kódu.

## <a name="syntax"></a>Syntaxe

```cpp
template <typename T>
struct RemoveIUnknown;

template <typename T>
class RemoveIUnknown : public T;
```

### <a name="parameters"></a>Parametry

*Š*<br/>
Třída.

## <a name="remarks"></a>Poznámky

Vytvoří typ, který je ekvivalentní typu `IUnknown`, ale má nevirtuální `QueryInterface`, `AddRef`a `Release` členské funkce.

Ve výchozím nastavení metody modelu COM poskytují metody Virtual `QueryInterface`, `AddRef`a `Release`. `ComPtr` ale nevyžaduje režii virtuálních metod. `RemoveIUnknown` eliminuje tato režie poskytováním privátních, nevirtuálních `QueryInterface`, `AddRef`a `Release`ch metod.

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice typedef

|Název|Popis|
|----------|-----------------|
|`ReturnType`|Synonymum pro typ, který je ekvivalentní parametru template *T* , ale má nevirtuální `IUnknown` členy.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`T`

`RemoveIUnknown`

## <a name="requirements"></a>Požadavky

**Záhlaví:** Client. h

**Obor názvů:** Microsoft:: WRL::D etails

## <a name="see-also"></a>Viz také

[Microsoft::WRL::Details – obor názvů](microsoft-wrl-details-namespace.md)
