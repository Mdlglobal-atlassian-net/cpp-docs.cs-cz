---
title: "Možnosti, Průvodce jednoduchého objektu knihovny ATL | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: vc.codewiz.class.atl.simple.options
dev_langs: C++
helpviewer_keywords: ATL Simple Object Wizard, options
ms.assetid: 125fe179-942d-4181-8b82-33e92e1fd779
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c57206cb5be251e609f14132b4f0913a22b31534
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="options-atl-simple-object-wizard"></a>Možnosti, Průvodce jednoduchého objektu knihovny ATL
Tato stránka ATL Simple Object Wizard slouží k poskytují zvýšenou efektivitu a podpory chyb pro objekt.  
  
 Další informace o projekty knihovny ATL a třídy ATL COM, najdete v části [ATL COM – součásti plochy](../../atl/atl-com-desktop-components.md).  
  
 **Model vláken**  
 Určuje metodu pro správu vláken. Ve výchozím projektu používá **Apartment** dělení na vlákna.  
  
 V tématu [nastavení modelu vláken pro projekt](../../atl/specifying-the-threading-model-for-a-project-atl.md) Další informace.  
  
|Možnost|Popis|  
|------------|-----------------|  
|`Single`|Určuje, že objekt vždy běží v primární vlákno COM. V tématu [jedno vláknové objekty apartment](http://msdn.microsoft.com/library/windows/desktop/ms680112) a [InprocServer32](http://msdn.microsoft.com/library/windows/desktop/ms682390) Další informace.|  
|**Objektu Apartment**|Určuje, že objekt používá dělení objektu apartment. Ekvivalentní k jedné vláken typu apartment. Každý objekt komponentu apartment-threaded je přiřazen izolovaný prostor pro jeho vlákno dobu životnosti objektu; více vláken však lze použít pro více objektů. Každý apartment je vázaný na konkrétní vlákno a má Windows message pump (výchozí).<br /><br /> V tématu [jedno vláknové objekty apartment](http://msdn.microsoft.com/library/windows/desktop/ms680112) Další informace.|  
|**Obě**|Určuje, že objekt můžete použít buď objektu apartment nebo volných vláken, z které druh vlákno je vytvořen v závislosti.|  
|**Volné**|Určuje, že objekt používá volných vláken. Volných vláken je ekvivalentní k modelu objektu apartment s více vlákny. V tématu [vícevláknové izolované prostory](http://msdn.microsoft.com/library/windows/desktop/ms693421) Další informace.|  
|**Neutrální** (pouze systém Windows 2000)|Určuje, že objekt postupuje podle pokynů pro vícevláknové izolované prostory, ale můžete spustit na jakýkoli druh přístup z více vláken.|  
  
 **Agregace**  
 Označuje, zda objekt používá [agregace](http://msdn.microsoft.com/library/windows/desktop/ms686558). Agregovaný objekt zvolí, které rozhraní ke zveřejnění na klienty a rozhraní jsou viditelné, jako kdyby agregovaný objekt implementoval. Klienti agregovaného objektu komunikovat pouze s agregovaný objekt.  
  
|Možnost|Popis|  
|------------|-----------------|  
|Ano|Určuje, že se dají agregovat objektu. Výchozí nastavení|  
|Ne|Určuje, že není agregovaný objekt.|  
|Pouze|Určuje, že objekt musí být agregován.|  
  
 **Rozhraní**  
 Určuje typ rozhraní, které podporuje objekt. Ve výchozím nastavení podporuje objekt duální rozhraní.  
  
|Možnost|Popis|  
|------------|-----------------|  
|**Duální**|Určuje, že objekt podporuje rozhraní dual (jeho vtable má funkce vlastního rozhraní a pozdní vazba `IDispatch` metody). Umožňuje oba klienti COM a [automatizace řadiče](../../mfc/automation-clients.md) pro přístup k objektu. Výchozí nastavení|  
|**Vlastní**|Určuje, že objekt podporuje vlastní rozhraní (jeho vtable má funkce vlastního rozhraní). Vlastní rozhraní může být rychlejší než duální rozhraní, zejména přes hranice procesu.<br /><br /> -   **Automatizace kompatibilní** řadiče Automation umožňuje přístup k objektu, který podporuje vlastní rozhraní.|  
  
 **Podpora**  
 Určuje další podporu pro objekt.  
  
|Možnost|Popis|  
|------------|-----------------|  
|**ISupportErrorInfo**|Vytvoří podporu pro [ISupportErrorInfo](../../atl/reference/isupporterrorinfoimpl-class.md) rozhraní tak objekt může vrátit informace o chybě do klienta.|  
|**Body připojení**|Povoluje bod připojení pro objekt tím, že třídu objektu, které jsou odvozeny od [IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md).|  
|**Volné zařazování vláken**|Vytvoří objekt zařazení ukazatelů na rozhraní efektivně mezi vlákny v rámci jednoho procesu a volné zařazování vláken. K dispozici pro určení objekt **obě** jako model vláken.|  
|**IObjectWithSite (podpora objektu IE)**|Implementuje [IObjectWithSiteImpl](../../atl/reference/iobjectwithsiteimpl-class.md), který poskytuje jednoduchý způsob, jak podporovat komunikaci mezi objektem a jeho lokality v kontejneru.|  
  
## <a name="see-also"></a>Viz také  
 [Průvodce jednoduchého objektu knihovny ATL](../../atl/reference/atl-simple-object-wizard.md)   
 [Jednoduchého objektu knihovny ATL](../../atl/reference/adding-an-atl-simple-object.md)   
 [Proces serveru problémy dělení na vlákna](http://msdn.microsoft.com/library/windows/desktop/ms687205)

