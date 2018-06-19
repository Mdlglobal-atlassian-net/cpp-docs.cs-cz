---
title: WeakReference Class1 | Microsoft Docs
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
ms.openlocfilehash: a44b992138371ff33a9059990a5ec3e93689c679
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33891643"
---
# <a name="weakreference-class1"></a>WeakReference Class1
Podporuje infrastrukturu rozhraní knihovny WRL a není určena pro použití přímo z vašeho kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class WeakReference;  
```  
  
## <a name="remarks"></a>Poznámky  
 Představuje *slabé odkaz* , lze pomocí prostředí Windows Runtime nebo klasického modelu COM. Slabé odkazy představuje objekt, který může nebo nemusí být dostupné.  
  
 A `WeakReference` objekt udržuje *silné odkaz*, který je zde ukazatel na objekt a *počet silné odkazů*, což je počet kopií silné odkaz, který byl distribuován podle Metoda Resolve(). Sice nenulový počet silné odkaz, odkaz na silné je platný a je přístupný objekt. Pokud počet silné odkazů klesne na nulu, silné odkaz je neplatný a objekt je nedostupný.  
  
 WeakReference objekt se obvykle používá k reprezentování objekt, jehož existence řídí na externí vlákna nebo aplikaci. Můžete například vytvořte objekt WeakReference z odkaz na objekt souboru. Je-li otevřít soubor, je silné odkaz platný. Ale pokud soubor se zavřel, silné odkaz bude neplatná.  
  
 WeakReference metody jsou bezpečné pro přístup z více vláken.  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[WeakReference::WeakReference – konstruktor](../windows/weakreference-weakreference-constructor.md)|Inicializuje novou instanci třídy WeakReference.|  
|[WeakReference::~WeakReference – destruktor](../windows/weakreference-tilde-weakreference-destructor.md)|Deinitializes (zničí) aktuální instance třídy WeakReference.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[WeakReference::DecrementStrongReference – metoda](../windows/weakreference-decrementstrongreference-method.md)|Snižuje počet silné odkaz na aktuální objekt WeakReference.|  
|[WeakReference::IncrementStrongReference – metoda](../windows/weakreference-incrementstrongreference-method.md)|Zvětší počet silné odkaz na aktuální WeakReference objektu.|  
|[WeakReference::Resolve – metoda](../windows/weakreference-resolve-method.md)|Nastaví zadaný ukazatele na aktuální hodnotu silné odkaz, pokud počet silné odkazů nenulové hodnoty.|  
|[WeakReference::SetUnknown – metoda](../windows/weakreference-setunknown-method.md)|Nastaví odkaz na silné aktuálního objektu WeakReference ukazatel zadaný rozhraní.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `WeakReference`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** implements.h  
  
 **Namespace:** Microsoft::WRL:: details –  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)