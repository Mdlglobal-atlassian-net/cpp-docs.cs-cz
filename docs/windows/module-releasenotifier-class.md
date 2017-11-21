---
title: "Module::ReleaseNotifier – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: module/Microsoft::WRL::Module::ReleaseNotifier
dev_langs: C++
helpviewer_keywords: ReleaseNotifier class
ms.assetid: 17249cd1-4d88-42e3-8146-da9e942d12bd
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b48374182d9b39d43cbf0ec99cb51075867e914d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="modulereleasenotifier-class"></a>Module::ReleaseNotifier – třída
Vyvolá obslužnou rutinu události, až bude vydaná poslední objekt v modulu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class ReleaseNotifier;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[Module::ReleaseNotifier:: ~ releasenotifier – destruktor](../windows/module-releasenotifier-tilde-releasenotifier-destructor.md)|Deinitializes aktuální instance třídy Module::ReleaseNotifier.|  
|[Module::releasenotifier:: releasenotifier – konstruktor](../windows/module-releasenotifier-releasenotifier-constructor.md)|Inicializuje novou instanci třídy Module::ReleaseNotifier.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[Module::ReleaseNotifier:: Invoke – metoda](../windows/module-releasenotifier-invoke-method.md)|Pokud je implementována, volá obslužnou rutinu události při vydání poslední objekt v modulu.|  
|[Module::ReleaseNotifier::Release](../windows/module-releasenotifier-release.md)|Odstraní aktuální objekt Module::ReleaseNotifier, pokud objekt byl zkonstruován s parametrem `true`.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `ReleaseNotifier`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** module.h  
  
 **Namespace:** Microsoft::WRL
 
 ## <a name="see-also"></a>Viz také
 [Module – třídy](../windows/module-class.md)