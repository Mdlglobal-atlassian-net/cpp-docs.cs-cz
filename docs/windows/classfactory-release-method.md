---
title: ClassFactory::Release – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::ClassFactory::Release
dev_langs:
- C++
helpviewer_keywords:
- Release method
ms.assetid: 49da2002-f9d6-4d7f-8a65-48c20b1bf99f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e1af266d769b950324a1a4a9b8023b6b8e164038
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42606032"
---
# <a name="classfactoryrelease-method"></a>ClassFactory::Release – metoda

Sníží počet odkaz pro aktuální **ClassFactory –** objektu.

## <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD_(
   ULONG,
   Release
)();
```

## <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě HRESULT s popisem chyby.

## <a name="requirements"></a>Požadavky

**Záhlaví:** module.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Viz také

[ClassFactory – třída](../windows/classfactory-class.md)