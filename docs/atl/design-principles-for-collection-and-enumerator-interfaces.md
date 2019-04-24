---
title: Návrh rozhraní kolekce a výčtů (ATL)
ms.date: 11/04/2016
helpviewer_keywords:
- enumerator interfaces
- collection interfaces
ms.assetid: ea19a39e-6333-41a1-be62-5435c236640e
ms.openlocfilehash: f40c86d3bc8d9b4e4c752fe6657f6a5a14f19e0c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62234824"
---
# <a name="design-principles-for-collection-and-enumerator-interfaces"></a>Principy návrhu rozhraní kolekce a výčtů

Existují různé MSDL za každý typ rozhraní:

- Poskytuje rozhraní kolekce *náhodné* přístup k *jeden* položky v kolekci prostřednictvím `Item` metoda, umožňuje klientům zjistit, kolik položek jsou v kolekci prostřednictvím `Count` vlastnost, a často umožňuje klientům přidávání a odebírání položek.

- Poskytuje enumerátor rozhraní *sériového portu* přístup k *více* položek v kolekci, je neumožňuje klientům zjistit, kolik položek jsou v kolekci (dokud enumerátor zastaví vrácení položky), a neposkytuje žádným způsobem přidávání nebo odebírání položek.

Každý typ rozhraní hraje různé roli při poskytování přístupu k prvkům v kolekci.

## <a name="see-also"></a>Viz také:

[Kolekce a výčty](../atl/atl-collections-and-enumerators.md)
