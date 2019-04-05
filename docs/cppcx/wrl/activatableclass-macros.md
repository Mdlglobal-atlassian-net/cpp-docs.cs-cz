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
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "59037591"
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

*název_serveru*<br/>
Název, který určuje podmnožinu objektů pro vytváření v modulu.

## <a name="remarks"></a>Poznámky

Nepoužívejte tato makra pomocí klasického modelu COM, pokud nechcete použít `#undef` směrnice a zkontrolujte, že `__WRL_WINRT_STRICT__` odebrat definici makra.

## <a name="requirements"></a>Požadavky

**Záhlaví:** module.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Viz také:

[Modul – třída](module-class.md)