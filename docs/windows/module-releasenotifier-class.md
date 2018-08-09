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
ms.openlocfilehash: 97c998f7e0814c5acae55dd3e9b747faed0242e1
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2018
ms.locfileid: "40016220"
---
# <a name="modulereleasenotifier-class"></a>Module::ReleaseNotifier – třída
Vyvolá obslužnou rutinu události po vydání poslední objekt v modulu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
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