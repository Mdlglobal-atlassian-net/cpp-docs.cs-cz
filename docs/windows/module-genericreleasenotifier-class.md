---
title: Module::genericreleasenotifier – třída | Dokumentace Microsoftu
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
ms.openlocfilehash: ba92e459ffb26ffc1bbb9239a843d628e7041d6d
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2018
ms.locfileid: "40013516"
---
# <a name="modulegenericreleasenotifier-class"></a>Module::GenericReleaseNotifier – třída
Vyvolá obslužnou rutinu události po vydání poslední objekt v aktuálním modulu. Obslužná rutina události je zadaný ve výrazu lambda, funktor nebo ukazatel na funkci.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
template<typename T>  
class GenericReleaseNotifier : public ReleaseNotifier;  
```  
  
### <a name="parameters"></a>Parametry  
 *T*  
 Typ datového člena, který obsahuje umístění obslužné rutiny události.  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[Module::GenericReleaseNotifier::GenericReleaseNotifier – konstruktor](../windows/module-genericreleasenotifier-genericreleasenotifier-constructor.md)|Inicializuje novou instanci třídy **Module::GenericReleaseNotifier** třídy.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[Module::GenericReleaseNotifier::Invoke – metoda](../windows/module-genericreleasenotifier-invoke-method.md)|Volá obslužnou rutinu události spojené s aktuálním **Module::GenericReleaseNotifier** objektu.|  
  
### <a name="protected-data-members"></a>Chránění členové dat  
  
|Název|Popis|  
|----------|-----------------|  
|[Module::GenericReleaseNotifier::callback_ – datový člen](../windows/module-genericreleasenotifier-callback-data-member.md)|Obsahuje výraz lambda, funktor nebo obslužná rutina události ukazatele na funkce přidružené k aktuální **Module::GenericReleaseNotifier** objektu.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `ReleaseNotifier`  
  
 `GenericReleaseNotifier`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** module.h  
  
 **Namespace:** Microsoft::WRL
 
 ## <a name="see-also"></a>Viz také
 [Module – třída](../windows/module-class.md)