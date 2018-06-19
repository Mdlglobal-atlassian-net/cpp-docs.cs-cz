---
title: Navrhování kolekce a rozhraní pro výčty (ATL) | Microsoft Docs
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
ms.openlocfilehash: 05649cce0e80af6f54327545cef7b663d69babf9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32354916"
---
# <a name="design-principles-for-collection-and-enumerator-interfaces"></a>Principy návrhu pro sběr a rozhraní pro výčty
Existují různé zásady za každý typ rozhraní:  
  
-   Poskytuje rozhraní, které je kolekce *náhodných* přístup k *jeden* položka v kolekci prostřednictvím **položky** metoda, umožňuje klientům zjistit, kolik položek jsou v kolekci prostřednictvím **počet** vlastnost, a často umožňuje klientům přidání a odebrání položek.  
  
-   Poskytuje rozhraní enumerátor *sériové* přístup k *více* položek v kolekci, je neumožňuje klienta, které chcete zjistit, kolik položek jsou v kolekci (dokud enumerátor zastaví vrácení položky), a neposkytuje žádné způsob přidání nebo odebrání položky.  
  
 Každý typ rozhraní hraje jinou roli při poskytování přístupu k elementů v kolekci.  
  
## <a name="see-also"></a>Viz také  
 [Kolekce a výčty](../atl/atl-collections-and-enumerators.md)

