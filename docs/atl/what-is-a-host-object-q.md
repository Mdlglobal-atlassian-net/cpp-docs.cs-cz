---
title: Co je objekt hostitele? (ATL) | Microsoft Docs
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
- host objects
ms.assetid: 4f8da992-b27e-45e8-b5e0-c8b1dcae4fac
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: da735caa84c133b9cdf63fae5df8bdd3d5f774b5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="what-is-a-host-object"></a>Co je objekt hostitele?
Objekt hostitele je objekt modelu COM, který představuje kontejneru ovládacího prvku ActiveX poskytl ATL pro konkrétní okno. Hostitel objektu podtřídy okně kontejner, aby ho můžete podle zprávy pro ovládací prvek, poskytuje rozhraní nezbytné kontejneru má být používána ovládacího prvku, a zpřístupňuje [IAxWinHostWindow](../atl/reference/iaxwinhostwindow-interface.md) a [ IAxWinAmbientDispatch](../atl/reference/iaxwinambientdispatch-interface.md) rozhraní, které se vám umožní nakonfigurovat prostředí ovládacího prvku.  
  
 Objekt hostitele můžete nastavit vlastnosti prostředí kontejneru.  
  
## <a name="see-also"></a>Viz také  
 [Uzavření ovládacího prvku – nejčastější dotazy](../atl/atl-control-containment-faq.md)

