---
title: Comptrref::comptrref – konstruktor | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::ComPtrRef::ComPtrRef
dev_langs:
- C++
helpviewer_keywords:
- ComPtrRef, constructor
ms.assetid: ce2d2533-fef6-4b2d-b088-6f3db01df5a5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 606f9560f6d490e1d50d94dd12103713781c4f1b
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42603757"
---
# <a name="comptrrefcomptrref-constructor"></a>ComPtrRef::ComPtrRef – konstruktor

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

## <a name="syntax"></a>Syntaxe

```cpp
ComPtrRef(
   _In_opt_ T* ptr
);
```

### <a name="parameters"></a>Parametry

*ptr*  
Zadaná hodnota jiného **comptrref –** objektu.

## <a name="remarks"></a>Poznámky

Inicializuje novou instanci třídy **comptrref –** třídy z zadaný ukazatel na jiný **comptrref –** objektu.

## <a name="requirements"></a>Požadavky

**Záhlaví:** client.h

**Namespace:** Microsoft::WRL:: details –

## <a name="see-also"></a>Viz také

[ComPtrRef – třída](../windows/comptrref-class.md)  
[Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)