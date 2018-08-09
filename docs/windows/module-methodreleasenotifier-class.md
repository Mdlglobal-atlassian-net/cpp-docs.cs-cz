---
title: Module::methodreleasenotifier – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::MethodReleaseNotifier
dev_langs:
- C++
helpviewer_keywords:
- MethodReleaseNotifier class
ms.assetid: 5c2902be-964b-488f-9f1c-adf504995cbc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 80b2653128415cfd847db5b9592df116ffd0d470
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2018
ms.locfileid: "40014309"
---
# <a name="modulemethodreleasenotifier-class"></a>Module::MethodReleaseNotifier – třída
Vyvolá obslužnou rutinu události po vydání poslední objekt v aktuálním modulu. Obslužná rutina události je zadaný objekt a jejího člena ukazatel na metodu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
template<typename T>  
class MethodReleaseNotifier : public ReleaseNotifier;  
```  
  
### <a name="parameters"></a>Parametry  
 *T*  
 Typ objektu, jehož členská funkce je obslužnou rutinu události.  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[Module::MethodReleaseNotifier::MethodReleaseNotifier – konstruktor](../windows/module-methodreleasenotifier-methodreleasenotifier-constructor.md)|Inicializuje novou instanci třídy **Module::MethodReleaseNotifier** třídy.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[Module::MethodReleaseNotifier::Invoke – metoda](../windows/module-methodreleasenotifier-invoke-method.md)|Volá obslužnou rutinu události spojené s aktuálním **Module::MethodReleaseNotifier** objektu.|  
  
### <a name="protected-data-members"></a>Chránění členové dat  
  
|Název|Popis|  
|----------|-----------------|  
|[Module::MethodReleaseNotifier::method_ – datový člen](../windows/module-methodreleasenotifier-method-data-member.md)|Uchovává ukazatel na obslužnou rutinu události pro aktuální **Module::MethodReleaseNotifier** objektu.|  
|[Module::MethodReleaseNotifier::object_ – datový člen](../windows/module-methodreleasenotifier-object-data-member.md)|Uchovává ukazatel na objekt, jehož členská funkce je obslužnou rutinu události pro aktuální **Module::MethodReleaseNotifier** objektu.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `ReleaseNotifier`  
  
 `MethodReleaseNotifier`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** module.h  
  
 **Namespace:** Microsoft::WRL
 
 ## <a name="see-also"></a>Viz také
 [Module – třída](../windows/module-class.md)