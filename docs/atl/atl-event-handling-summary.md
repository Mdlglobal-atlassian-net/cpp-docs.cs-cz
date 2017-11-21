---
title: "Zpracování Souhrn událostí ATL | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: event handling, implementing
ms.assetid: e8b47ef0-0bdc-47ff-9dd6-34df11dde9a2
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 8c4aec5679ae7a880bd5305037e880de9ff7d93a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="atl-event-handling-summary"></a>Souhrn zpracování události knihovny ATL
Obecně platí zpracování událostí modelu COM je poměrně jednoduché proces. Existují tři hlavní kroky:  
  
-   Implementaci rozhraní událostí v objektu.  
  
-   Poraďte zdroj události, jestli chce přijímat události objektu.  
  
-   Zdroj události Unadvise, pokud objekt již nepotřebuje přijímat události.  
  
## <a name="implementing-the-interface"></a>Implementace rozhraní  
 Existují čtyři hlavní způsoby implementace rozhraní pomocí ATL.  
  
|Odvozena od|Vhodná pro typ rozhraní|Vyžaduje, abyste implementovat všechny metody *|Vyžaduje knihovny typů v době běhu|  
|-----------------|---------------------------------|---------------------------------------------|-----------------------------------------|  
|Rozhraní|Vtable|Ano|Ne|  
|[IDispatchImpl](../atl/reference/idispatchimpl-class.md)|Duální|Ano|Ano|  
|[IDispEventImpl](../atl/reference/idispeventimpl-class.md)|Dispinterface|Ne|Ano|  
|[IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md)|Dispinterface|Ne|Ne|  
  
 \*Při použití třídy, které podporují ATL, nikdy musíte implementovat **IUnknown** nebo `IDispatch` metody ručně.  
  
## <a name="advising-and-unadvising-the-event-source"></a>Poradenství a Unadvising zdroj události  
 Existují tři způsoby hlavní radí a unadvising zdroje událostí pomocí ATL.  
  
|Poradit – funkce|Unadvise – funkce|Nejvhodnější pro použití s|Vyžaduje, abyste ke sledování souboru cookie|Komentáře|  
|---------------------|-----------------------|--------------------------------|---------------------------------------------|--------------|  

|[AtlAdvise](reference/connection-point-global-functions.md#atladvise), [CComPtrBase::Advise](../atl/reference/ccomptrbase-class.md#advise)|[AtlUnadvise](reference/connection-point-global-functions.md#atlunadvise)| Vtable nebo duální rozhraní | Ano | `AtlAdvise` je globální funkce ATL. `CComPtrBase::Advise`používá [CComPtr](../atl/reference/ccomptr-class.md) a [CComQIPtr](../atl/reference/ccomqiptr-class.md). |  

|[IDispEventSimpleImpl::DispEventAdvise](../atl/reference/idispeventsimpleimpl-class.md#dispeventadvise)|[IDispEventSimpleImpl::DispEventUnadvise](../atl/reference/idispeventsimpleimpl-class.md#dispeventunadvise)|[IDispEventImpl](../atl/reference/idispeventimpl-class.md) nebo [ IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md)| Ne | Parametry méně než `AtlAdvise` od základní třídy nemá další práci. |  
|[CComCompositeControl::AdviseSinkMap(TRUE)](../atl/reference/ccomcompositecontrol-class.md#advisesinkmap)|[CComCompositeControl::AdviseSinkMap(FALSE)](../atl/reference/ccomcompositecontrol-class.md#advisesinkmap)| ActiveX – ovládací prvky v složené ovládací prvky | Ne | `CComCompositeControl::AdviseSinkMap` informuje o tom, všechny položky události jímky mapy. Stejnou funkci unadvises položky. Tato metoda je volána automaticky pomocí `CComCompositeControl` třídy. |  
|[CAxDialogImpl::AdviseSinkMap(TRUE)](../atl/reference/caxdialogimpl-class.md#advisesinkmap)|[CAxDialogImpl::AdviseSinkMap(FALSE)](../atl/reference/caxdialogimpl-class.md#advisesinkmap)| ActiveX – ovládací prvky v dialogovém okně | Ne | `CAxDialogImpl::AdviseSinkMap` informuje o tom a unadvises všechny ovládací prvky ActiveX v prostředku dialogového okna. To se provádí automaticky za vás. |  
  
## <a name="see-also"></a>Viz také  
 [Zpracování událostí](../atl/event-handling-and-atl.md)   
 [Podpora IDispEventImpl](../atl/supporting-idispeventimpl.md)

