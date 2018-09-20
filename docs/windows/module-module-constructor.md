---
title: Module::module – konstruktor | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::Module
dev_langs:
- C++
helpviewer_keywords:
- Module, constructor
ms.assetid: 5436fc74-61dc-41b6-81af-4f03177159aa
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e96e6cf984196cbca3051eec397ae06e48e2f1c0
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46406656"
---
# <a name="modulemodule-constructor"></a>Module::Module – konstruktor

Inicializuje novou instanci třídy **modulu** třídy.

## <a name="syntax"></a>Syntaxe

```cpp
Module();
```

## <a name="remarks"></a>Poznámky

Tento konstruktor je chráněn a nelze volat pomocí **nové** – klíčové slovo. Namísto toho zavolejte metodu buď [Module::getmodule – metoda](../windows/module-getmodule-method.md) nebo [Module::Create – metoda](../windows/module-create-method.md).

## <a name="requirements"></a>Požadavky

**Záhlaví:** module.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Viz také

[Module – třída](../windows/module-class.md)