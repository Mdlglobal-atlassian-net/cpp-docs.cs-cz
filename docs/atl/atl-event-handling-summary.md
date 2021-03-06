---
title: Shrnutí zpracování událostí ATL
ms.date: 11/04/2016
helpviewer_keywords:
- event handling, implementing
ms.assetid: e8b47ef0-0bdc-47ff-9dd6-34df11dde9a2
ms.openlocfilehash: 0e3a47719e3160170ed1bfa64b315415ddc7a1c8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62252145"
---
# <a name="atl-event-handling-summary"></a>Shrnutí zpracování událostí ATL

Obecně platí zpracování událostí modelu COM je poměrně jednoduchý proces. Existují tři hlavní kroky:

- Implementace rozhraní události na váš objekt.

- Doporučte zdroj události, chce přijímat události objektu.

- Když váš objekt už nebude potřeba příjem událostí, zrušíte avízo o zdroji události.

## <a name="implementing-the-interface"></a>Implementace rozhraní

Existují čtyři hlavní způsoby implementace rozhraní pomocí knihovny ATL.

|Jsou odvozeny z|Vhodný pro typ rozhraní|Je potřeba implementovat všechny metody *|Vyžaduje knihovnu typů v době běhu|
|-----------------|---------------------------------|---------------------------------------------|-----------------------------------------|
|Rozhraní|Vtable|Ano|Ne|
|[IDispatchImpl](../atl/reference/idispatchimpl-class.md)|Duální|Ano|Ano|
|[IDispEventImpl](../atl/reference/idispeventimpl-class.md)|Dispinterface|Ne|Ano|
|[IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md)|Dispinterface|Ne|Ne|

\* Při použití třídy podpory knihovny ATL, nikdy musíte implementovat `IUnknown` nebo `IDispatch` metody ručně.

## <a name="advising-and-unadvising-the-event-source"></a>Nutnost a Unadvising zdroj události

Existují tři hlavní způsoby informacemi a unadvising zdroje událostí pomocí knihovny ATL.

|Doporučte – funkce|Zrušíte avízo o – funkce|Nejvhodnější pro použití se službou|Vyžaduje, abyste udržovat přehled o souboru cookie|Komentáře|
|---------------------|-----------------------|--------------------------------|---------------------------------------------|--------------|
|[AtlAdvise](reference/connection-point-global-functions.md#atladvise), [CComPtrBase::Advise](../atl/reference/ccomptrbase-class.md#advise)|[AtlUnadvise](reference/connection-point-global-functions.md#atlunadvise)|Vtable nebo duální rozhraní|Ano|`AtlAdvise` globální funkce ATL je. `CComPtrBase::Advise` používá [CComPtr](../atl/reference/ccomptr-class.md) a [CComQIPtr](../atl/reference/ccomqiptr-class.md).|
|[IDispEventSimpleImpl::DispEventAdvise](../atl/reference/idispeventsimpleimpl-class.md#dispeventadvise)|[IDispEventSimpleImpl::DispEventUnadvise](../atl/reference/idispeventsimpleimpl-class.md#dispeventunadvise)|[Idispeventimpl –](../atl/reference/idispeventimpl-class.md) nebo [idispeventsimpleimpl –](../atl/reference/idispeventsimpleimpl-class.md)|Ne|Méně parametrů než `AtlAdvise` od základní třídy provede další práci.|
|[CComCompositeControl::AdviseSinkMap(TRUE)](../atl/reference/ccomcompositecontrol-class.md#advisesinkmap)|[CComCompositeControl::AdviseSinkMap(FALSE)](../atl/reference/ccomcompositecontrol-class.md#advisesinkmap)|Ovládací prvky ActiveX v složených ovládacích prvků|Ne|`CComCompositeControl::AdviseSinkMap` vás informuje o tom, že všechny položky v případě jímky mapy. Stejnou funkci unadvises položky. Tato metoda je volána automaticky `CComCompositeControl` třídy.|
|[CAxDialogImpl::AdviseSinkMap(TRUE)](../atl/reference/caxdialogimpl-class.md#advisesinkmap)|[CAxDialogImpl::AdviseSinkMap(FALSE)](../atl/reference/caxdialogimpl-class.md#advisesinkmap)|Ovládací prvky ActiveX v dialogovém okně|Ne|`CAxDialogImpl::AdviseSinkMap` vás informuje o tom a unadvises všechny ovládací prvky ActiveX v prostředku dialogového okna. To je prováděno automaticky za vás.|

## <a name="see-also"></a>Viz také:

[Zpracování událostí](../atl/event-handling-and-atl.md)<br/>
[Podpora IDispEventImpl](../atl/supporting-idispeventimpl.md)
