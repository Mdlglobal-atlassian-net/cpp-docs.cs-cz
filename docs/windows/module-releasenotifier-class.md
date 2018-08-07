---
title: Module::releasenotifier – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::ReleaseNotifier
dev_langs:
- C++
helpviewer_keywords:
- ReleaseNotifier class
ms.assetid: 17249cd1-4d88-42e3-8146-da9e942d12bd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1deeb3076d3f1bfc2243ec333f258f543a37fceb
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/07/2018
ms.locfileid: "39608388"
---
# <a name="modulereleasenotifier-class"></a>Module::ReleaseNotifier – třída
Vyvolá obslužnou rutinu události po vydání poslední objekt v modulu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class ReleaseNotifier;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[Module::ReleaseNotifier::~ReleaseNotifier – destruktor](../windows/module-releasenotifier-tilde-releasenotifier-destructor.md)|Zruší inicializaci aktuální instance **Module::ReleaseNotifier** třídy.|  
|[Module::ReleaseNotifier::ReleaseNotifier – konstruktor](../windows/module-releasenotifier-releasenotifier-constructor.md)|Inicializuje novou instanci třídy **Module::ReleaseNotifier** třídy.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[Module::ReleaseNotifier::Invoke – metoda](../windows/module-releasenotifier-invoke-method.md)|Při implementaci, volá obslužná rutina události po vydání poslední objekt v modulu.|  
|[Module::ReleaseNotifier::Release](../windows/module-releasenotifier-release.md)|Odstraní aktuální **Module::ReleaseNotifier** objektu, pokud byl objekt zkonstruován s parametrem **true**.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `ReleaseNotifier`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** module.h  
  
 **Namespace:** Microsoft::WRL
 
 ## <a name="see-also"></a>Viz také
 [Module – třída](../windows/module-class.md)