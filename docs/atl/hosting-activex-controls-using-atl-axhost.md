---
title: Hostování ovládacích prvků ActiveX pomocí knihovny ATL AXHost | Dokumentace Microsoftu
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
ms.openlocfilehash: e26fd9e80b96c2b0196e3fd0e11b9c97f0f3bff3
ms.sourcegitcommit: 76fd30ff3e0352e2206460503b61f45897e60e4f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/13/2018
ms.locfileid: "39027203"
---
# <a name="hosting-activex-controls-using-atl-axhost"></a>Hostování ovládacích prvků ActiveX pomocí knihovny ATL AXHost
Ukázka v tomto tématu ukazuje, jak vytvořit AXHost a o tom, k hostování ovládacího prvku ActiveX pomocí různých funkce ATL. Také ukazuje, jak získat přístup k řízení a datovou sadu jímky událostí (použití [IDispEventImpl](../atl/reference/idispeventimpl-class.md)) z ovládacího prvku, který je hostitelem. Ukázka hostitelem ovládacího prvku kalendáře v hlavním okně nebo v podřízené okno.  
  
 Všimněte si, že definice symbolu USE_METHOD. Můžete změnit hodnotu tohoto symbolu se liší od 1 do 8. Hodnota symbolu Určuje, jak bude ovládací prvek vytvořen:  
  
-   Pro sudým číslem hodnoty USE_METHOD, volání za účelem vytvoření podtřídy hostitelského okna a převede ho na hostitele ovládacího prvku. Pro hodnoty s lichými čísly kód vytvoří podřízené okno, které slouží jako hostitel.  
  
-   Pro hodnoty USE_METHOD mezi 1 a 4, přístup k ovládacímu prvku a zpracování událostí, které můžete provést při volání metody, která vytvoří také hostitele. Hodnoty v rozmezí 5 až 8 dotazování hostitele pro rozhraní a zapojit jímky.  
  
Toto je souhrn:  
  
|USE_METHOD|Hostitel|Řízení přístupu a zpracování událostí|Jsme vám ukázali – funkce|  
|-----------------|----------|--------------------------------------|---------------------------|  
|1|Podřízené okno|Jeden krok|CreateControlLicEx|  
|2|Hlavní okno|Jeden krok|AtlAxCreateControlLicEx|  
|3|Podřízené okno|Jeden krok|CreateControlEx|  
|4|Hlavní okno|Jeden krok|AtlAxCreateControlEx|  
|5|Podřízené okno|Několik kroků|CreateControlLic|  
|6|Hlavní okno|Několik kroků|AtlAxCreateControlLic|  
|7|Podřízené okno|Několik kroků|CreateControl|  
|8|Hlavní okno|Několik kroků|AtlAxCreateControl|  
  
 [!code-cpp[NVC_ATL_AxHost#1](../atl/codesnippet/cpp/hosting-activex-controls-using-atl-axhost_1.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [Nejčastější dotazy k používání kontejnerů ovládacích prvků](../atl/atl-control-containment-faq.md)   
 [AtlAxCreateControl](reference/composite-control-global-functions.md#atlaxcreatecontrol)   
 [AtlAxCreateControlEx](reference/composite-control-global-functions.md#atlaxcreatecontrolex)   
 [AtlAxCreateControlLic](reference/composite-control-global-functions.md#atlaxcreatecontrollic)   
 [AtlAxCreateControlLicEx](reference/composite-control-global-functions.md#atlaxcreatecontrolex)   
 [Caxwindow2t – třída](../atl/reference/caxwindow2t-class.md)   
 [IAxWinHostWindowLic – rozhraní](../atl/reference/iaxwinhostwindowlic-interface.md)

