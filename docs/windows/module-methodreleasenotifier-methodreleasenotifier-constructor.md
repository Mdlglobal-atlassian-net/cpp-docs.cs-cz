---
title: 'Module::methodreleasenotifier:: methodreleasenotifier – konstruktor | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::MethodReleaseNotifier::MethodReleaseNotifier
dev_langs:
- C++
helpviewer_keywords:
- MethodReleaseNotifier, constructor
ms.assetid: 762e2ca4-0a92-49de-9ff5-d3efa0f067c0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 01c000ee928e9394827a69acb48ef0f41478a699
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2018
ms.locfileid: "40018504"
---
# <a name="modulemethodreleasenotifiermethodreleasenotifier-constructor"></a>Module::MethodReleaseNotifier::MethodReleaseNotifier – konstruktor
Inicializuje novou instanci třídy **Module::MethodReleaseNotifier** třídy.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
MethodReleaseNotifier(  
   _In_ T* object,   
   _In_ void (T::* method)(),   
   bool release) throw() :  
            ReleaseNotifier(release), object_(object),   
            method_(method);  
```  
  
### <a name="parameters"></a>Parametry  
 *object*  
 Objekt, jehož členská funkce je obslužnou rutinu události.  
  
 *– Metoda*  
 Členská funkce parametru *objekt* , který je obslužnou rutinu události.  
  
 *Vydání verze*  
 Zadejte **true** povolit volání základní [modulu:: ReleaseNotifier::Release()](../windows/module-releasenotifier-release.md) metody; v opačném případě zadejte **false**.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** module.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [Module::MethodReleaseNotifier – třída](../windows/module-methodreleasenotifier-class.md)