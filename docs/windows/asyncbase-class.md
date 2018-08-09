---
title: Asyncbase – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase
dev_langs:
- C++
helpviewer_keywords:
- AsyncBase class
ms.assetid: 64259b9b-f427-4ffd-a611-e7a2f82362b2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: dcf5a095167e48a52405978a105cadaddfa870f2
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39647811"
---
# <a name="asyncbase-class"></a>AsyncBase – třída
Implementuje asynchronní stav počítače Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
template <  
   typename TComplete,  
   typename TProgress = Details::Nil,  
   AsyncResultType resultType = SingleResult  
>  
class AsyncBase : public AsyncBase<TComplete, Details::Nil, resultType>;  
  
template <  
   typename TComplete,  
   AsyncResultType resultType  
>  
class AsyncBase<TComplete, Details::Nil, resultType> : public Microsoft::WRL::Implements<IAsyncInfo>;  
```  
  
### <a name="parameters"></a>Parametry  
 *TComplete*  
 Obslužná rutina události, která je volána po dokončení asynchronní operace.  
  
 *TProgress*  
 Obslužná rutina události, která je volána při spuštěné asynchronní operace nahlásí aktuální průběh operace.  
  
 *Hodnota resultType*  
 Jeden z [asyncresulttype –](../windows/asyncresulttype-enumeration.md) hodnot výčtu. Ve výchozím nastavení `SingleResult`.  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[AsyncBase::AsyncBase – konstruktor](../windows/asyncbase-asyncbase-constructor.md)|Inicializuje novou instanci **asyncbase –** třídy.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[AsyncBase::Cancel – metoda](../windows/asyncbase-cancel-method.md)|Zruší asynchronní operace.|  
|[AsyncBase::Close – metoda](../windows/asyncbase-close-method.md)|Ukončí asynchronní operaci.|  
|[AsyncBase::FireCompletion – metoda](../windows/asyncbase-firecompletion-method.md)|Vyvolá obslužnou rutinu události dokončení nebo obnoví vnitřní průběh delegáta.|  
|[AsyncBase::FireProgress – metoda](../windows/asyncbase-fireprogress-method.md)|Vyvolá obslužnou rutinu události aktuální průběh.|  
|[AsyncBase::get_ErrorCode – metoda](../windows/asyncbase-get-errorcode-method.md)|Získá kód chyby pro aktuální asynchronní operaci.|  
|[AsyncBase::get_Id – metoda](../windows/asyncbase-get-id-method.md)|Načte popisovač asynchronní operace.|  
|[AsyncBase::get_Status – metoda](../windows/asyncbase-get-status-method.md)|Načte hodnotu označující stav asynchronní operace.|  
|[AsyncBase::GetOnComplete – metoda](../windows/asyncbase-getoncomplete-method.md)|Adresa aktuálního obslužné rutiny události dokončení zkopíruje do zadané proměnné.|  
|[AsyncBase::GetOnProgress – metoda](../windows/asyncbase-getonprogress-method.md)|Adresa obslužné rutiny události aktuální průběh zkopíruje do zadané proměnné.|  
|[AsyncBase::put_Id – metoda](../windows/asyncbase-put-id-method.md)|Nastaví popisovač asynchronní operace.|  
|[AsyncBase::PutOnComplete – metoda](../windows/asyncbase-putoncomplete-method.md)|Nastaví adresu obslužné rutiny události dokončení se zadanou hodnotou.|  
|[AsyncBase::PutOnProgress – metoda](../windows/asyncbase-putonprogress-method.md)|Nastaví adresu průběh obslužné rutiny události se zadanou hodnotou.|  
|[AsyncBase::Start – metoda](../windows/asyncbase-start-method.md)|Spustí asynchronní operaci.|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[AsyncBase::CheckValidStateForDelegateCall – metoda](../windows/asyncbase-checkvalidstatefordelegatecall-method.md)|Ověřuje, zda vlastnosti delegáta lze upravit v aktuálním asynchronní stavu.|  
|[AsyncBase::CheckValidStateForResultsCall – metoda](../windows/asyncbase-checkvalidstateforresultscall-method.md)|Testuje, jestli výsledky asynchronní operace se můžou shromažďovat v aktuálním asynchronní stavu.|  
|[AsyncBase::ContinueAsyncOperation – metoda](../windows/asyncbase-continueasyncoperation-method.md)|Určuje, zda by měly pokračovat ve zpracování asynchronní operaci, nebo by měla zastavit.|  
|[AsyncBase::CurrentStatus – metoda](../windows/asyncbase-currentstatus-method.md)|Načte stav aktuální asynchronní operace.|  
|[AsyncBase::ErrorCode – metoda](../windows/asyncbase-errorcode-method.md)|Získá kód chyby pro aktuální asynchronní operaci.|  
|[AsyncBase::OnCancel – metoda](../windows/asyncbase-oncancel-method.md)|Při přepisu v odvozené třídě, zruší asynchronní operace.|  
|[AsyncBase::OnClose – metoda](../windows/asyncbase-onclose-method.md)|Při přepisu v odvozené třídě, ukončí asynchronní operaci.|  
|[AsyncBase::OnStart – metoda](../windows/asyncbase-onstart-method.md)|Při přepisu v odvozené třídě, spustí asynchronní operaci.|  
|[AsyncBase::TryTransitionToCompleted – metoda](../windows/asyncbase-trytransitiontocompleted-method.md)|Určuje, zda aktuální asynchronní operace byla dokončena.|  
|[AsyncBase::TryTransitionToError – metoda](../windows/asyncbase-trytransitiontoerror-method.md)|Určuje, zda kód zadanou chybovou můžete upravit stavu došlo k vnitřní chybě.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `AsyncBase`  
  
 `AsyncBase`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** async.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL – obor názvů](../windows/microsoft-wrl-namespace.md)