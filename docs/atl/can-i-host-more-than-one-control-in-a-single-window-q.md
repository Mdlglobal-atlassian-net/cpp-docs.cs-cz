---
title: "Může hostovat více než jeden ovládací prvek v jednom okně? | Microsoft Docs"
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
- controls [ATL], hosting multiple
- windows [C++], hosting multiple controls
ms.assetid: 3a967a1a-7e7e-42e3-8eed-f7bde912363f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: be87c0bad9ab250593847cc24d16158030040054
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="can-i-host-more-than-one-control-in-a-single-window"></a>Může hostovat více než jeden ovládací prvek v jednom okně?
Není možné k hostování více než jeden ovládací prvek v jednom okně ATL hostitele. Každý hostitel okno je určena pro obsahovat přesně jeden ovládací prvek v čase (umožňuje jednoduchý mechanismus pro zpracování zprávy reflexe a za řízení vedlejším vlastnostem). Pokud potřebujete uživatelům zobrazit více ovládacích prvků v jednom okně, je však představuje jednoduché vytvořit více oken hostitele jako podřízené objekty tohoto okna.  
  
## <a name="see-also"></a>Viz také  
 [Uzavření ovládacího prvku – nejčastější dotazy](../atl/atl-control-containment-faq.md)

