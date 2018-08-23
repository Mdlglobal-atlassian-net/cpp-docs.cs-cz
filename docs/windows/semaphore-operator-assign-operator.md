---
title: Semaphore::Operator = – operátor | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Semaphore::operator=
dev_langs:
- C++
helpviewer_keywords:
- operator= operator
ms.assetid: ea19839f-91f0-4b00-a35b-5728fcba4981
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: fbce88be7f7b83c22964438bc4ea7a783754fb63
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42609005"
---
# <a name="semaphoreoperator-operator"></a>Semaphore::operator= – operátor

Posune Zadaný popisovač z **semafor** objektů na aktuální **semafor** objektu.

## <a name="syntax"></a>Syntaxe

```cpp
Semaphore& operator=(
   _Inout_ Semaphore&& h
);
```

### <a name="parameters"></a>Parametry

*h*  
Odkaz rvalue na **semafor** objektu.

## <a name="return-value"></a>Návratová hodnota

Odkaz na aktuální **semafor** objektu.

## <a name="requirements"></a>Požadavky

**Záhlaví:** corewrappers.h

**Namespace:** Microsoft::WRL:: wrappers –

## <a name="see-also"></a>Viz také
[Semaphore – třída](../windows/semaphore-class.md)