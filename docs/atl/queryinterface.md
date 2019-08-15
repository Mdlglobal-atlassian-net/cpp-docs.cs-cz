---
title: QueryInterface
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- interfaces, pointers
- interfaces, availability
- QueryInterface method
ms.assetid: 62fce95e-aafa-4187-b50b-e6611b74c3b3
ms.openlocfilehash: de2762cff3d697261e159336d866a5a7cb10fafa
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492006"
---
# <a name="queryinterface"></a>QueryInterface

I když existují mechanismy, pomocí kterých může objekt vyjadřovat funkce, které poskytuje staticky (před vytvořením instance), základní mechanismus com je použít `IUnknown` metodu nazvanou [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q_)).

Každé rozhraní je odvozeno `IUnknown`z, takže každé rozhraní má `QueryInterface`implementaci. Bez ohledu na implementaci Tato metoda dotazuje objekt pomocí IID rozhraní, na které volající chce ukazatel. Pokud objekt podporuje toto rozhraní, `QueryInterface` načte ukazatel na rozhraní a zároveň zavolá. `AddRef` V opačném případě vrátí kód chyby E_NOINTERFACE.

Všimněte si, že je nutné vždy dodržovat pravidla [počítání odkazů](../atl/reference-counting.md) . Pokud voláte `Release` ukazatel rozhraní, chcete-li snížit počet odkazů na nulu, neměli byste tento ukazatel používat znovu. Občas může být nutné získat Slabý odkaz na objekt (to znamená, že můžete chtít získat ukazatel na jedno z jeho rozhraní bez zvýšení počtu odkazů), ale není přijatelné, pokud to uděláte voláním metody `QueryInterface` `Release`následovaný. Ukazatel získaný takovým způsobem je neplatný a neměl by být použit. Tato možnost bude přehlednější, když je definována [_ATL_DEBUG_INTERFACES](reference/debugging-and-error-reporting-macros.md#_atl_debug_interfaces) , takže definování tohoto makra je užitečný způsob, jak najít chyby počítání odkazů.

## <a name="see-also"></a>Viz také:

[Úvod do modelu COM](../atl/introduction-to-com.md)<br/>
[QueryInterface Navigace v objektu](/windows/win32/com/queryinterface--navigating-in-an-object)
