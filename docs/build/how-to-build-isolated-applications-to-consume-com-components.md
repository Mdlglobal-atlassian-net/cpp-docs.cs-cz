---
title: "Postupy: sestavení izolované aplikace pro zpracování součástí modelu COM | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: isolated applications [C++]
ms.assetid: 04587547-1174-44ab-bd99-1292358fba20
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 80fe7391f41180cb4e5a6cfed5954a8ba821f44e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-build-isolated-applications-to-consume-com-components"></a>Postupy: Sestavení izolované aplikace pro zpracování součástí modelu COM
Izolované aplikace jsou aplikace, které mají manifest integrovaný do programu. Můžete vytvořit izolované aplikace pro zpracování součástí modelu COM.  
  
### <a name="to-add-com-references-to-manifests-of-isolated-applications"></a>Chcete-li přidat COM odkazy na manifesty izolované aplikace  
  
1.  Otevření stránek vlastností projektu pro izolované aplikace.  
  
2.  Rozbalte **vlastnosti konfigurace** uzel a potom rozbalte **Nástroj Manifest** uzlu.  
  
3.  Vyberte **izolované COM** stránku vlastností a pak nastavte **název souboru součást** vlastnost na název součásti COM, která chcete izolované aplikace využívat.  
  
4.  Click **OK**.  
  
### <a name="to-build-manifests-into-isolated-applications"></a>K vytvoření manifestů do izolované aplikace  
  
1.  Otevření stránek vlastností projektu pro izolované aplikace.  
  
2.  Rozbalte **vlastnosti konfigurace** uzel a potom rozbalte **Nástroj Manifest** uzlu.  
  
3.  Vyberte **vstup a výstup** stránku vlastností a pak nastavte **vložení manifestu** vlastností **Ano**.  
  
4.  Click **OK**.  
  
5.  Sestavte řešení.  
  
## <a name="see-also"></a>Viz také  
 [Izolované aplikace](http://msdn.microsoft.com/library/aa375190)   
 [O souběžně sdílená sestavení](http://msdn.microsoft.com/library/ff951640)