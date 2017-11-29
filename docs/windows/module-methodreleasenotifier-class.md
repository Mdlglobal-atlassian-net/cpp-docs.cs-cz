---
title: "Module::MethodReleaseNotifier – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: module/Microsoft::WRL::Module::MethodReleaseNotifier
dev_langs: C++
helpviewer_keywords: MethodReleaseNotifier class
ms.assetid: 5c2902be-964b-488f-9f1c-adf504995cbc
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 474d4f82b41eaab43c5e87ca335b911db0b4e64e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="modulemethodreleasenotifier-class"></a>Module::MethodReleaseNotifier – třída
Po vydání poslední objekt v aktuální modul, vyvolá obslužnou rutinu události. Obslužné rutiny události je zadaný objekt a jejího člena ukazatel na metodu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<  
   typename T  
>  
class MethodReleaseNotifier : public ReleaseNotifier;  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ objektu, jehož členská funkce je obslužná rutina události.  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[Module::methodreleasenotifier:: methodreleasenotifier – konstruktor](../windows/module-methodreleasenotifier-methodreleasenotifier-constructor.md)|Inicializuje novou instanci třídy Module::MethodReleaseNotifier.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[Module::MethodReleaseNotifier:: Invoke – metoda](../windows/module-methodreleasenotifier-invoke-method.md)|Volá obslužnou rutinu události související s aktuálním objektem Module::MethodReleaseNotifier.|  
  
### <a name="protected-data-members"></a>Chráněné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[Module::methodreleasenotifier:: method_ – datový člen](../windows/module-methodreleasenotifier-method-data-member.md)|Obslužné rutiny události pro aktuální objekt Module::MethodReleaseNotifier obsahuje ukazatel.|  
|[Module::methodreleasenotifier:: object_ – datový člen](../windows/module-methodreleasenotifier-object-data-member.md)|Obsahuje ukazatele na objekt, jehož členská funkce je obslužné rutiny události pro aktuální objekt Module::MethodReleaseNotifier.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `ReleaseNotifier`  
  
 `MethodReleaseNotifier`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** module.h  
  
 **Namespace:** Microsoft::WRL
 
 ## <a name="see-also"></a>Viz také
 [Module – třídy](../windows/module-class.md)