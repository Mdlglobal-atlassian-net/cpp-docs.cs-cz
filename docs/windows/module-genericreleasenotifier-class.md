---
title: Module::GenericReleaseNotifier – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::GenericReleaseNotifier
dev_langs:
- C++
helpviewer_keywords:
- GenericReleaseNotifier class
ms.assetid: 244a8fbe-f89b-409b-aa65-db3e37f9b125
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c3ba58e08bac36d905fbf874546d7791f2aa3fcb
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33882005"
---
# <a name="modulegenericreleasenotifier-class"></a>Module::GenericReleaseNotifier – třída
Po vydání poslední objekt v aktuální modul, vyvolá obslužnou rutinu události. Obslužné rutiny události je určena na lambda, functor nebo ukazatel funkce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<typename T>  
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