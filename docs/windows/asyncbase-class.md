---
title: "AsyncBase – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: async/Microsoft::WRL::AsyncBase
dev_langs: C++
helpviewer_keywords: AsyncBase class
ms.assetid: 64259b9b-f427-4ffd-a611-e7a2f82362b2
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ad32c1ed42a2a991ba9ed9bd550330bc460834cc
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="asyncbase-class"></a>AsyncBase – třída
Implementuje počítač asynchronní stavu prostředí Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
template <  
   typename TComplete,  
   typename TProgress = Details::Nil,  
   AsyncResultType resultType = SingleResult  
>  
class AsyncBase : public AsyncBase< TComplete, Details::Nil, resultType >;  
  
template <  
   typename TComplete,  
   AsyncResultType resultType  
>  
class AsyncBase< TComplete, Details::Nil, resultType > : public Microsoft::WRL::Implements< IAsyncInfo >;  
```  
  
#### <a name="parameters"></a>Parametry  
 `TComplete`  
 Obslužné rutiny události, která je volána při dokončení asynchronní operace.  
  
 `TProgress`  
 Obslužné rutiny události, která je volána při spuštění asynchronní operaci sestavy aktuální průběh operace.  
  
 `resultType`  
 Jeden z [AsyncResultType](../windows/asyncresulttype-enumeration.md) hodnot výčtu. Ve výchozím nastavení SingleResult.  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[Asyncbase::asyncbase – konstruktor](../windows/asyncbase-asyncbase-constructor.md)|Inicializuje novou instanci třídy AsyncBase.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[Asyncbase::Cancel – metoda](../windows/asyncbase-cancel-method.md)|Zruší asynchronní operace.|  
|[Asyncbase::Close – metoda](../windows/asyncbase-close-method.md)|Ukončí asynchronní operaci.|  
|[Asyncbase::firecompletion – metoda](../windows/asyncbase-firecompletion-method.md)|Volá obslužnou rutinu události dokončení nebo obnoví interní průběh delegáta.|  
|[Asyncbase::fireprogress – metoda](../windows/asyncbase-fireprogress-method.md)|Vyvolá aktuální obslužné rutiny události průběh.|  
|[Asyncbase::get_errorcode – metoda](../windows/asyncbase-get-errorcode-method.md)|Načte kód chyby pro aktuální asynchronní operaci.|  
|[Asyncbase::get_id – metoda](../windows/asyncbase-get-id-method.md)|Načte popisovač asynchronní operaci.|  
|[Asyncbase::get_status – metoda](../windows/asyncbase-get-status-method.md)|Načte hodnotu, která určuje stav asynchronní operace.|  
|[Asyncbase::getoncomplete – metoda](../windows/asyncbase-getoncomplete-method.md)|Zkopíruje adresu aktuální obslužné rutiny události dokončení na zadanou proměnnou.|  
|[Asyncbase::getonprogress – metoda](../windows/asyncbase-getonprogress-method.md)|Zkopíruje adresu aktuální obslužné rutiny události průběhu na zadanou proměnnou.|  
|[Asyncbase::put_id – metoda](../windows/asyncbase-put-id-method.md)|Nastaví popisovač asynchronní operaci.|  
|[Asyncbase::putoncomplete – metoda](../windows/asyncbase-putoncomplete-method.md)|Nastaví adresu dokončení obslužné rutiny události se zadanou hodnotou.|  
|[Asyncbase::putonprogress – metoda](../windows/asyncbase-putonprogress-method.md)|Nastaví adresu průběh obslužné rutiny události se zadanou hodnotou.|  
|[Asyncbase::Start – metoda](../windows/asyncbase-start-method.md)|Spustí asynchronní operaci.|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[Asyncbase::checkvalidstatefordelegatecall – metoda](../windows/asyncbase-checkvalidstatefordelegatecall-method.md)|Ověřuje, zda vlastnosti delegáta lze upravit v aktuálním stavu asynchronní.|  
|[Asyncbase::checkvalidstateforresultscall – metoda](../windows/asyncbase-checkvalidstateforresultscall-method.md)|Ověřuje, zda je možné v aktuálním stavu asynchronní shromažďovat výsledky asynchronní operace.|  
|[Asyncbase::continueasyncoperation – metoda](../windows/asyncbase-continueasyncoperation-method.md)|Určuje, zda by měly pokračovat ve zpracování asynchronní operaci, nebo by měla zastaví.|  
|[Asyncbase::currentStatus – metoda](../windows/asyncbase-currentstatus-method.md)|Načte stav aktuální asynchronní operace.|  
|[Asyncbase::ErrorCode – metoda](../windows/asyncbase-errorcode-method.md)|Načte kód chyby pro aktuální asynchronní operaci.|  
|[Asyncbase::oncancel – metoda](../windows/asyncbase-oncancel-method.md)|Při přepisu v odvozené třídě, zruší asynchronní operace.|  
|[Asyncbase::onclose – metoda](../windows/asyncbase-onclose-method.md)|Při přepisu v odvozené třídě, ukončí asynchronní operaci.|  
|[Asyncbase::ONSTART – metoda](../windows/asyncbase-onstart-method.md)|Při přepisu v odvozené třídě, spustí asynchronní operaci.|  
|[Asyncbase::trytransitiontocompleted – metoda](../windows/asyncbase-trytransitiontocompleted-method.md)|Určuje, zda aktuální asynchronní operace byla dokončena.|  
|[Asyncbase::trytransitiontoerror – metoda](../windows/asyncbase-trytransitiontoerror-method.md)|Určuje, zda kód zadaný chyby můžete upravit stav vnitřní chybě.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `AsyncBase`  
  
 `AsyncBase`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** async.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL Namespace](../windows/microsoft-wrl-namespace.md)