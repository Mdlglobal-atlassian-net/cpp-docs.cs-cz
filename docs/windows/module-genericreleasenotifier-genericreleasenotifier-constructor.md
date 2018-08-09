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
ms.openlocfilehash: 5aa78562c934c41b2ff2ab7b381f6b2612426651
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2018
ms.locfileid: "40014585"
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