---
title: 'Postupy: Sestavení izolované aplikace pro zpracování součástí modelu COM'
ms.date: 11/04/2016
helpviewer_keywords:
- isolated applications [C++]
ms.assetid: 04587547-1174-44ab-bd99-1292358fba20
ms.openlocfilehash: 8ae3c51502267f202cbb85ea7be2a81dc3310410
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69493238"
---
# <a name="how-to-build-isolated-applications-to-consume-com-components"></a>Postupy: Sestavení izolované aplikace pro zpracování součástí modelu COM

Izolované aplikace jsou aplikace, které mají manifesty integrované do programu. Izolované aplikace můžete vytvořit pro využívání komponent modelu COM.

### <a name="to-add-com-references-to-manifests-of-isolated-applications"></a>Přidání odkazů COM na manifesty izolovaných aplikací

1. Otevřete stránky vlastností projektu pro izolovanou aplikaci.

1. Rozbalte uzel **Vlastnosti konfigurace** a poté rozbalte uzel **Nástroj manifest** .

1. Vyberte stránku vlastností **izolovaného modelu COM** a nastavte vlastnost **název souboru komponenty** na název komponenty modelu COM, kterou má izolovaná aplikace spotřebovat.

1. Klikněte na tlačítko **OK**.

### <a name="to-build-manifests-into-isolated-applications"></a>Sestavení manifestů do izolovaných aplikací

1. Otevřete stránky vlastností projektu pro izolovanou aplikaci.

1. Rozbalte uzel **Vlastnosti konfigurace** a poté rozbalte uzel **Nástroj manifest** .

1. Vyberte stránku vlastností **vstup a výstup** a nastavte vlastnost pro **vložení manifestu** na **hodnotu Ano**.

1. Klikněte na tlačítko **OK**.

1. Sestavte řešení.

## <a name="see-also"></a>Viz také

[Izolované aplikace](/windows/win32/SbsCs/isolated-applications)<br/>
[Sestavení vedle sebe](/windows/win32/SbsCs/about-side-by-side-assemblies-)
