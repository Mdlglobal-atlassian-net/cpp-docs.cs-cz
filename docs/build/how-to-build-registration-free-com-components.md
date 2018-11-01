---
title: 'Postupy: Sestavení součásti modelu COM bez registrace'
ms.date: 11/04/2016
helpviewer_keywords:
- COM components, registration-free
ms.assetid: 7e585d6a-0314-45b2-8f1b-cae9ac4df037
ms.openlocfilehash: 4f4ebf121b761c37969fa3f9788bda52d913f340
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50463528"
---
# <a name="how-to-build-registration-free-com-components"></a>Postupy: Sestavení součásti modelu COM bez registrace

Komponenty modelu COM bez registrace jsou komponenty modelu COM, které mají manifestů, které jsou součástí knihovny DLL.

### <a name="to-build-manifests-into-com-components"></a>K vytvoření manifestů do komponenty modelu COM

1. Otevření stránek vlastností projektu pro komponenty modelu COM.

1. Rozbalte **vlastnosti konfigurace** uzel a potom rozbalte **Nástroj Manifest** uzlu.

1. Vyberte **vstupní a výstupní** stránku vlastností a pak nastavte **vložit Manifest** vlastností **Ano**.

1. Klikněte na tlačítko **OK**.

1. Sestavte řešení.

## <a name="see-also"></a>Viz také

[Izolované aplikace](/windows/desktop/SbsCs/isolated-applications)<br/>
[Informace o sestavení vedle sebe](/windows/desktop/SbsCs/about-side-by-side-assemblies-)<br/>
[Postupy: Sestavení izolovaných aplikací pro zpracování součástí modelu COM](../build/how-to-build-isolated-applications-to-consume-com-components.md)