---
title: InspectableClass – makro | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::InspectableClass
dev_langs:
- C++
ms.assetid: ff390b26-58cc-424f-87ac-1fe3cc692b59
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a20815972f595a15097a057537d6cb5cdca4fb4b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46408326"
---
# <a name="inspectableclass-macro"></a>InspectableClass – makro

Nastaví runtime název a vztah důvěryhodnosti na úrovni třídy.

## <a name="syntax"></a>Syntaxe

```cpp
InspectableClass(
   runtimeClassName,
   trustLevel)  
```

### <a name="parameters"></a>Parametry

*runtimeClassName*<br/>
Úplný textový název třídy runtime.

*trustLevel*<br/>
Jeden z [TrustLevel](https://msdn.microsoft.com/library/br224625.aspx) hodnot výčtu.

## <a name="remarks"></a>Poznámky

**InspectableClass** – makro jde použít jenom s typy prostředí Windows Runtime.

## <a name="requirements"></a>Požadavky

**Záhlaví:** implements.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Viz také

[RuntimeClass – třída](../windows/runtimeclass-class.md)