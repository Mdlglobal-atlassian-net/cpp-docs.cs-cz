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
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: eb640f146109363a8025818b3ec560c250029914
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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
|[Module::ReleaseNotifier::~ReleaseNotifier – destruktor](../windows/module-releasenotifier-tilde-releasenotifier-destructor.md)|Deinitializes aktuální instance třídy Module::ReleaseNotifier.|  
|[Module::ReleaseNotifier::ReleaseNotifier – konstruktor](../windows/module-releasenotifier-releasenotifier-constructor.md)|Inicializuje novou instanci třídy Module::ReleaseNotifier.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[Module::ReleaseNotifier::Invoke – metoda](../windows/module-releasenotifier-invoke-method.md)|Pokud je implementována, volá obslužnou rutinu události při vydání poslední objekt v modulu.|  
|[Module::ReleaseNotifier::Release](../windows/module-releasenotifier-release.md)|Odstraní aktuální objekt Module::ReleaseNotifier, pokud objekt byl zkonstruován s parametrem `true`.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `ReleaseNotifier`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** module.h  
  
 **Namespace:** Microsoft::WRL
 
 ## <a name="see-also"></a>Viz také
 [Module – třída](../windows/module-class.md)