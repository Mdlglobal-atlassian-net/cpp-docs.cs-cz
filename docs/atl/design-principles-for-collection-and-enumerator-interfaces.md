---
title: Návrh rozhraní kolekce a výčtů (ATL) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- enumerator interfaces
- collection interfaces
ms.assetid: ea19a39e-6333-41a1-be62-5435c236640e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ab8b42804ca892c80971928b869e09ccdf479d68
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/05/2018
ms.locfileid: "37851324"
---
# <a name="design-principles-for-collection-and-enumerator-interfaces"></a>Principy návrhu rozhraní kolekce a výčtů
Existují různé MSDL za každý typ rozhraní:  
  
-   Poskytuje rozhraní kolekce *náhodné* přístup k *jeden* položky v kolekci prostřednictvím `Item` metoda, umožňuje klientům zjistit, kolik položek jsou v kolekci prostřednictvím `Count` vlastnost, a často umožňuje klientům přidávání a odebírání položek.  
  
-   Poskytuje enumerátor rozhraní *sériového portu* přístup k *více* položek v kolekci, je neumožňuje klientům zjistit, kolik položek jsou v kolekci (dokud enumerátor zastaví vrácení položky), a neposkytuje žádným způsobem přidávání nebo odebírání položek.  
  
 Každý typ rozhraní hraje různé roli při poskytování přístupu k prvkům v kolekci.  
  
## <a name="see-also"></a>Viz také  
 [Kolekce a výčty](../atl/atl-collections-and-enumerators.md)

