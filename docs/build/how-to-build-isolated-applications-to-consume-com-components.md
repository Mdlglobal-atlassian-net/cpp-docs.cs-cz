---
title: 'Postupy: Sestavení izolovaných aplikací pro zpracování součástí modelu COM'
ms.date: 11/04/2016
helpviewer_keywords:
- isolated applications [C++]
ms.assetid: 04587547-1174-44ab-bd99-1292358fba20
ms.openlocfilehash: 01b5c7056bd10a7c1f88df74b5c6b4aa78ff3fde
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57417876"
---
# <a name="how-to-build-isolated-applications-to-consume-com-components"></a>Postupy: Sestavení izolovaných aplikací pro zpracování součástí modelu COM

Izolované aplikace jsou aplikace, které mají manifesty integrovaný do programu. Můžete vytvořit izolované aplikace pro zpracování součástí modelu COM.

### <a name="to-add-com-references-to-manifests-of-isolated-applications"></a>Chcete-li přidat odkazy modelu COM do manifestu izolované aplikace

1. Otevření stránek vlastností projektu pro izolované aplikace.

1. Rozbalte **vlastnosti konfigurace** uzel a potom rozbalte **Nástroj Manifest** uzlu.

1. Vyberte **izolovaná komponenta COM** stránku vlastností a pak nastavte **název souboru komponenty** nastavte název komponenty modelu COM, který chcete izolované aplikace využívat.

1. Klikněte na **OK**.

### <a name="to-build-manifests-into-isolated-applications"></a>K vytvoření manifestů do izolované aplikace

1. Otevření stránek vlastností projektu pro izolované aplikace.

1. Rozbalte **vlastnosti konfigurace** uzel a potom rozbalte **Nástroj Manifest** uzlu.

1. Vyberte **vstupní a výstupní** stránku vlastností a pak nastavte **vložit Manifest** vlastností **Ano**.

1. Klikněte na **OK**.

1. Sestavte řešení.

## <a name="see-also"></a>Viz také:

[Izolované aplikace](/windows/desktop/SbsCs/isolated-applications)<br/>
[Informace o sestavení vedle sebe](/windows/desktop/SbsCs/about-side-by-side-assemblies-)
