---
title: QueryInterface | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- QueryInterface
dev_langs:
- C++
helpviewer_keywords:
- interfaces, pointers
- interfaces, availability
- QueryInterface method
ms.assetid: 62fce95e-aafa-4187-b50b-e6611b74c3b3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c361bc9510c610f2004af9f09c061d6f4b8b8cd2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46057443"
---
# <a name="queryinterface"></a>QueryInterface

I když jsou mechanismy, které můžete vyjádřit objekt staticky (dříve, než je vytvořena instance) poskytuje funkce, je použít základní mechanismus COM `IUnknown` metodu s názvem [QueryInterface](/windows/desktop/api/unknwn/nf-unknwn-iunknown-queryinterface(q_)).

Každé rozhraní je odvozena od `IUnknown`, takže každý rozhraní obsahuje implementace `QueryInterface`. Bez ohledu na implementaci tato metoda dotazuje objektu pomocí identifikátor IID rozhraní, ke kterému volající požaduje ukazatel. Pokud objekt podporuje rozhraní, `QueryInterface` při volání také načte ukazatel rozhraní, `AddRef`. V opačném případě vrátí kód chyby: E_NOINTERFACE.

Všimněte si, že musí dodržovat [počítání odkazů](../atl/reference-counting.md) pravidla za všech okolností. Při volání `Release` na ukazatel rozhraní k snížen počet odkazů na nulu, neměli byste používat tento ukazatel znovu. Občas budete muset získat nestálý odkaz na objekt (to znamená, které staví na získání ukazatele na jedno z jeho rozhraní bez zvyšování počtu odkazů), ale není přijatelné pro toto provést zavoláním `QueryInterface` následovaný `Release`. Ukazatele získaného takovým způsobem, není platný a neměl by se používat. To méně zřejmé, kdy [_ATL_DEBUG_INTERFACES](reference/debugging-and-error-reporting-macros.md#_atl_debug_interfaces) je definován, takže definování toto makro je užitečný způsob počítání chyby hledání referencí.

## <a name="see-also"></a>Viz také

[Úvod do modelu COM](../atl/introduction-to-com.md)<br/>
[QueryInterface: Navigace v objektu](/windows/desktop/com/queryinterface--navigating-in-an-object)

