---
title: Activatableclass – makra | Microsoft Docs
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
ms.openlocfilehash: aeb68deddd1cdfa9e1e869a08bfb0a1f3bb8d6ca
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33857461"
---
# <a name="activatableclass-macros"></a>ActivatableClass – makra

Naplní vnitřní mezipaměti, která obsahuje objekt factory, který můžete vytvořit instanci zadané třídy.

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
Objekt Factory, který vytvoří instanci zadané třídy.

*serverName*  
Název, který určuje podmnožinu objektů Factory v modulu.

## <a name="remarks"></a>Poznámky

Nepoužívejte tyto makra pomocí klasického modelu COM, pokud nechcete použít `#undef` – direktiva zajistit, aby **&#95; &#95;WRL_WINRT_STRICT&#95; &#95;** definici makra se odebere.

## <a name="requirements"></a>Požadavky

**Záhlaví:** module.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Viz také

[Module – třída](../windows/module-class.md)