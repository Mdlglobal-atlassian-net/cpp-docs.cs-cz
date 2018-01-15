---
title: "Kde se uplatní vzdálená automatizace? | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: Remote Automation, DCOM
ms.assetid: 4c4c8176-cfc0-44f7-bc87-b690f069ad2f
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9ad6eef0bbaad7860e7f4310ce283efe18c668eb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="where-does-remote-automation-fit-in"></a>Kde se uplatní vzdálená automatizace?
Byla vydána v 1996 a je k dispozici v 32bitové a 64bitové verze platformy DCOM. Visual Basic team v Microsoft vždy zaznamenal jazyka Visual Basic jako pomocí automatizace umožňující komunikaci jeho součástí. Nedostatečná distribuované verze vážně omezenou využívat tyto možnosti v podnikovém prostředí, takže týmem vývoj Visual Basic 4.0 Enterprise Edition rozhodli prozkoumat vytvoření vlastní sadu součástí vzdálenou komunikaci pro automatizaci OLE a modelu COM. Hlavní cíl bylo zřejmé, zajistěte, aby výsledkem by být kompatibilní s a modelu DCOM může vyměnit, když jsou k dispozici. Potom pokračovalo implementovat vzdálené automatizace (RA) pro 16bitové a 32bitové verze platformy systému Windows.  
  
 Vzdálená automatizace není vázána k žádné konkrétní jazyk, ale až do vydání Visual C++ 4.2 Enterprise Edition, dodání pouze s 4.0 Visual Basic. Upozorňujeme, že je Vzdálená automatizace zcela subsumed model DCOM. Pokud máte možnost využívají model DCOM místo vzdálené automatizace v aplikacích, měli byste tak učinit. Nicméně existují scénáře, kde je vhodnější vzdálené automatizace:  
  
-   Všude, kde máte klienty 16 bitů.  
  
-   Jestliže vaše organizace není povoleno DCOM verze systému Windows NT nebo systému Windows 95 ještě.  
  
-   Pokud provádíte upgrade sady existující aplikace, která používá vzdálené automatizace součástí C++ použijte místo jeden nebo více komponent jazyka Visual Basic.  
  
 Musí být žádný rozdíl mezi programům vytvořeným používat vzdálené automatizace a ty na používání automatizace přes DCOM, a konfigurační nástroje usnadňují velmi přepínač operace mezi vzdálené automatizace a modelu DCOM. V důsledku toho je obtížné upgradovat aplikaci ze vzdálené automatizace na DCOM po infrastruktury na místě.  
  
## <a name="see-also"></a>Viz také  
 [Co přínosy vzdálené automatizace](what-does-remote-automation-provide-q.md)   
 [Historie modelu DCOM](../mfc/history-of-dcom.md)
