---
title: QueryInterface
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- interfaces, pointers
- interfaces, availability
- QueryInterface method
ms.assetid: 62fce95e-aafa-4187-b50b-e6611b74c3b3
ms.openlocfilehash: 28f3781706981b06d49829c0277014c09574ef6b
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57816058"
---
# <a name="queryinterface"></a>QueryInterface

I když jsou mechanismy, které můžete vyjádřit objekt staticky (dříve, než je vytvořena instance) poskytuje funkce, je použít základní mechanismus COM `IUnknown` metodu s názvem [QueryInterface](/windows/desktop/api/unknwn/nf-unknwn-iunknown-queryinterface(q_)).

Každé rozhraní je odvozena od `IUnknown`, takže každý rozhraní obsahuje implementace `QueryInterface`. Bez ohledu na implementaci tato metoda dotazuje objektu pomocí identifikátor IID rozhraní, ke kterému volající požaduje ukazatel. Pokud objekt podporuje rozhraní, `QueryInterface` při volání také načte ukazatel rozhraní, `AddRef`. V opačném případě vrátí kód chyby: E_NOINTERFACE.

Všimněte si, že musí dodržovat [počítání odkazů](../atl/reference-counting.md) pravidla za všech okolností. Při volání `Release` na ukazatel rozhraní k snížen počet odkazů na nulu, neměli byste používat tento ukazatel znovu. Občas budete muset získat nestálý odkaz na objekt (to znamená, které staví na získání ukazatele na jedno z jeho rozhraní bez zvyšování počtu odkazů), ale není přijatelné pro toto provést zavoláním `QueryInterface` následovaný `Release`. Ukazatele získaného takovým způsobem, není platný a neměl by se používat. To méně zřejmé, kdy [_ATL_DEBUG_INTERFACES](reference/debugging-and-error-reporting-macros.md#_atl_debug_interfaces) je definován, takže definování toto makro je užitečný způsob počítání chyby hledání referencí.

## <a name="see-also"></a>Viz také:

[Úvod do modelu COM](../atl/introduction-to-com.md)<br/>
[QueryInterface: Navigace v objektu](/windows/desktop/com/queryinterface--navigating-in-an-object)
