---
title: "Může hostovat více než jeden ovládací prvek v jednom okně? | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- controls [ATL], hosting multiple
- windows [C++], hosting multiple controls
ms.assetid: 3a967a1a-7e7e-42e3-8eed-f7bde912363f
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 5fa1a1b914d7d9725e8f2d9858f0481bb7aa24a4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="can-i-host-more-than-one-control-in-a-single-window"></a>Může hostovat více než jeden ovládací prvek v jednom okně?
Není možné k hostování více než jeden ovládací prvek v jednom okně ATL hostitele. Každý hostitel okno je určena pro obsahovat přesně jeden ovládací prvek v čase (umožňuje jednoduchý mechanismus pro zpracování zprávy reflexe a za řízení vedlejším vlastnostem). Pokud potřebujete uživatelům zobrazit více ovládacích prvků v jednom okně, je však představuje jednoduché vytvořit více oken hostitele jako podřízené objekty tohoto okna.  
  
## <a name="see-also"></a>Viz také  
 [Uzavření ovládacího prvku – nejčastější dotazy](../atl/atl-control-containment-faq.md)

