---
title: FactoryCacheFlags – výčet
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::FactoryCacheFlags
ms.assetid: 6f54258f-0144-4264-9608-414e5905f6fb
ms.openlocfilehash: 250c8c8e7ade72bd1a9cd63f0b515774058f0723
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214003"
---
# <a name="factorycacheflags-enumeration"></a>FactoryCacheFlags – výčet

Určuje, zda jsou objekty factory ukládány do mezipaměti.

## <a name="syntax"></a>Syntaxe

```cpp
enum FactoryCacheFlags;
```

## <a name="remarks"></a>Poznámky

Ve výchozím nastavení jsou zásady ukládání do mezipaměti továrny při vytváření objektu [modulu](module-class.md) určeny jako parametr šablony [ModuleType](moduletype-enumeration.md) . Pokud chcete tuto zásadu přepsat, zadejte hodnotu **FactoryCacheFlags –** při vytváření objektu factory.

|||
|-|-|
|`FactoryCacheDefault`|Je použita zásada ukládání do mezipaměti objektu `Module`.|
|`FactoryCacheEnabled`|Povolí ukládání do mezipaměti objektu Factory bez ohledu na parametr šablony `ModuleType`, který se používá k vytvoření objektu `Module`.|
|`FactoryCacheDisabled`|Zakáže ukládání do mezipaměti objektu Factory bez ohledu na parametr šablony `ModuleType`, který se používá k vytvoření objektu `Module`.|

## <a name="requirements"></a>Požadavky

**Hlavička:** Implements. h

**Obor názvů:** Microsoft:: WRL

## <a name="see-also"></a>Viz také

[Microsoft::WRL – obor názvů](microsoft-wrl-namespace.md)
