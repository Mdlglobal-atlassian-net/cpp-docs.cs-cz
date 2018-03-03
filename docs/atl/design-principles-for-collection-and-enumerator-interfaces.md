---
title: "Navrhování kolekce a rozhraní pro výčty (ATL) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- enumerator interfaces
- collection interfaces
ms.assetid: ea19a39e-6333-41a1-be62-5435c236640e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8709274e1b95816dee01b4457993521dde5d5213
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="design-principles-for-collection-and-enumerator-interfaces"></a>Principy návrhu pro sběr a rozhraní pro výčty
Existují různé zásady za každý typ rozhraní:  
  
-   Poskytuje rozhraní, které je kolekce *náhodných* přístup k *jeden* položka v kolekci prostřednictvím **položky** metoda, umožňuje klientům zjistit, kolik položek jsou v kolekci prostřednictvím **počet** vlastnost, a často umožňuje klientům přidání a odebrání položek.  
  
-   Poskytuje rozhraní enumerátor *sériové* přístup k *více* položek v kolekci, je neumožňuje klienta, které chcete zjistit, kolik položek jsou v kolekci (dokud enumerátor zastaví vrácení položky), a neposkytuje žádné způsob přidání nebo odebrání položky.  
  
 Každý typ rozhraní hraje jinou roli při poskytování přístupu k elementů v kolekci.  
  
## <a name="see-also"></a>Viz také  
 [Kolekce a výčty](../atl/atl-collections-and-enumerators.md)

