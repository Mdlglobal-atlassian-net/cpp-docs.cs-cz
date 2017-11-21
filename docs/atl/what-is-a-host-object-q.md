---
title: Co je objekt hostitele? (ATL) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: host objects
ms.assetid: 4f8da992-b27e-45e8-b5e0-c8b1dcae4fac
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ab37e9a9d3a19f250f52d5f5c60de41968012625
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="what-is-a-host-object"></a>Co je objekt hostitele?
Objekt hostitele je objekt modelu COM, který představuje kontejneru ovládacího prvku ActiveX poskytl ATL pro konkrétní okno. Hostitel objektu podtřídy okně kontejner, aby ho můžete podle zprávy pro ovládací prvek, poskytuje rozhraní nezbytné kontejneru má být používána ovládacího prvku, a zpřístupňuje [IAxWinHostWindow](../atl/reference/iaxwinhostwindow-interface.md) a [ IAxWinAmbientDispatch](../atl/reference/iaxwinambientdispatch-interface.md) rozhraní, které se vám umožní nakonfigurovat prostředí ovládacího prvku.  
  
 Objekt hostitele můžete nastavit vlastnosti prostředí kontejneru.  
  
## <a name="see-also"></a>Viz také  
 [Uzavření ovládacího prvku – nejčastější dotazy](../atl/atl-control-containment-faq.md)

