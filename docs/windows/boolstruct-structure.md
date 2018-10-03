---
title: Boolstruct – struktura | Dokumentace Microsoftu
ms.custom: ''
ms.date: 09/21/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::BoolStruct
- internal/Microsoft::WRL::Details::BoolStruct::Member
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Details::BoolStruct structure
- Microsoft::WRL::Details::BoolStruct::Member data member
ms.assetid: 666eae78-e81d-4fb7-a9e4-1ba617d6d4cd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 74a292f2253d29730e8ee9104ea81308081c0496
ms.sourcegitcommit: 1d9bd38cacbc783fccd3884b7b92062161c91c84
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2018
ms.locfileid: "48234265"
---
# <a name="boolstruct-structure"></a>BoolStruct – struktura

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

## <a name="syntax"></a>Syntaxe

```cpp
struct BoolStruct;
```

## <a name="remarks"></a>Poznámky

`BoolStruct` Struktury definuje, jestli `ComPtr` spravuje doba života objektu rozhraní. `BoolStruct` se používá interně pomocí [BoolType()](../windows/comptr-operator-microsoft-wrl-details-booltype-operator.md) operátor.

## <a name="members"></a>Členové

### <a name="public-data-members"></a>Veřejné datové členy

Název                          | Popis
----------------------------- | ------------------------------------------------------------------------------------------------------------------
[Boolstruct::Member –](#member) | Určuje, že [ComPtr](../windows/comptr-class.md) je nebo není, Správa doba života objektu rozhraní.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`BoolStruct`

## <a name="requirements"></a>Požadavky

**Záhlaví:** internal.h

**Namespace:** Microsoft::WRL:: details –

## <a name="member"></a>Boolstruct::Member –

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

```cpp
int Member;
```

### <a name="remarks"></a>Poznámky

Určuje, že [ComPtr](../windows/comptr-class.md) je nebo není, Správa doba života objektu rozhraní.
