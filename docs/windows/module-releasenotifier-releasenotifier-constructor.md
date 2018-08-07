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
ms.openlocfilehash: 93dca0500971f0bcfdefd017457e02bf6a033660
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/07/2018
ms.locfileid: "39608466"
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