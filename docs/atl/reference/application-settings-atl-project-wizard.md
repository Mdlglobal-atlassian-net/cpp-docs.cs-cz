---
title: Nastavení aplikace, ATL projektu průvodce | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.appwiz.atl.com.appset
dev_langs:
- C++
helpviewer_keywords:
- ATL Project Wizard, application settings
ms.assetid: d48c9fc5-f439-49fd-884c-8bcfa7d52991
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 47fbf95451834e5f8c41e8b6d7e5af7a9746bb85
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32357402"
---
# <a name="application-settings-atl-project-wizard"></a>Nastavení aplikace, Průvodce projektem knihovny ATL
Použití **nastavení aplikace** stránce Průvodce projektu knihovny ATL návrhu a přidávat do nového projektu knihovny ATL základní funkce.  
  
## <a name="server-type"></a>Typ serveru  
 Vyberte jednu ze tří typů serveru:  
  
 **Dynamická knihovna (DLL)**  
 Vyberte, chcete-li vytvořit server v procesu.  
  
 **Spustitelný soubor (EXE)**  
 Vyberte, chcete-li vytvořit místní server mimo proces. Tato možnost není povolena podpora MFC nebo modelu COM + 1.0. Neumožňuje sloučení proxy/stub kódu.  
  
 **Služba (EXE)**  
 Vyberte, chcete-li vytvořit aplikaci systému Windows, která běží na pozadí při spuštění systému Windows. Tato možnost není povolena podpora MFC nebo modelu COM + 1.0 nebo nepovoluje slučování proxy/stub kódu.  
  
## <a name="additional-options"></a>Další možnosti  
  
> [!NOTE]
>  Všechny další možnosti jsou dostupné pro pouze projektů knihovny DLL.  
  
 **Povolit slučování proxy/stub kódu**  
 Vyberte **Povolit slučování proxy/stub kódu** zaškrtávací políčko pro vaše pohodlí při zařazování rozhraní je vyžadován. Tuto možnost umístí proxy a stub kód generovaný MIDL ve stejné spustitelného souboru jako server.  
  
 **Podpora MFC**  
 Vyberte, chcete-li určit, že objektu tvoří Podpora MFC. Tato možnost váš projekt odkazuje na knihovny MFC tak, aby vám přístup k libovolnému třídy a funkce, které obsahují.  
  
 **Podpora COM + 1.0**  
 Vyberte, chcete-li změnit nastavení sestavení projektu tak, aby mohl podporovat komponenty modelu COM + 1.0. Kromě standardní seznamu knihoven průvodce přidá comsvcs.lib knihovny specifické komponenty modelu COM + 1.0  
  
 Kromě toho mtxex.dll zpoždění načíst v hostitelském systému, pokud je aplikace spuštěna.  
  
-   **Podpora registrátora součást** Pokud projektu knihovny ATL obsahuje podporu pro komponenty modelu COM + 1.0, můžete nastavit tuto možnost. Registrátor komponent umožňuje vaší objekt modelu COM + 1.0, který chcete získat seznam součástí, zaregistrovat součásti nebo zrušit registraci součásti (jednotlivě nebo všechny najednou).  
  
## <a name="see-also"></a>Viz také  
 [Průvodce projektem knihovny ATL](../../atl/reference/atl-project-wizard.md)   
 [Vytvoření projektu knihovny ATL](../../atl/reference/creating-an-atl-project.md)   
 [Výchozí konfigurace projektu ATL](../../atl/reference/default-atl-project-configurations.md)

