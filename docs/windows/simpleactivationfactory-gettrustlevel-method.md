---
title: Simpleactivationfactory::gettrustlevel – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::SimpleActivationFactory::GetTrustLevel
dev_langs:
- C++
ms.assetid: 99aa9bc9-d954-4a6f-902b-4abe00e43039
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b5a1838c153dc7a0a4def9f98e5e043e36ae9414
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42603842"
---
# <a name="simpleactivationfactorygettrustlevel-method"></a>SimpleActivationFactory::GetTrustLevel – metoda

Získá instanci třídy určené úroveň důvěryhodnosti `Base` parametr šablony třídy.

## <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(
   GetTrustLevel
)(_Out_ TrustLevel* trustLvl);
```

### <a name="parameters"></a>Parametry

*trustLvl*  
Když tato operace dokončí, úroveň důvěryhodnosti objektu aktuální třídy.

## <a name="return-value"></a>Návratová hodnota

Vždy S_OK.

## <a name="requirements"></a>Požadavky

**Záhlaví:** module.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Viz také

[SimpleActivationFactory – třída](../windows/simpleactivationfactory-class.md)