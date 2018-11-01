---
title: RuntimeClassType – výčet
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::RuntimeClassType
helpviewer_keywords:
- RuntimeClassType enumeration
ms.assetid: d380712d-672e-4ea9-b7c5-cf9fa7dbb770
ms.openlocfilehash: 62a82d5fab9fd22e23a5244d4fda3b7f5202304c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50626808"
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