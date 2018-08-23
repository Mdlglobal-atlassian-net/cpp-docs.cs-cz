---
title: Activatableclass – makra | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- ActivatableClass
- ActivatableClassWithFactory
- ActivatableClassWithFactoryEx
dev_langs:
- C++
helpviewer_keywords:
- ActivatableClassWithFactory
- ActivatableClass
- ActivatableClassWithFactoryEx
ms.assetid: 9bd64709-ec2c-4678-8c96-ea5982622bdd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 398149d0d65b0dcf4c914d8f35e4c6faf209173f
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42606984"
---
# <a name="activatableclass-macros"></a>ActivatableClass – makra

Naplní interní mezipaměť, která obsahuje objekt factory, který můžete vytvořit instanci dané třídy.

## <a name="syntax"></a>Syntaxe

```cpp
ActivatableClass(
   className
);

ActivatableClassWithFactory(
   className,
   factory
);

ActivatableClassWithFactoryEx(
   className,
   factory,
   serverName
);
```

### <a name="parameters"></a>Parametry

*Název třídy*  
Název třídy pro vytvoření.

*objekt pro vytváření*  
Objekt Factory, který vytvoří instanci dané třídy.

*název_serveru*  
Název, který určuje podmnožinu objektů pro vytváření v modulu.

## <a name="remarks"></a>Poznámky

Nepoužívejte tato makra pomocí klasického modelu COM, pokud nechcete použít `#undef` směrnice a zkontrolujte, že `__WRL_WINRT_STRICT__` odebrat definici makra.

## <a name="requirements"></a>Požadavky

**Záhlaví:** module.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Viz také

[Module – třída](../windows/module-class.md)