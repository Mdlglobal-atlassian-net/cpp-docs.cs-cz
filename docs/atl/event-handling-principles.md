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
ms.openlocfilehash: 066c8db60afed31ceba1c9ef6f4a10d5f842e608
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492146"
---
# <a name="event-handling-principles"></a>Principy zpracování událostí

Existují tři kroky společné pro všechny zpracování událostí. Budete potřebovat:

- Implementujte rozhraní události v objektu.

- Poraďte se se zdrojem událostí, který váš objekt chce přijmout události.

- Pokud objekt již nepotřebuje přijímat události, odradit zdroj události.

Způsob implementace rozhraní události bude záviset na typu. Rozhraní události může být vtable, Dual nebo IDispatch. Je až do návrháře zdroje událostí pro definování rozhraní; je to až do implementace tohoto rozhraní.

> [!NOTE]
>  I když neexistují žádné technické důvody, že rozhraní události nemůže být duální, je k dispozici řada dobrých důvodů návrhu, abyste se vyhnuli použití duálních. Jedná se však o rozhodnutí provedené návrhářem nebo implementací *zdroje*události. Vzhledem k tomu, že pracujete z perspektivy události `sink`, je třeba umožnit možnost, že nebudete mít žádnou volbu, ale implementovat rozhraní se dvěma událostmi. Další informace o duálních rozhraních naleznete v tématu [duální rozhraní a ATL](../atl/dual-interfaces-and-atl.md).

Doporučuje se, abyste zdroj událostí mohli rozdělit do tří kroků:

- Dotaz na zdrojový objekt pro [IConnectionPointContainer](/windows/win32/api/ocidl/nn-ocidl-iconnectionpointcontainer).

- Zavolejte [IConnectionPointContainer:: FindConnectionPoint](/windows/win32/api/ocidl/nf-ocidl-iconnectionpointcontainer-findconnectionpoint) a předejte IID rozhraní události, které vás zajímá. V případě úspěchu se vrátí rozhraní [IConnectionPoint](/windows/win32/api/ocidl/nn-ocidl-iconnectionpoint) objektu Connection Point.

- Zavolejte [IConnectionPoint:: Advise](/windows/win32/api/ocidl/nf-ocidl-iconnectionpoint-advise) `IUnknown` , který předává událost jímky. Pokud se to nezdaří, vrátí `DWORD` soubor cookie, který představuje připojení.

Po úspěšném zaregistrování vašeho zájmu při přijímání událostí budou metody v rozhraní události vašeho objektu volány v závislosti na událostech vyvolaných zdrojovým objektem. Když už nepotřebujete přijímat události, můžete soubor cookie předat zpátky do spojovacího bodu pomocí [IConnectionPoint:: Unadvise](/windows/win32/api/ocidl/nf-ocidl-iconnectionpoint-unadvise). Tím dojde k přerušení připojení mezi zdrojem a jímkou.

Buďte opatrní, abyste se vyhnuli referenčním cyklům při zpracování událostí.

## <a name="see-also"></a>Viz také:

[Zpracování událostí](../atl/event-handling-and-atl.md)
