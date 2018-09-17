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
ms.openlocfilehash: 6d2acabb6a5e9c35029b346097a66eaf1311826c
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45704025"
---
# <a name="how-to-build-isolated-applications-to-consume-com-components"></a>Postupy: Sestavení izolované aplikace pro zpracování součástí modelu COM

Izolované aplikace jsou aplikace, které mají manifesty integrovaný do programu. Můžete vytvořit izolované aplikace pro zpracování součástí modelu COM.

### <a name="to-add-com-references-to-manifests-of-isolated-applications"></a>Chcete-li přidat odkazy modelu COM do manifestu izolované aplikace

1. Otevření stránek vlastností projektu pro izolované aplikace.

1. Rozbalte **vlastnosti konfigurace** uzel a potom rozbalte **Nástroj Manifest** uzlu.

1. Vyberte **izolovaná komponenta COM** stránku vlastností a pak nastavte **název souboru komponenty** nastavte název komponenty modelu COM, který chcete izolované aplikace využívat.

1. Klikněte na tlačítko **OK**.

### <a name="to-build-manifests-into-isolated-applications"></a>K vytvoření manifestů do izolované aplikace

1. Otevření stránek vlastností projektu pro izolované aplikace.

1. Rozbalte **vlastnosti konfigurace** uzel a potom rozbalte **Nástroj Manifest** uzlu.

1. Vyberte **vstupní a výstupní** stránku vlastností a pak nastavte **vložit Manifest** vlastností **Ano**.

1. Klikněte na tlačítko **OK**.

1. Sestavte řešení.

## <a name="see-also"></a>Viz také

[Izolované aplikace](/windows/desktop/SbsCs/isolated-applications)<br/>
[Informace o sestavení vedle sebe](/windows/desktop/SbsCs/about-side-by-side-assemblies-)