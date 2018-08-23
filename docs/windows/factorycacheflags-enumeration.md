---
title: Factorycacheflags – výčet | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::FactoryCacheFlags
dev_langs:
- C++
ms.assetid: 6f54258f-0144-4264-9608-414e5905f6fb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 900ab21b72434c430ef65e7d6745731bbfd42002
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42593372"
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