---
title: 'Postupy: sestavení součásti modelu COM bez registrace | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- COM components, registration-free
ms.assetid: 7e585d6a-0314-45b2-8f1b-cae9ac4df037
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e54327344d61cc70e68b528c5f88f3d30f5d185a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32367856"
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
 [Postupy: Sestavení izolovaných aplikací pro zpracování součástí modelu COM](../build/how-to-build-isolated-applications-to-consume-com-components.md)