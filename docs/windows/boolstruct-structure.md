---
title: Boolstruct – struktura | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::BoolStruct
dev_langs:
- C++
helpviewer_keywords:
- BoolStruct structure
ms.assetid: 666eae78-e81d-4fb7-a9e4-1ba617d6d4cd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c4981c7f82fe2c544bf907ac59d6e9ca22105cbd
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42592534"
---
# <a name="boolstruct-structure"></a>BoolStruct – struktura

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

## <a name="syntax"></a>Syntaxe

```cpp
struct BoolStruct;
```

## <a name="remarks"></a>Poznámky

**Boolstruct –** struktury definuje, jestli `ComPtr` spravuje doba života objektu rozhraní. **Boolstruct –** se používá interně pomocí [BoolType()](../windows/comptr-operator-microsoft-wrl-details-booltype-operator.md) operátor.

## <a name="members"></a>Členové

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[BoolStruct::Member – datový člen](../windows/boolstruct-member-data-member.md)|Určuje, že [ComPtr](../windows/comptr-class.md) je nebo není, Správa doba života objektu rozhraní.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`BoolStruct`

## <a name="requirements"></a>Požadavky

**Záhlaví:** internal.h

**Namespace:** Microsoft::WRL:: details –

## <a name="see-also"></a>Viz také

[Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)  
[ComPtr::operator Microsoft::WRL::Details::BoolType – operátor](../windows/comptr-operator-microsoft-wrl-details-booltype-operator.md)