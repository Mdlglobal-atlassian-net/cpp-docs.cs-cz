---
title: BoolStruct – struktura
ms.date: 09/21/2018
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::BoolStruct
- internal/Microsoft::WRL::Details::BoolStruct::Member
helpviewer_keywords:
- Microsoft::WRL::Details::BoolStruct structure
- Microsoft::WRL::Details::BoolStruct::Member data member
ms.assetid: 666eae78-e81d-4fb7-a9e4-1ba617d6d4cd
ms.openlocfilehash: 4f2a5acf6edb824cff2121c1b6444181b5cfcf98
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371854"
---
# <a name="boolstruct-structure"></a>BoolStruct – struktura

Podporuje infrastrukturu WRL a není určen pro použití přímo z vašeho kódu.

## <a name="syntax"></a>Syntaxe

```cpp
struct BoolStruct;
```

## <a name="remarks"></a>Poznámky

Struktura `BoolStruct` definuje, `ComPtr` zda a spravuje životnost objektu rozhraní. `BoolStruct`je interně používán operátorem [BoolType().](comptr-class.md#operator-microsoft-wrl-details-booltype)

## <a name="members"></a>Členové

### <a name="public-data-members"></a>Veřejné datové členy

Name (Název)                          | Popis
----------------------------- | ------------------------------------------------------------------------------------------------------------------
[BoolStruct::Člen](#member) | Určuje, že [comPtr](comptr-class.md) spravuje nebo nespravuje životnost objektu rozhraní.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`BoolStruct`

## <a name="requirements"></a>Požadavky

**Záhlaví:** internal.h

**Obor názvů:** Microsoft::WRL::Details

## <a name="boolstructmember"></a><a name="member"></a>BoolStruct::Člen

Podporuje infrastrukturu WRL a není určen pro použití přímo z vašeho kódu.

```cpp
int Member;
```

### <a name="remarks"></a>Poznámky

Určuje, že [comPtr](comptr-class.md) spravuje nebo nespravuje životnost objektu rozhraní.
