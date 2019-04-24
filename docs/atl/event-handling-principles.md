---
title: Principy (ATL) pro zpracování událostí
ms.date: 11/04/2016
helpviewer_keywords:
- event handling, implementing
- event handling, advising event sources
- interfaces, event and event sink
- dual interfaces, event interfaces
- event handling, dual event interfaces
ms.assetid: d17ca7cb-54f2-4658-ab8b-b721ac56801d
ms.openlocfilehash: b882a1d356a431f75be1feb6e7bd997abed41c33
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62234768"
---
# <a name="event-handling-principles"></a>Principy zpracování událostí

Společné pro všechny zpracování událostí jsou tři kroky. Budete muset:

- Implementace rozhraní události na váš objekt.

- Doporučte zdroj události, chce přijímat události objektu.

- Když váš objekt už nebude potřeba příjem událostí, zrušíte avízo o zdroji události.

Tak, že budete implementovat rozhraní události závisí na jeho typu. Události rozhraní může být vtable, dvou nebo dispinterface. Záleží jen na návrháře k definování rozhraní zdroje událostí To je pro vás k implementaci rozhraní.

> [!NOTE]
>  I když neexistují žádné z technických důvodů, které nelze duální rozhraní události, existuje mnoho důvodů dobrý návrh vyhnout se použití duals. To je však rozhodnutí provedených Návrhář/implementátora události *zdroj*. Vzhledem k tomu, že pracujete z hlediska události `sink`, je nutné povolit možnost, že nemusí mít kdykoli vybíráte, ale implementace rozhraní duální události. Další informace o duální rozhraní najdete v tématu [duální rozhraní a ATL](../atl/dual-interfaces-and-atl.md).

Nutnost zdroj události je možné rozdělit do tří kroků:

- Zadat dotaz na objekt zdroje pro [IConnectionPointContainer](/windows/desktop/api/ocidl/nn-ocidl-iconnectionpointcontainer).

- Volání [IConnectionPointContainer::FindConnectionPoint](/windows/desktop/api/ocidl/nf-ocidl-iconnectionpointcontainer-findconnectionpoint) předávání identifikátor IID rozhraní události, která vás zajímá. Pokud úspěšná, vrátí [IConnectionPoint](/windows/desktop/api/ocidl/nn-ocidl-iconnectionpoint) rozhraní na objekt bodu připojení.

- Volání [IConnectionPoint::Advise](/windows/desktop/api/ocidl/nf-ocidl-iconnectionpoint-advise) předání `IUnknown` z jímky událostí. Pokud úspěšná, vrátí `DWORD` představující připojení souboru cookie.

Jakmile úspěšně jste se zaregistrovali váš zájem o přijímání událostí, zavolá se podle události vyvolané zdrojový objekt metody rozhraní objektu události. Pokud už nepotřebujete příjem událostí, soubor cookie můžete předat zpět do spojovacího bodu prostřednictvím [IConnectionPoint::Unadvise](/windows/desktop/api/ocidl/nf-ocidl-iconnectionpoint-unadvise). Tím dojde k přerušení připojení mezi zdroje a jímky.

Dejte pozor, abyste se vyhnuli odkaz cykly, při zpracování událostí.

## <a name="see-also"></a>Viz také:

[Zpracování událostí](../atl/event-handling-and-atl.md)
