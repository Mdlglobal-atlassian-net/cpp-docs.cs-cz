---
title: "Postupy: sestavení součásti modelu COM bez registrace | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: COM components, registration-free
ms.assetid: 7e585d6a-0314-45b2-8f1b-cae9ac4df037
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: bba711f88a53a3d9b6f9eae1faed09670e95d497
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-build-registration-free-com-components"></a>Postupy: Sestavení součásti modelu COM bez registrace
Komponenty modelu COM bez registrace jsou komponenty modelu COM, které mají manifest integrovány do knihovny DLL.  
  
### <a name="to-build-manifests-into-com-components"></a>K vytvoření manifestů do komponenty modelu COM  
  
1.  Otevření stránek vlastností projektu pro komponenty modelu COM.  
  
2.  Rozbalte **vlastnosti konfigurace** uzel a potom rozbalte **Nástroj Manifest** uzlu.  
  
3.  Vyberte **vstup a výstup** stránku vlastností a pak nastavte **vložení manifestu** vlastností **Ano**.  
  
4.  Click **OK**.  
  
5.  Sestavte řešení.  
  
## <a name="see-also"></a>Viz také  
 [Izolované aplikace](http://msdn.microsoft.com/library/aa375190)   
 [O souběžně sdílená sestavení](http://msdn.microsoft.com/library/ff951640)   
 [Postupy: sestavení izolované aplikace pro zpracování součástí modelu COM](../build/how-to-build-isolated-applications-to-consume-com-components.md)