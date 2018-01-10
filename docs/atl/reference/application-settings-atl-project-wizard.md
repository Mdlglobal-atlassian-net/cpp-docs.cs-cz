---
title: "Nastavení aplikace, ATL projektu průvodce | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: vc.appwiz.atl.com.appset
dev_langs: C++
helpviewer_keywords: ATL Project Wizard, application settings
ms.assetid: d48c9fc5-f439-49fd-884c-8bcfa7d52991
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 12b7e383716d7cfa330bdfdebe21c33550669cc2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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

