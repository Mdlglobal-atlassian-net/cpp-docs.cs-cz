---
title: 'Postupy: vytváření komponent COM bez registrace | Dokumentace Microsoftu'
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
ms.openlocfilehash: 1eaf9417f4d2b3b825933589556055772b84e057
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43197410"
---
# <a name="how-to-build-registration-free-com-components"></a>Postupy: Sestavení součásti modelu COM bez registrace
Komponenty modelu COM bez registrace jsou komponenty modelu COM, které mají manifestů, které jsou součástí knihovny DLL.  
  
### <a name="to-build-manifests-into-com-components"></a>K vytvoření manifestů do komponenty modelu COM  
  
1.  Otevření stránek vlastností projektu pro komponenty modelu COM.  
  
2.  Rozbalte **vlastnosti konfigurace** uzel a potom rozbalte **Nástroj Manifest** uzlu.  
  
3.  Vyberte **vstupní a výstupní** stránku vlastností a pak nastavte **vložit Manifest** vlastností **Ano**.  
  
4.  Klikněte na tlačítko **OK**.  
  
5.  Sestavte řešení.  
  
## <a name="see-also"></a>Viz také  
 [Izolované aplikace](/windows/desktop/SbsCs/isolated-applications)   
 [Informace o sestavení vedle sebe](/windows/desktop/SbsCs/about-side-by-side-assemblies-)   
 [Postupy: Sestavení izolovaných aplikací pro zpracování součástí modelu COM](../build/how-to-build-isolated-applications-to-consume-com-components.md)