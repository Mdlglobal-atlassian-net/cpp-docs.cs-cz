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
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c33d48c69852ab22cfa2bfb4f33d45edcc469662
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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
|[AsyncBase::AsyncBase – konstruktor](../windows/asyncbase-asyncbase-constructor.md)|Inicializuje novou instanci třídy AsyncBase.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[AsyncBase::Cancel – metoda](../windows/asyncbase-cancel-method.md)|Zruší asynchronní operace.|  
|[AsyncBase::Close – metoda](../windows/asyncbase-close-method.md)|Ukončí asynchronní operaci.|  
|[AsyncBase::FireCompletion – metoda](../windows/asyncbase-firecompletion-method.md)|Volá obslužnou rutinu události dokončení nebo obnoví interní průběh delegáta.|  
|[AsyncBase::FireProgress – metoda](../windows/asyncbase-fireprogress-method.md)|Vyvolá aktuální obslužné rutiny události průběh.|  
|[AsyncBase::get_ErrorCode – metoda](../windows/asyncbase-get-errorcode-method.md)|Načte kód chyby pro aktuální asynchronní operaci.|  
|[AsyncBase::get_Id – metoda](../windows/asyncbase-get-id-method.md)|Načte popisovač asynchronní operaci.|  
|[AsyncBase::get_Status – metoda](../windows/asyncbase-get-status-method.md)|Načte hodnotu, která určuje stav asynchronní operace.|  
|[AsyncBase::GetOnComplete – metoda](../windows/asyncbase-getoncomplete-method.md)|Zkopíruje adresu aktuální obslužné rutiny události dokončení na zadanou proměnnou.|  
|[AsyncBase::GetOnProgress – metoda](../windows/asyncbase-getonprogress-method.md)|Zkopíruje adresu aktuální obslužné rutiny události průběhu na zadanou proměnnou.|  
|[AsyncBase::put_Id – metoda](../windows/asyncbase-put-id-method.md)|Nastaví popisovač asynchronní operaci.|  
|[AsyncBase::PutOnComplete – metoda](../windows/asyncbase-putoncomplete-method.md)|Nastaví adresu dokončení obslužné rutiny události se zadanou hodnotou.|  
|[AsyncBase::PutOnProgress – metoda](../windows/asyncbase-putonprogress-method.md)|Nastaví adresu průběh obslužné rutiny události se zadanou hodnotou.|  
|[AsyncBase::Start – metoda](../windows/asyncbase-start-method.md)|Spustí asynchronní operaci.|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[AsyncBase::CheckValidStateForDelegateCall – metoda](../windows/asyncbase-checkvalidstatefordelegatecall-method.md)|Ověřuje, zda vlastnosti delegáta lze upravit v aktuálním stavu asynchronní.|  
|[AsyncBase::CheckValidStateForResultsCall – metoda](../windows/asyncbase-checkvalidstateforresultscall-method.md)|Ověřuje, zda je možné v aktuálním stavu asynchronní shromažďovat výsledky asynchronní operace.|  
|[AsyncBase::ContinueAsyncOperation – metoda](../windows/asyncbase-continueasyncoperation-method.md)|Určuje, zda by měly pokračovat ve zpracování asynchronní operaci, nebo by měla zastaví.|  
|[AsyncBase::CurrentStatus – metoda](../windows/asyncbase-currentstatus-method.md)|Načte stav aktuální asynchronní operace.|  
|[AsyncBase::ErrorCode – metoda](../windows/asyncbase-errorcode-method.md)|Načte kód chyby pro aktuální asynchronní operaci.|  
|[AsyncBase::OnCancel – metoda](../windows/asyncbase-oncancel-method.md)|Při přepisu v odvozené třídě, zruší asynchronní operace.|  
|[AsyncBase::OnClose – metoda](../windows/asyncbase-onclose-method.md)|Při přepisu v odvozené třídě, ukončí asynchronní operaci.|  
|[AsyncBase::OnStart – metoda](../windows/asyncbase-onstart-method.md)|Při přepisu v odvozené třídě, spustí asynchronní operaci.|  
|[AsyncBase::TryTransitionToCompleted – metoda](../windows/asyncbase-trytransitiontocompleted-method.md)|Určuje, zda aktuální asynchronní operace byla dokončena.|  
|[AsyncBase::TryTransitionToError – metoda](../windows/asyncbase-trytransitiontoerror-method.md)|Určuje, zda kód zadaný chyby můžete upravit stav vnitřní chybě.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `AsyncBase`  
  
 `AsyncBase`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** async.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL – obor názvů](../windows/microsoft-wrl-namespace.md)