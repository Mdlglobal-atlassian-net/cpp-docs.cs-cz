---
title: Runtimeclasstype – výčet | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::RuntimeClassType
dev_langs:
- C++
helpviewer_keywords:
- RuntimeClassType enumeration
ms.assetid: d380712d-672e-4ea9-b7c5-cf9fa7dbb770
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a3358455755ec4c00ebea85fc13fe0022c7b6697
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42595451"
---
# <a name="runtimeclasstype-enumeration"></a>RuntimeClassType – výčet

Určuje typ [RuntimeClass](../windows/runtimeclass-class.md) instanci, která je podporována.

## <a name="syntax"></a>Syntaxe

```cpp
enum RuntimeClassType;
```

## <a name="members"></a>Členové

### <a name="values"></a>Hodnoty

|Název|Popis|
|----------|-----------------|
|`ClassicCom`|Klasické třída modelu COM modulu runtime.|
|`Delegate`|Ekvivalentní `ClassicCom`.|
|`InhibitFtmBase`|Zakáže `FtmBase` podporu při `__WRL_CONFIGURATION_LEGACY__` není definován.|
|`InhibitWeakReference`|Zakáže slabou podporu odkazu.|
|`WinRt`|Třída Windows Runtime.|
|`WinRtClassicComMix`|Kombinace `WinRt` a `ClassicCom`.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** implements.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Viz také

[Microsoft::WRL – obor názvů](../windows/microsoft-wrl-namespace.md)