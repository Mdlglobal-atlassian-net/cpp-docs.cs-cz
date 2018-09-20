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
ms.openlocfilehash: 5c97d69bbca685ca64245d5d784452029c14f73f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46393621"
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

*Název třídy*<br/>
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

## <a name="see-also"></a>Viz také

[Module – třída](../windows/module-class.md)