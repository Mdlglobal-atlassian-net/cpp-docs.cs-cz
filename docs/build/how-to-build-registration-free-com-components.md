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
ms.openlocfilehash: e0a9e1769ff0ba9a0589f9d59c3d1f1ed2fc5bcb
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45699852"
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