---
title: Asyncbase::fireprogress – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::FireProgress
dev_langs:
- C++
helpviewer_keywords:
- FireProgress method
ms.assetid: 4512bef6-0ebc-4465-9b8a-4c9dfa82084c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 91cf005e3dc1d088a5c7d0e664f67610fac28843
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42606246"
---
# <a name="asyncbasefireprogress-method"></a>AsyncBase::FireProgress – metoda

Vyvolá obslužnou rutinu události aktuální průběh.

## <a name="syntax"></a>Syntaxe

```cpp
void FireProgress(
   const typename ProgressTraits::Arg2Type arg
);
```

### <a name="parameters"></a>Parametry

*arg*  
Metoda obslužné rutiny události, která se má vyvolat.

## <a name="remarks"></a>Poznámky

`ProgressTraits` je odvozen z [argtraitshelper – struktura](../windows/argtraitshelper-structure.md).

## <a name="requirements"></a>Požadavky

**Záhlaví:** async.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Viz také

[AsyncBase – třída](../windows/asyncbase-class.md)