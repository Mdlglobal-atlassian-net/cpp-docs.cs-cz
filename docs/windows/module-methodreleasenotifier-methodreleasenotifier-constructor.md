---
title: 'Module::methodreleasenotifier:: methodreleasenotifier – konstruktor | Microsoft Docs'
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
ms.openlocfilehash: 91540ca3fff03f1f0a449413c2d1ca72781c70f1
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33875224"
---
# <a name="modulemethodreleasenotifiermethodreleasenotifier-constructor"></a>Module::MethodReleaseNotifier::MethodReleaseNotifier – konstruktor
Inicializuje novou instanci třídy Module::MethodReleaseNotifier.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
MethodReleaseNotifier(  
   _In_ T* object,   
   _In_ void (T::* method)(),   
   bool release) throw() :  
            ReleaseNotifier(release), object_(object),   
            method_(method);  
```  
  
#### <a name="parameters"></a>Parametry  
 `object`  
 Objekt, jehož členská funkce je obslužné rutiny události.  
  
 `method`  
 Členská funkce parametru `object` tedy popisovač události.  
  
 `release`  
 Zadejte `true` Chcete-li povolit volání základní [modulu:: ReleaseNotifier::Release()](../windows/module-releasenotifier-release.md) metodu; jinak, zadejte `false`.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** module.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [Module::MethodReleaseNotifier – třída](../windows/module-methodreleasenotifier-class.md)