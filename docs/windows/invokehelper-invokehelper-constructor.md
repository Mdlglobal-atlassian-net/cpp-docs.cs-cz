---
title: Invokehelper::invokehelper – konstruktor | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::InvokeHelper::InvokeHelper
dev_langs:
- C++
helpviewer_keywords:
- InvokeHelper, constructor
ms.assetid: 0223c574-abc3-4fc0-99e6-38626ba79243
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1ad09a5a4794a9db8882a088f90da5046b6f7b9d
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42609237"
---
# <a name="invokehelperinvokehelper-constructor"></a>InvokeHelper::InvokeHelper – konstruktor

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

## <a name="syntax"></a>Syntaxe

```cpp
explicit InvokeHelper(
   TCallback callback
);
```

### <a name="parameters"></a>Parametry

*zpětné volání*  
Obslužné rutiny události.

## <a name="remarks"></a>Poznámky

Inicializuje novou instanci třídy **InvokeHelper** třídy.

`TCallback` Parametr šablony určuje typ obslužné rutiny události.

## <a name="requirements"></a>Požadavky

**Záhlaví:** event.h

**Namespace:** Microsoft::WRL:: details –

## <a name="see-also"></a>Viz také

[InvokeHelper – struktura](../windows/invokehelper-structure.md)  
[Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)