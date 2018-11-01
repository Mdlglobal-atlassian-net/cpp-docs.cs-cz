---
title: Návrh rozhraní kolekce a výčtů (ATL)
ms.date: 11/04/2016
helpviewer_keywords:
- enumerator interfaces
- collection interfaces
ms.assetid: ea19a39e-6333-41a1-be62-5435c236640e
ms.openlocfilehash: 8c7f782f52391b162a8b32a97961269178999ee0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50538200"
---
# <a name="design-principles-for-collection-and-enumerator-interfaces"></a>Principy návrhu rozhraní kolekce a výčtů

Existují různé MSDL za každý typ rozhraní:

- Poskytuje rozhraní kolekce *náhodné* přístup k *jeden* položky v kolekci prostřednictvím `Item` metoda, umožňuje klientům zjistit, kolik položek jsou v kolekci prostřednictvím `Count` vlastnost, a často umožňuje klientům přidávání a odebírání položek.

- Poskytuje enumerátor rozhraní *sériového portu* přístup k *více* položek v kolekci, je neumožňuje klientům zjistit, kolik položek jsou v kolekci (dokud enumerátor zastaví vrácení položky), a neposkytuje žádným způsobem přidávání nebo odebírání položek.

Každý typ rozhraní hraje různé roli při poskytování přístupu k prvkům v kolekci.

## <a name="see-also"></a>Viz také

[Kolekce a výčty](../atl/atl-collections-and-enumerators.md)

