---
title: 'Postupy: Vytváření komponent COM bez registrace'
ms.date: 11/04/2016
helpviewer_keywords:
- COM components, registration-free
ms.assetid: 7e585d6a-0314-45b2-8f1b-cae9ac4df037
ms.openlocfilehash: 503c3e4399359d793ce660f36844d2edc6602146
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57416767"
---
# <a name="how-to-build-registration-free-com-components"></a>Postupy: Vytváření komponent COM bez registrace

Komponenty modelu COM bez registrace jsou komponenty modelu COM, které mají manifestů, které jsou součástí knihovny DLL.

### <a name="to-build-manifests-into-com-components"></a>K vytvoření manifestů do komponenty modelu COM

1. Otevření stránek vlastností projektu pro komponenty modelu COM.

1. Rozbalte **vlastnosti konfigurace** uzel a potom rozbalte **Nástroj Manifest** uzlu.

1. Vyberte **vstupní a výstupní** stránku vlastností a pak nastavte **vložit Manifest** vlastností **Ano**.

1. Klikněte na **OK**.

1. Sestavte řešení.

## <a name="see-also"></a>Viz také:

[Izolované aplikace](/windows/desktop/SbsCs/isolated-applications)<br/>
[Informace o sestavení vedle sebe](/windows/desktop/SbsCs/about-side-by-side-assemblies-)<br/>
[Postupy: Sestavení izolovaných aplikací pro zpracování součástí modelu COM](../build/how-to-build-isolated-applications-to-consume-com-components.md)
