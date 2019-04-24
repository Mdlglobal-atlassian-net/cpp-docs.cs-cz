---
title: ActivatableClass – makra
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ActivatableClass
- ActivatableClassWithFactory
- ActivatableClassWithFactoryEx
helpviewer_keywords:
- ActivatableClassWithFactory
- ActivatableClass
- ActivatableClassWithFactoryEx
ms.assetid: 9bd64709-ec2c-4678-8c96-ea5982622bdd
ms.openlocfilehash: 7d38db9e7d3fa94c89195b6379e14692f26f7ee5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62304134"
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

*className*<br/>
Název třídy pro vytvoření.

*objekt pro vytváření*<br/>
Objekt Factory, který vytvoří instanci dané třídy.

*serverName*<br/>
Název, který určuje podmnožinu objektů pro vytváření v modulu.

## <a name="remarks"></a>Poznámky

Nepoužívejte tato makra pomocí klasického modelu COM, pokud nechcete použít `#undef` směrnice a zkontrolujte, že `__WRL_WINRT_STRICT__` odebrat definici makra.

## <a name="requirements"></a>Požadavky

**Záhlaví:** module.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Viz také:

[Module – třída](module-class.md)