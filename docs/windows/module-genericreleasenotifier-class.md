---
title: "Module::GenericReleaseNotifier – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: module/Microsoft::WRL::Module::GenericReleaseNotifier
dev_langs: C++
helpviewer_keywords: GenericReleaseNotifier class
ms.assetid: 244a8fbe-f89b-409b-aa65-db3e37f9b125
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c87205d1d52c8273ac7eea55fcc5385810349f1f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="modulegenericreleasenotifier-class"></a>Module::GenericReleaseNotifier – třída
Po vydání poslední objekt v aktuální modul, vyvolá obslužnou rutinu události. Obslužné rutiny události je určena na lambda, functor nebo ukazatel funkce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<  
   typename T  
>  
class GenericReleaseNotifier : public ReleaseNotifier;  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ člena data, která obsahuje umístění obslužné rutiny události.  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[Module::GenericReleaseNotifier::GenericReleaseNotifier – konstruktor](../windows/module-genericreleasenotifier-genericreleasenotifier-constructor.md)|Inicializuje novou instanci třídy Module::GenericReleaseNotifier.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[Module::GenericReleaseNotifier::Invoke – metoda](../windows/module-genericreleasenotifier-invoke-method.md)|Volá obslužnou rutinu události související s aktuálním objektem Module::GenericReleaseNotifier.|  
  
### <a name="protected-data-members"></a>Chráněné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[Module::GenericReleaseNotifier::callback_ – datový člen](../windows/module-genericreleasenotifier-callback-data-member.md)|Obsahuje lambda, functor nebo obslužná rutina události – ukazatel funkce související s aktuálním objektem Module::GenericReleaseNotifier.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `ReleaseNotifier`  
  
 `GenericReleaseNotifier`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** module.h  
  
 **Namespace:** Microsoft::WRL
 
 ## <a name="see-also"></a>Viz také
 [Module – třída](../windows/module-class.md)