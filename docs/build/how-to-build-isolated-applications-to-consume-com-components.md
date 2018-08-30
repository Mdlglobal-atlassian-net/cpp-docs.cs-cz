---
title: 'Postupy: sestavení izolovaných aplikací pro zpracování součástí modelu COM | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- isolated applications [C++]
ms.assetid: 04587547-1174-44ab-bd99-1292358fba20
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1b94a41aef1122a507a8966c475b9a87c69e3789
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43196829"
---
# <a name="how-to-build-isolated-applications-to-consume-com-components"></a>Postupy: Sestavení izolované aplikace pro zpracování součástí modelu COM
Izolované aplikace jsou aplikace, které mají manifesty integrovaný do programu. Můžete vytvořit izolované aplikace pro zpracování součástí modelu COM.  
  
### <a name="to-add-com-references-to-manifests-of-isolated-applications"></a>Chcete-li přidat odkazy modelu COM do manifestu izolované aplikace  
  
1.  Otevření stránek vlastností projektu pro izolované aplikace.  
  
2.  Rozbalte **vlastnosti konfigurace** uzel a potom rozbalte **Nástroj Manifest** uzlu.  
  
3.  Vyberte **izolovaná komponenta COM** stránku vlastností a pak nastavte **název souboru komponenty** nastavte název komponenty modelu COM, který chcete izolované aplikace využívat.  
  
4.  Klikněte na tlačítko **OK**.  
  
### <a name="to-build-manifests-into-isolated-applications"></a>K vytvoření manifestů do izolované aplikace  
  
1.  Otevření stránek vlastností projektu pro izolované aplikace.  
  
2.  Rozbalte **vlastnosti konfigurace** uzel a potom rozbalte **Nástroj Manifest** uzlu.  
  
3.  Vyberte **vstupní a výstupní** stránku vlastností a pak nastavte **vložit Manifest** vlastností **Ano**.  
  
4.  Klikněte na tlačítko **OK**.  
  
5.  Sestavte řešení.  
  
## <a name="see-also"></a>Viz také  
 [Izolované aplikace](/windows/desktop/SbsCs/isolated-applications)   
 [Informace o sestavení vedle sebe](/windows/desktop/SbsCs/about-side-by-side-assemblies-)