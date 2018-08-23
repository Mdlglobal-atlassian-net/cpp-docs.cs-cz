---
title: 'Module::releasenotifier:: releasenotifier – konstruktor | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::ReleaseNotifier::ReleaseNotifier
dev_langs:
- C++
helpviewer_keywords:
- ReleaseNotifier, constructor
ms.assetid: 889a3c9a-2366-44a1-ba7d-a59c1885e7f3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f4ab2d5d03516147acda38ea2133d7445695de80
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42598785"
---
# <a name="modulereleasenotifierreleasenotifier-constructor"></a>Module::ReleaseNotifier::ReleaseNotifier – konstruktor

Inicializuje novou instanci třídy **Module::ReleaseNotifier** třídy.

## <a name="syntax"></a>Syntaxe

```cpp
ReleaseNotifier(bool release) throw();
```

### <a name="parameters"></a>Parametry

*Vydání verze*  
**true** odstranit to instance, kdy `Release` metoda je volána; **false** k odstranění této instance.

## <a name="exceptions"></a>Výjimky

## <a name="requirements"></a>Požadavky

**Záhlaví:** module.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Viz také

[Module::ReleaseNotifier – třída](../windows/module-releasenotifier-class.md)