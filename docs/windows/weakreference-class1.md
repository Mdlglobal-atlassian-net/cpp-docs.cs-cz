---
title: WeakReference – Třída1 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::WeakReference
dev_langs:
- C++
helpviewer_keywords:
- WeakReference class
ms.assetid: 3f4c956b-dbbd-49b1-8cfa-9509a9956c97
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 78b9a62838508c2e97bdd04f56778a622343e6f1
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2018
ms.locfileid: "40012287"
---
# <a name="weakreference-class1"></a>WeakReference – Třída1
Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
class WeakReference;  
```  
  
## <a name="remarks"></a>Poznámky  
 Představuje *nestálý odkaz* , který je možné pomocí prostředí Windows Runtime nebo klasického modelu COM. Slabý odkaz představuje objekt, který může nebo nemusí být dostupný.  
  
 A **WeakReference** udržuje objekt *silného odkazu*, což je ukazatel na objekt a *silného odkazu počet*, což je počet kopií silného odkaz, který byl distribuován podle `Resolve()` metody. Počet silného odkazu je nenulová, silný odkaz je platný a je přístupný objekt. Když počet odkazů silné klesne na nulu, silný odkaz je neplatný a objekt je nedostupný.  
  
 A **WeakReference** objekt se obvykle používá k reprezentaci objektu, jehož existence je řízena vnějším vláknem nebo aplikací. Například sestavit **WeakReference** objekt z odkazu na objekt souboru. Když je soubor otevřen, silný odkaz je platný. Ale pokud se soubor zavře, silný odkaz níže uvedených situací.  
  
 **WeakReference** metody jsou bezpečné pro vlákna.  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[WeakReference::WeakReference – konstruktor](../windows/weakreference-weakreference-constructor.md)|Inicializuje novou instanci třídy **WeakReference** třídy.|  
|[WeakReference::~WeakReference – destruktor](../windows/weakreference-tilde-weakreference-destructor.md)|Zruší inicializaci (odstraní) aktuální instancí třídy **WeakReference** třídy.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[WeakReference::DecrementStrongReference – metoda](../windows/weakreference-decrementstrongreference-method.md)|Sníží počet silné referenční aktuálního **WeakReference** objektu.|  
|[WeakReference::IncrementStrongReference – metoda](../windows/weakreference-incrementstrongreference-method.md)|Zvýší počet odkazů silné aktuálního **WeakReference** objektu.|  
|[WeakReference::Resolve – metoda](../windows/weakreference-resolve-method.md)|Nastaví zadaný ukazatel na aktuální hodnotu silného odkazu, pokud je počet odkazů silné nenulové.|  
|[WeakReference::SetUnknown – metoda](../windows/weakreference-setunknown-method.md)|Nastaví silný odkaz aktuální **WeakReference** objektu na zadané rozhraní ukazatel.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `WeakReference`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** implements.h  
  
 **Namespace:** Microsoft::WRL:: details –  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)