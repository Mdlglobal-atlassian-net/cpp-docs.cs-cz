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
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62398768"
---
# <a name="boolstruct-structure"></a>BoolStruct – struktura

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

## <a name="syntax"></a>Syntaxe

```cpp
struct BoolStruct;
```

## <a name="remarks"></a>Poznámky

`BoolStruct` Struktury definuje, jestli `ComPtr` spravuje doba života objektu rozhraní. `BoolStruct` se používá interně pomocí [BoolType()](comptr-class.md#operator-microsoft-wrl-details-booltype) operátor.

## <a name="members"></a>Členové

### <a name="public-data-members"></a>Veřejné datové členy

Název                          | Popis
----------------------------- | ------------------------------------------------------------------------------------------------------------------
[Boolstruct::Member –](#member) | Určuje, že [ComPtr](comptr-class.md) je nebo není, Správa doba života objektu rozhraní.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`BoolStruct`

## <a name="requirements"></a>Požadavky

**Záhlaví:** internal.h

**Namespace:** Microsoft::WRL::Details

## <a name="member"></a>Boolstruct::Member –

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

```cpp
int Member;
```

### <a name="remarks"></a>Poznámky

Určuje, že [ComPtr](comptr-class.md) je nebo není, Správa doba života objektu rozhraní.
