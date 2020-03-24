---
title: InterfaceList – struktura
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::InterfaceList
helpviewer_keywords:
- InterfaceList structure
ms.assetid: 6ec3228d-eb3e-4b7e-aef1-7dcf17bdf61a
ms.openlocfilehash: 7fd06f71bc4d8097366dc0e87d7ff92c5a12a790
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213860"
---
# <a name="interfacelist-structure"></a>InterfaceList – struktura

Podporuje infrastrukturu WRL a není určena pro použití přímo v kódu.

## <a name="syntax"></a>Syntaxe

```cpp
template <typename T, typename U>
struct InterfaceList;
```

### <a name="parameters"></a>Parametry

*Š*<br/>
Název rozhraní; první rozhraní v seznamu rekurzivní.

*H*<br/>
Název rozhraní; zbývající rozhraní v seznamu rekurzivní.

## <a name="remarks"></a>Poznámky

Slouží k vytvoření rekurzivního seznamu rozhraní.

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice typedef

|Název|Popis|
|----------|-----------------|
|`FirstT`|Synonymum pro parametr šablony *T*|
|`RestT`|Synonymum pro parametr šablony *U*|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`InterfaceList`

## <a name="requirements"></a>Požadavky

**Hlavička:** Implements. h

**Obor názvů:** Microsoft:: WRL::D etails

## <a name="see-also"></a>Viz také

[Microsoft::WRL::Details – obor názvů](microsoft-wrl-details-namespace.md)
