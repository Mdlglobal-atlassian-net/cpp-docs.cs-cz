---
title: Hostování ovládacích prvků ActiveX pomocí knihovny ATL AXHost | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CAxWindow2T class
- Calendar control (ActiveX), hosting with ATL AXHost
- Calendar control (ActiveX)
- ActiveX controls [C++], hosting
- hosting ActiveX controls
- AXHost method
ms.assetid: 2c1200ec-effb-4814-820a-509519699468
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5057a077e8e778fa3d943b736d51d19af8f60fc6
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="hosting-activex-controls-using-atl-axhost"></a>Hostování ovládacích prvků ActiveX pomocí AXHost knihovny ATL
Ukázka v tomto tématu ukazuje postup vytvoření AXHost a jak pro hostování ovládacího prvku ActiveX pomocí různých funkcí ATL. Také ukazuje, jak pro přístup k řízení a jímka událostí (použití [IDispEventImpl](../atl/reference/idispeventimpl-class.md)) z ovládacího prvku, který je hostován. Ukázka hostitelem ovládacího prvku kalendář v hlavním okně nebo podřízeného okna.  
  
 Všimněte si, definice `USE_METHOD` symbol. Můžete změnit hodnotu tento symbol, který má být mezi 1 a 8. Určuje hodnota atributu symbol vytváření ovládacího prvku:  
  
-   Pro hodnoty sudé `USE_METHOD`, volání vytvoření podtřídy hostitele okna a převede jej na hostiteli ovládacího prvku. Lichých hodnoty vytvoří kód podřízeného okna, který funguje jako hostitel.  
  
-   Pro hodnoty `USE_METHOD` od 1 do 4, přístup k ovládacímu prvku a vnořování událostí, které se provádí v volání, které vytvoří také hostitele. Hodnoty v rozsahu 5 až 8 dotazování hostitele pro rozhraní a propojte jímky.  
  
 Zde je souhrn:  
  
|USE_METHOD|Hostitel|Řízení přístupu a událostí vnořování|Ukázán – funkce|  
|-----------------|----------|--------------------------------------|---------------------------|  
|1|Podřízená okna|Jeden krok|CreateControlLicEx|  
|2|Hlavní okno|Jeden krok|AtlAxCreateControlLicEx|  
|3|Podřízená okna|Jeden krok|CreateControlEx|  
|4|Hlavní okno|Jeden krok|AtlAxCreateControlEx|  
|5|Podřízená okna|Několik kroků|CreateControlLic|  
|6|Hlavní okno|Několik kroků|AtlAxCreateControlLic|  
|7|Podřízená okna|Několik kroků|CreateControl –|  
|8|Hlavní okno|Několik kroků|AtlAxCreateControl|  
  
 [!code-cpp[NVC_ATL_AxHost#1](../atl/codesnippet/cpp/hosting-activex-controls-using-atl-axhost_1.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [Uzavření ovládacího prvku – nejčastější dotazy](../atl/atl-control-containment-faq.md)   
 [AtlAxCreateControl](reference/composite-control-global-functions.md#atlaxcreatecontrol)   
 [AtlAxCreateControlEx](reference/composite-control-global-functions.md#atlaxcreatecontrolex)   
 [AtlAxCreateControlLic](reference/composite-control-global-functions.md#atlaxcreatecontrollic)   
 [AtlAxCreateControlLicEx](reference/composite-control-global-functions.md#atlaxcreatecontrolex)   
 [CAxWindow2T – třída](../atl/reference/caxwindow2t-class.md)   
 [IAxWinHostWindowLic – rozhraní](../atl/reference/iaxwinhostwindowlic-interface.md)

