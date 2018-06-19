---
title: Může hostovat více než jeden ovládací prvek v jednom okně? | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- controls [ATL], hosting multiple
- windows [C++], hosting multiple controls
ms.assetid: 3a967a1a-7e7e-42e3-8eed-f7bde912363f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ceb9444b6371e261115bbf52ef5a249100772d1f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32356421"
---
# <a name="can-i-host-more-than-one-control-in-a-single-window"></a>Může hostovat více než jeden ovládací prvek v jednom okně?
Není možné k hostování více než jeden ovládací prvek v jednom okně ATL hostitele. Každý hostitel okno je určena pro obsahovat přesně jeden ovládací prvek v čase (umožňuje jednoduchý mechanismus pro zpracování zprávy reflexe a za řízení vedlejším vlastnostem). Pokud potřebujete uživatelům zobrazit více ovládacích prvků v jednom okně, je však představuje jednoduché vytvořit více oken hostitele jako podřízené objekty tohoto okna.  
  
## <a name="see-also"></a>Viz také  
 [Uzavření ovládacího prvku – nejčastější dotazy](../atl/atl-control-containment-faq.md)

