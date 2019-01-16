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
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2019
ms.locfileid: "54334762"
---
# <a name="runtimeclasstype-enumeration"></a>RuntimeClassType – výčet

Určuje typ [RuntimeClass](runtimeclass-class.md) instanci, která je podporována.

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

[Microsoft::WRL – obor názvů](microsoft-wrl-namespace.md)