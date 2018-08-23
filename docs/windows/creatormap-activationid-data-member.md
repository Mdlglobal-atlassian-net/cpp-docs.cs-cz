---
title: Creatormap::activationid – datový člen | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::CreatorMap::activationId
dev_langs:
- C++
helpviewer_keywords:
- activationId data member
ms.assetid: 77518b76-6e6a-4b48-8e2e-a4c7c67769e0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: eeaaedeb4c3806af888f36e62c8fa8e54c47eb46
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42595691"
---
# <a name="creatormapactivationid-data-member"></a>CreatorMap::activationId – datový člen

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

## <a name="syntax"></a>Syntaxe

```cpp
union {
   const IID* clsid;
   const wchar_t* (*getRuntimeName)();
} activationId;
```

### <a name="parameters"></a>Parametry

*identifikátor CLSID*  
Identifikátor rozhraní.

*getRuntimeName*  
Funkce, která načte název modulu runtime Windows objektu.

## <a name="remarks"></a>Poznámky

Představuje ID objektu, který je identifikován classic ID třídy modelu COM nebo název modulu runtime Windows.

## <a name="requirements"></a>Požadavky

**Záhlaví:** module.h

**Namespace:** Microsoft::WRL:: details –

## <a name="see-also"></a>Viz také

[CreatorMap – struktura](../windows/creatormap-structure.md)  
[Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)