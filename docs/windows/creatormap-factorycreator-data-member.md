---
title: Creatormap::factorycreator – datový člen | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::CreatorMap::factoryCreator
dev_langs:
- C++
helpviewer_keywords:
- factoryCreator data member
ms.assetid: c9aac363-8f38-4cfd-9605-1e6ac74c5097
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 90367a21d76fe7fe735d1174bc9b9d40900dec78
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42600827"
---
# <a name="creatormapfactorycreator-data-member"></a>CreatorMap::factoryCreator – datový člen

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT (*factoryCreator)(
   unsigned int* currentflags,
   const CreatorMap* entry,
   REFIID iidClassFactory,
 IUnknown** factory);
```

### <a name="parameters"></a>Parametry

*currentflags*  
Jeden z [runtimeclasstype –](../windows/runtimeclasstype-enumeration.md) enumerátory.

*entry*  
Creatormap –.

*iidClassFactory*  
ID rozhraní objekt pro vytváření tříd.

*objekt pro vytváření*  
Po dokončení operace, adresa objektu pro vytváření tříd.

## <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě HRESULT, která označuje chybu.

## <a name="remarks"></a>Poznámky

Vytvoří objekt pro vytváření pro zadaný creatormap –.

## <a name="requirements"></a>Požadavky

**Záhlaví:** module.h

**Namespace:** Microsoft::WRL:: details –

## <a name="see-also"></a>Viz také

[CreatorMap – struktura](../windows/creatormap-structure.md)  
[Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)