---
title: "Activatableclass – makra | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ActivatableClass
- ActivatableClassWithFactory
- ActivatableClassWithFactoryEx
dev_langs: C++
helpviewer_keywords:
- ActivatableClassWithFactory
- ActivatableClass
- ActivatableClassWithFactoryEx
ms.assetid: 9bd64709-ec2c-4678-8c96-ea5982622bdd
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 6cd75d4075cfe590151f7746281640febb334ce9
ms.sourcegitcommit: ca2f94dfd015e0098a6eaf5c793ec532f1c97de1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2017
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

Nepoužívejte tyto makra pomocí klasického modelu COM, pokud nechcete použít `#undef` – direktiva zajistit, aby **&#95; &#95; WRL_WINRT_STRICT &#95; &#95;**  definici makra se odebere.

## <a name="requirements"></a>Požadavky

**Záhlaví:** module.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Viz také

[Module – třídy](../windows/module-class.md)