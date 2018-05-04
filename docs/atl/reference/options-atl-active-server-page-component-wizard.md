---
title: Možnosti, Průvodce komponentou stránky ASP ATL | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.codewiz.class.atl.asp.options
dev_langs:
- C++
helpviewer_keywords:
- ATL Active Server Page Component Wizard, options
ms.assetid: 54f34e26-53c7-4456-9675-cb86e356bde0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 31549c812b4f523cb8026a0d0b15ae60e31cd1f8
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="options-atl-active-server-page-component-wizard"></a>Možnosti Průvodce komponentou stránky ASP knihovny ATL
Na této stránce Průvodce komponentou ATL Active Server stránky můžete navrhnout poskytují zvýšenou efektivitu a podpory chyb pro objekt.  
  
 Další informace o projekty knihovny ATL a třídy ATL COM, najdete v části [ATL COM – součásti plochy](../../atl/atl-com-desktop-components.md).  
  
 **Model vláken**  
 Určuje metodu pro správu vláken. Ve výchozím projektu používá **Apartment** dělení na vlákna.  
  
 V tématu [nastavení modelu vláken pro projekt](../../atl/specifying-the-threading-model-for-a-project-atl.md) Další informace.  
  
|Možnost|Popis|  
|------------|-----------------|  
|`Single`|Určuje, že objekt používá jeden model vláken. V jednom modelu vláken objektu vždy běží v primární COM vlákno. V tématu [jedno vláknové objekty apartment](http://msdn.microsoft.com/library/windows/desktop/ms680112) a [InprocServer32](http://msdn.microsoft.com/library/windows/desktop/ms682390) Další informace.|  
|**Objektu Apartment**|Určuje, že objekt používá dělení objektu apartment. Ekvivalentní k jedné vláken typu apartment. Každý objekt komponentu apartment-threaded je přiřazen izolovaný prostor pro jeho vlákno dobu životnosti objektu; více vláken však lze použít pro více objektů. Každý apartment je vázaný na konkrétní vlákno a má Windows message pump (výchozí).<br /><br /> V tématu [jedno vláknové objekty apartment](http://msdn.microsoft.com/library/windows/desktop/ms680112) Další informace.|  
|**Obě**|Určuje, že objekt můžete použít buď objektu apartment nebo volných vláken, z které druh vlákno je vytvořen v závislosti.|  
|**Volné**|Určuje, že objekt používá volných vláken. Volných vláken je ekvivalentní k modelu objektu apartment s více vlákny. V tématu [vícevláknové izolované prostory](http://msdn.microsoft.com/library/windows/desktop/ms693421) Další informace.|  
|**Neutrální**|Určuje, že objekt postupuje podle pokynů pro vícevláknové izolované prostory, ale můžete spustit na jakýkoli druh přístup z více vláken.|  
  
 **Agregace**  
 Označuje, zda objekt používá [agregace](http://msdn.microsoft.com/library/windows/desktop/ms686558). Agregovaný objekt zvolí, které rozhraní ke zveřejnění na klienty a rozhraní jsou viditelné, jako kdyby agregovaný objekt implementoval. Klienti agregovaného objektu komunikovat pouze s agregovaný objekt.  
  
|Možnost|Popis|  
|------------|-----------------|  
|**Ano**|Určuje, že se dají agregovat objektu. Výchozí nastavení|  
|**Ne**|Určuje, že není agregovaný objekt.|  
|**Pouze**|Určuje, že objekt musí být agregován.|  
  
 **Podpora**  
 (Popis prvku přidávaného)  
  
|Možnost|Popis|  
|------------|-----------------|  
|**ISupportErrorInfo**|Vytvoří podporu pro [ISupportErrorInfo](../../atl/reference/isupporterrorinfoimpl-class.md) rozhraní tak objekt může vrátit informace o chybě do klienta.|  
|**Body připojení**|Povoluje bod připojení pro objekt tím, že třídu objektu, které jsou odvozeny od [IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md).|  
|**Volné zařazování vláken**|Vytvoří objekt zařazení ukazatelů na rozhraní efektivně mezi vlákny v rámci jednoho procesu a volné zařazování vláken. K dispozici pro objekty buď **i** nebo **volné** jako model vláken.|  
  
## <a name="see-also"></a>Viz také  
 [Průvodce komponentou stránky ASP knihovny ATL](../../atl/reference/atl-active-server-page-component-wizard.md)   
 [Komponenty ASP knihovny ATL](../../atl/reference/adding-an-atl-active-server-page-component.md)

