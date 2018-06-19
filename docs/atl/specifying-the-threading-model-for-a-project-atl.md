---
title: Určení modelu vláken pro projekt (ATL) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- _ATL_FREE_THREADED macro
- _ATL_APARTMENT_THREADED macro
- ATL, multithreading
- threading [ATL], models
- _ATL_SINGLE_THREADED macro
ms.assetid: 6b571078-521c-4f3e-9f08-482aa235a822
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6f807aa82a62fb703430ace5bc6be516e08ca9dc
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32359633"
---
# <a name="specifying-the-threading-model-for-a-project-atl"></a>Určení modelu vláken pro projekt (ATL)
Chcete-li určit model vláken projektu knihovny ATL k dispozici jsou následující makra:  
  
|– Makro|Pokyny k používání|  
|-----------|--------------------------|  
|_ATL_SINGLE_THREADED –|Určete, zda všechny vaše objektů, které používají jeden model vláken.|  
|_ATL_APARTMENT_THREADED –|Určete, zda jeden nebo více objektů použít dělení objektu apartment.|  
|_ATL_FREE_THREADED –|Zadejte, pokud jeden nebo více objektům používat volné nebo neutrální dělení na vlákna. Existující kód může obsahovat odkazy na ekvivalentní makro [_ATL_MULTI_THREADED](reference/compiler-options-macros.md#_atl_multi_threaded).|  
  
 Pokud nejsou definovány žádné z těchto makra pro svůj projekt, _atl_free_threaded – bude platit.  
  
 Makra ovlivnit výkon následujícím způsobem:  
  
-   Určení makra, která odpovídá k objektům v projektu může zlepšit výkon běhu.  
  
-   Určení vyšší úroveň makro, například pokud zadejte _atl_apartment_threaded – v případě, že všechny vaše objekty jsou jednotlivé zřetězený, budou mírně snížit výkon běhu.  
  
-   Zadání nižší úrovni makra, například pokud zadáte _atl_single_threaded – Pokud jeden nebo více objektům použijte dělení objektu apartment nebo volných vláken, může způsobit selhání v době běhu aplikace.  
  
 V tématu [možnosti, ATL Simple Object Wizard](../atl/reference/options-atl-simple-object-wizard.md) popis dělení na vlákna modely k dispozici pro objekt knihovny ATL.  
  
## <a name="see-also"></a>Viz také  
 [Koncepty](../atl/active-template-library-atl-concepts.md)

