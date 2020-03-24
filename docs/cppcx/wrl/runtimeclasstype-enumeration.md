---
title: RuntimeClassType – výčet
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::RuntimeClassType
helpviewer_keywords:
- RuntimeClassType enumeration
ms.assetid: d380712d-672e-4ea9-b7c5-cf9fa7dbb770
ms.openlocfilehash: 53f0172968c28762bb1305e274bbd47494cdaf4c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213574"
---
# <a name="runtimeclasstype-enumeration"></a>RuntimeClassType – výčet

Určuje typ instance [RuntimeClass](runtimeclass-class.md) , která je podporována.

## <a name="syntax"></a>Syntaxe

```cpp
enum RuntimeClassType;
```

## <a name="members"></a>Členové

### <a name="values"></a>Hodnoty

|Název|Popis|
|----------|-----------------|
|`ClassicCom`|Třída klasického běhového prostředí modelu COM.|
|`Delegate`|Ekvivalent `ClassicCom`.|
|`InhibitFtmBase`|Zakáže podporu `FtmBase`, pokud `__WRL_CONFIGURATION_LEGACY__` není definováno.|
|`InhibitWeakReference`|Zakáže podporu slabých odkazů.|
|`WinRt`|Třída prostředí Windows Runtime.|
|`WinRtClassicComMix`|Kombinace `WinRt` a `ClassicCom`.|

## <a name="requirements"></a>Požadavky

**Hlavička:** Implements. h

**Obor názvů:** Microsoft:: WRL

## <a name="see-also"></a>Viz také

[Microsoft::WRL – obor názvů](microsoft-wrl-namespace.md)
