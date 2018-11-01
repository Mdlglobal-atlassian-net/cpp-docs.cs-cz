---
title: FactoryCacheFlags – výčet
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::FactoryCacheFlags
ms.assetid: 6f54258f-0144-4264-9608-414e5905f6fb
ms.openlocfilehash: 8320563991981f7a49d4775a2bad9c487124d907
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50595647"
---
# <a name="factorycacheflags-enumeration"></a>FactoryCacheFlags – výčet

Určuje, zda jsou uložené v mezipaměti objekt pro vytváření objektů.

## <a name="syntax"></a>Syntaxe

```cpp
enum FactoryCacheFlags;
```

## <a name="remarks"></a>Poznámky

Ve výchozím nastavení, je zadán objekt pro vytváření zásady ukládání do mezipaměti, jako [ModuleType](../windows/moduletype-enumeration.md) parametru šablony při vytváření [modulu](../windows/module-class.md) objektu. Chcete-li přepsat tyto zásady, zadejte **factorycacheflags –** hodnotu při vytváření objektu factory.

|||
|-|-|
|`FactoryCacheDefault`|Zásady ukládání do mezipaměti `Module` objekt se používá.|
|`FactoryCacheEnabled`|Nastaví objekt pro vytváření, ukládání do mezipaměti bez ohledu na to `ModuleType` parametr šablony, který se používá k vytvoření `Module` objektu.|
|`FactoryCacheDisabled`|Zakáže ukládání do mezipaměti objekt pro vytváření bez ohledu na to `ModuleType` parametr šablony, který se používá k vytvoření `Module` objektu.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** implements.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Viz také

[Microsoft::WRL – obor názvů](../windows/microsoft-wrl-namespace.md)