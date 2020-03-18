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
ms.openlocfilehash: cdec425e317585abbd9730447e2c4fbb19b8250a
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79418333"
---
# <a name="boolstruct-structure"></a>BoolStruct – struktura

Podporuje infrastrukturu WRL a není určena pro použití přímo v kódu.

## <a name="syntax"></a>Syntaxe

```cpp
struct BoolStruct;
```

## <a name="remarks"></a>Poznámky

Struktura `BoolStruct` definuje, zda `ComPtr` spravuje dobu života objektu rozhraní. `BoolStruct` se interně používá pomocí operátoru [BoolType – ()](comptr-class.md#operator-microsoft-wrl-details-booltype) .

## <a name="members"></a>Členové

### <a name="public-data-members"></a>Veřejné datové členy

Název                          | Popis
----------------------------- | ------------------------------------------------------------------------------------------------------------------
[BoolStruct –:: member](#member) | Určuje, že [ComPtr](comptr-class.md) je, nebo není, spravovat životnost objektu rozhraní.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`BoolStruct`

## <a name="requirements"></a>Požadavky

**Záhlaví:** interní. h

**Obor názvů:** Microsoft:: WRL::D etails

## <a name="member"></a>BoolStruct –:: member

Podporuje infrastrukturu WRL a není určena pro použití přímo v kódu.

```cpp
int Member;
```

### <a name="remarks"></a>Poznámky

Určuje, že [ComPtr](comptr-class.md) je, nebo není, spravovat životnost objektu rozhraní.
