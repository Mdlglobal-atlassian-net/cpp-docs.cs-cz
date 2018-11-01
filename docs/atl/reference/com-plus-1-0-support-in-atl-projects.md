---
title: Podpora COM + 1.0 v projektech ATL
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.ATL.MTS
helpviewer_keywords:
- ATL projects, COM+ 1.0 support
ms.assetid: 51fb08ac-d632-4657-a4e0-d3f989f0b6f8
ms.openlocfilehash: 4bc7683d6121dec748e30c1ea717042b9cf1ecbc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50562458"
---
# <a name="com-10-support-in-atl-projects"></a>Podpora COM + 1.0 v projektech ATL

Můžete použít [Průvodce projektem ATL](../../atl/reference/creating-an-atl-project.md) vytvořit projekt pomocí základní podporu pro komponenty modelu COM + 1.0.

COM + 1.0 je určená pro vývoj distribuovaných aplikací založených na komponentách. Také poskytuje infrastrukturu prostředí run-time pro nasazení a správě těchto aplikací.

Pokud vyberete **podporu modelu COM + 1.0** , zaškrtněte políčko v Průvodci změní skript sestavení v kroku odkaz. Konkrétně modelu COM + 1.0 projektu odkazy na následující knihovny:

- Comsvcs.lib

- Mtxguid.lib

Pokud vyberete **podporu modelu COM + 1.0** zaškrtávací políčko, můžete také vybrat **registrátora komponent podporu**. Registrátora komponent umožňuje váš objekt modelu COM + 1.0 mohl získat seznam součástí, zaregistrovat součásti nebo zrušit registraci součásti (jednotlivě nebo celou najednou).

## <a name="see-also"></a>Viz také

[Základy ATL – objekty COM](../../atl/fundamentals-of-atl-com-objects.md)<br/>
[Programování s použitím knihovny ATL a běhového kódu jazyka C](../../atl/programming-with-atl-and-c-run-time-code.md)<br/>
[Výchozí konfigurace projektu ATL](../../atl/reference/default-atl-project-configurations.md)

