---
title: 'Postupy: Sestavení součásti modelu COM bez registrace'
ms.date: 11/04/2016
helpviewer_keywords:
- COM components, registration-free
ms.assetid: 7e585d6a-0314-45b2-8f1b-cae9ac4df037
ms.openlocfilehash: 783677c97835acc98751fc4a19f9405af752b71a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62188935"
---
# <a name="how-to-build-registration-free-com-components"></a>Postupy: Sestavení součásti modelu COM bez registrace

Komponenty modelu COM bez registrace jsou komponenty modelu COM, které mají manifesty integrované do knihoven DLL.

### <a name="to-build-manifests-into-com-components"></a>Sestavení manifestů do komponent modelu COM

1. Otevřete stránky vlastností projektu pro komponentu COM.

1. Rozbalte uzel **Vlastnosti konfigurace** a poté rozbalte uzel **Nástroj manifest** .

1. Vyberte stránku vlastností **vstup a výstup** a nastavte vlastnost pro **vložení manifestu** na **hodnotu Ano**.

1. Klikněte na tlačítko **OK**.

1. Sestavte řešení.

## <a name="see-also"></a>Viz také

[Postupy: Sestavení izolované aplikace pro zpracování součástí modelu COM](how-to-build-isolated-applications-to-consume-com-components.md)
