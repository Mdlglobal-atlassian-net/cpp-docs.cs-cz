---
title: RuntimeClassType – výčet
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::RuntimeClassType
helpviewer_keywords:
- RuntimeClassType enumeration
ms.assetid: d380712d-672e-4ea9-b7c5-cf9fa7dbb770
ms.openlocfilehash: 3b869be00cdc405569b82bdf3730f8d4ca4f3aab
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2019
ms.locfileid: "58787005"
---
# <a name="runtimeclasstype-enumeration"></a>RuntimeClassType – výčet

Určuje typ [RuntimeClass](runtimeclass-class.md) instanci, která je podporována.

## <a name="syntax"></a>Syntaxe

```cpp
enum RuntimeClassType;
```

## <a name="members"></a>Členové

### <a name="values"></a>Hodnoty

|Name|Popis|
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

[Microsoft::WRL – obor názvů](microsoft-wrl-namespace.md)