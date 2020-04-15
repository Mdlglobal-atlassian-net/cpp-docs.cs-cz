---
title: Zásady zpracování událostí (ATL)
ms.date: 11/04/2016
helpviewer_keywords:
- event handling, implementing
- event handling, advising event sources
- interfaces, event and event sink
- dual interfaces, event interfaces
- event handling, dual event interfaces
ms.assetid: d17ca7cb-54f2-4658-ab8b-b721ac56801d
ms.openlocfilehash: 2e810853e7c81f279039e0b3dfda5199d38deee2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319568"
---
# <a name="event-handling-principles"></a>Zásady zpracování událostí

Existují tři kroky společné pro všechny zpracování událostí. Budete muset:

- Implementujte rozhraní události na objektu.

- Informujte zdroj události, že objekt chce přijímat události.

- Nedoporučujte zdroj události, pokud objekt již nepotřebuje přijímat události.

Způsob implementace rozhraní události bude záviset na jeho typu. Rozhraní události může být vtable, duální nebo dispinterface. Je na návrháři zdroje událostí definovat rozhraní; je na vás, abyste toto rozhraní implementovali.

> [!NOTE]
> Ačkoli neexistují žádné technické důvody, že rozhraní události nemůže být duální, existuje řada dobrých důvodů návrhu, aby se zabránilo použití duals. Toto je však rozhodnutí provedené návrhářem/realizátorem *zdroje*události . Vzhledem k tomu, že pracujete z pohledu události `sink`, musíte povolit možnost, že nemusíte mít jinou možnost, než implementovat duální rozhraní událostí. Další informace o duálních rozhraních naleznete [v tématu Duální rozhraní a knihovna ATL](../atl/dual-interfaces-and-atl.md).

Poradenství zdroje události lze rozdělit do tří kroků:

- Dotaz na zdrojový objekt pro [iConnectionPointContainer](/windows/win32/api/ocidl/nn-ocidl-iconnectionpointcontainer).

- Volání [IConnectionPointContainer::FindConnectionPoint](/windows/win32/api/ocidl/nf-ocidl-iconnectionpointcontainer-findconnectionpoint) předání IID rozhraní události, které vás zajímá. Pokud bude úspěšná, vrátí se rozhraní [IConnectionPoint](/windows/win32/api/ocidl/nn-ocidl-iconnectionpoint) na objektu spojovacího bodu.

- Volání [iConnectionPoint::Poradit](/windows/win32/api/ocidl/nf-ocidl-iconnectionpoint-advise) předání `IUnknown` jímky události. Pokud je úspěšná, `DWORD` vrátí se soubor cookie představující připojení.

Jakmile úspěšně zaregistrujete svůj zájem o příjem událostí, metody na rozhraní událostí objektu budou volány podle událostí vypálených zdrojovým objektem. Pokud již nepotřebujete přijímat události, můžete soubor cookie předat zpět do spojovacího bodu přes [iConnectionPoint::Unadvise](/windows/win32/api/ocidl/nf-ocidl-iconnectionpoint-unadvise). Tím dojde k přerušení spojení mezi zdrojem a jímkou.

Při zpracování událostí dávejte pozor, abyste se vyhnuli referenčním cyklům.

## <a name="see-also"></a>Viz také

[Zpracování událostí](../atl/event-handling-and-atl.md)
