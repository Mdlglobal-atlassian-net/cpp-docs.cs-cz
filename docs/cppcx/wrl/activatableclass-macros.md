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
ms.openlocfilehash: 7bc3d789d6c0d304aa170d59dff23a97a67061d7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214263"
---
# <a name="activatableclass-macros"></a>ActivatableClass – makra

Naplní interní mezipaměť, která obsahuje objekt pro vytváření, který může vytvořit instanci zadané třídy.

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

*NázevTřídy*<br/>
Název třídy, která se má vytvořit

*instalací*<br/>
Objekt pro vytváření, který vytvoří instanci zadané třídy.

*serverName*<br/>
Název, který určuje podmnožinu továrn v modulu.

## <a name="remarks"></a>Poznámky

Nepoužívejte tato makra s klasickým modelem COM, pokud nepoužíváte direktivu `#undef`, abyste se ujistili, že definice makra `__WRL_WINRT_STRICT__` je odebrána.

## <a name="requirements"></a>Požadavky

**Záhlaví:** modul. h

**Obor názvů:** Microsoft:: WRL

## <a name="see-also"></a>Viz také

[Module – třída](module-class.md)
