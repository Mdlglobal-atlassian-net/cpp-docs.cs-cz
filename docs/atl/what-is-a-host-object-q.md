---
title: Co je objekt hostitele? (ATL) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- host objects
ms.assetid: 4f8da992-b27e-45e8-b5e0-c8b1dcae4fac
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8d197f02949f6eaaeee50b428338684135d1db27
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32357731"
---
# <a name="what-is-a-host-object"></a>Co je objekt hostitele?
Objekt hostitele je objekt modelu COM, který představuje kontejneru ovládacího prvku ActiveX poskytl ATL pro konkrétní okno. Hostitel objektu podtřídy okně kontejner, aby ho můžete podle zprávy pro ovládací prvek, poskytuje rozhraní nezbytné kontejneru má být používána ovládacího prvku, a zpřístupňuje [IAxWinHostWindow](../atl/reference/iaxwinhostwindow-interface.md) a [ IAxWinAmbientDispatch](../atl/reference/iaxwinambientdispatch-interface.md) rozhraní, které se vám umožní nakonfigurovat prostředí ovládacího prvku.  
  
 Objekt hostitele můžete nastavit vlastnosti prostředí kontejneru.  
  
## <a name="see-also"></a>Viz také  
 [Uzavření ovládacího prvku – nejčastější dotazy](../atl/atl-control-containment-faq.md)

