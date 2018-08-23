---
title: Asyncbase::continueasyncoperation – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::ContinueAsyncOperation
dev_langs:
- C++
helpviewer_keywords:
- ContinueAsyncOperation method
ms.assetid: ce38181d-2fc3-4579-b0ce-237a3c7648bc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b83d7a0bb5eadede42d2572d5ebc5a02a0fe9a0e
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42607182"
---
# <a name="asyncbasecontinueasyncoperation-method"></a>AsyncBase::ContinueAsyncOperation – metoda

Určuje, zda by měly pokračovat ve zpracování asynchronní operaci, nebo by měla zastavit.

## <a name="syntax"></a>Syntaxe

```cpp
inline bool ContinueAsyncOperation();
```

## <a name="return-value"></a>Návratová hodnota

**true** -li aktuální stav asynchronní operace *spuštění*, což znamená, že operace má pokračovat. V opačném případě **false**, což znamená, že operace by měla zastavit.

## <a name="requirements"></a>Požadavky

**Záhlaví:** async.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Viz také

[AsyncBase – třída](../windows/asyncbase-class.md)