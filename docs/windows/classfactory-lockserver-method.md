---
title: ClassFactory::lockserver – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::ClassFactory::LockServer
dev_langs:
- C++
helpviewer_keywords:
- LockServer method
ms.assetid: 8d859815-956d-4f81-a5af-7cdee7e945de
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5ea76974359da2002178a342ab7d9b5523c52889
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42584135"
---
# <a name="classfactorylockserver-method"></a>ClassFactory::LockServer – metoda

Zvýší nebo sníží počet podkladových objektů, které jsou sledovány aktuální **ClassFactory –** objektu.

## <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(
   LockServer
)(BOOL fLock);
```

### <a name="parameters"></a>Parametry

*hejna*  
**Hodnota TRUE** se zvýší počet sledovaných objektů. **false** se sníží počet sledovaných objektů.

## <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě E_FAIL.

## <a name="remarks"></a>Poznámky

**ClassFactory –** uchovává informace o objekty v základní instance [modulu](../windows/module-class.md) třídy.

## <a name="requirements"></a>Požadavky

**Záhlaví:** module.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Viz také

[ClassFactory – třída](../windows/classfactory-class.md)