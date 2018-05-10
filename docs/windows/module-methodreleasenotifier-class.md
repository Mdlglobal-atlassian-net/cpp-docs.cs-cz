---
title: Module::MethodReleaseNotifier – třída | Microsoft Docs
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
ms.openlocfilehash: 217e58f73130922d45f0d303e1e91858e8c2272f
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="modulemethodreleasenotifier-class"></a>Module::MethodReleaseNotifier – třída
Po vydání poslední objekt v aktuální modul, vyvolá obslužnou rutinu události. Obslužné rutiny události je zadaný objekt a jejího člena ukazatel na metodu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<typename T>  
class MethodReleaseNotifier : public ReleaseNotifier;  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ objektu, jehož členská funkce je obslužná rutina události.  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[Module::MethodReleaseNotifier::MethodReleaseNotifier – konstruktor](../windows/module-methodreleasenotifier-methodreleasenotifier-constructor.md)|Inicializuje novou instanci třídy Module::MethodReleaseNotifier.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[Module::MethodReleaseNotifier::Invoke – metoda](../windows/module-methodreleasenotifier-invoke-method.md)|Volá obslužnou rutinu události související s aktuálním objektem Module::MethodReleaseNotifier.|  
  
### <a name="protected-data-members"></a>Chráněné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[Module::MethodReleaseNotifier::method_ – datový člen](../windows/module-methodreleasenotifier-method-data-member.md)|Obslužné rutiny události pro aktuální objekt Module::MethodReleaseNotifier obsahuje ukazatel.|  
|[Module::MethodReleaseNotifier::object_ – datový člen](../windows/module-methodreleasenotifier-object-data-member.md)|Obsahuje ukazatele na objekt, jehož členská funkce je obslužné rutiny události pro aktuální objekt Module::MethodReleaseNotifier.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `ReleaseNotifier`  
  
 `MethodReleaseNotifier`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** module.h  
  
 **Namespace:** Microsoft::WRL
 
 ## <a name="see-also"></a>Viz také
 [Module – třída](../windows/module-class.md)