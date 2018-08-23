---
title: 'Module::genericreleasenotifier:: genericreleasenotifier – konstruktor | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::GenericReleaseNotifier::GenericReleaseNotifier
dev_langs:
- C++
helpviewer_keywords:
- GenericReleaseNotifier, constructor
ms.assetid: feb5b687-a4b0-4809-9022-8f292181b7a1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 98bcc3d3fcaf7aea3b2632cacb1ff38eedb868b8
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42612309"
---
# <a name="modulegenericreleasenotifiergenericreleasenotifier-constructor"></a>Module::GenericReleaseNotifier::GenericReleaseNotifier – konstruktor

Inicializuje novou instanci třídy **Module::GenericReleaseNotifier** třídy.

## <a name="syntax"></a>Syntaxe

```cpp
GenericReleaseNotifier(
   T callback,
   bool release
) throw() : ReleaseNotifier(release), callback_(callback);
```

### <a name="parameters"></a>Parametry

*zpětné volání*  
Výraz lambda, funktor nebo obslužná rutina události ukazatele na funkci, který lze vyvolat pomocí funkce operátoru závorky (`()`).

*Vydání verze*  
Zadejte **true** povolit volání základní [modulu:: ReleaseNotifier::Release()](../windows/module-releasenotifier-release.md) metody; v opačném případě zadejte **false**.

## <a name="requirements"></a>Požadavky

**Záhlaví:** module.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Viz také

[Module::GenericReleaseNotifier – třída](../windows/module-genericreleasenotifier-class.md)