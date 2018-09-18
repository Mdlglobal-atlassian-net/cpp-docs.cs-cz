---
title: Možnosti, Průvodce jednoduchým objektem ATL | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.codewiz.class.atl.simple.options
dev_langs:
- C++
helpviewer_keywords:
- ATL Simple Object Wizard, options
ms.assetid: 125fe179-942d-4181-8b82-33e92e1fd779
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 548b75a3cee974538450534e25a091c56ae35014
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45707418"
---
# <a name="options-atl-simple-object-wizard"></a>Možnosti Průvodce jednoduchým objektem ATL

Na této stránce Průvodce jednoduchým objektem ATL navrhnout poskytují zvýšenou efektivitu a chyba podpory pro objekt.

Další informace o projekty knihovny ATL a třídy knihovny ATL modelu COM, naleznete v tématu [desktopové komponenty ATL COM](../../atl/atl-com-desktop-components.md).

- **Model vláken**

   Označuje metodu pro správu vlákna. Ve výchozím nastavení, že projekt používá **objektu Apartment** dělení na vlákna.

   Zobrazit [určení modelu vláken projektu](../../atl/specifying-the-threading-model-for-a-project-atl.md) Další informace.

   |Možnost|Popis|
   |------------|-----------------|
   |**Jeden**|Určuje, že objekt vždy běží v primárním vláknu COM. Zobrazit [jedno vláknové objekty apartment](/windows/desktop/com/single-threaded-apartments) a [InprocServer32](/windows/desktop/com/inprocserver32) Další informace.|
   |**Objektu Apartment**|Určuje, že objekt používá podprocesový model apartment. Odpovídá jediné vlákně. Každý objekt jako součást podprocesový model apartment je přiřazena objektu apartment pro jeho vlákna po celou dobu životnosti objektu. více vláken však můžete použít pro více objektů. Každý apartment se váže na konkrétní vlákno a má pumpu zpráv Windows (výchozí).<br /><br /> Zobrazit [jedno vláknové objekty apartment](/windows/desktop/com/single-threaded-apartments) Další informace.|
   |**Obojí**|Určuje, zda objekt můžete používat objektu apartment nebo volných vláken, ze které druh vlákno je vytvořen v závislosti.|
   |**Zdarma**|Určuje, že objekt používá volných vláken. Volných vláken je ekvivalentní s více vlákny typu apartment modelu. Zobrazit [s více vlákny objekty apartment](/windows/desktop/com/multithreaded-apartments) Další informace.|
   |**Neutrální**|Určuje, že objekt pokyny pro vícevláknové izolované prostory se však můžete spustit na jakékoliv vlákno.|

- **Agregace**

   Označuje, zda objekt používá [agregace](/windows/desktop/com/aggregation). Agregovaný objekt zvolí, které rozhraní k tomu, aby klienti a jsou rozhraní vystavena jako by implementoval agregovaný objekt. Klienti agregovaný objekt komunikovat jen s agregovaný objekt.

   |Možnost|Popis|
   |------------|-----------------|
   |**Ano**|Určuje, že objekt se dají agregovat. Výchozí nastavení|
   |**Ne**|Určuje, že není agregovaný objekt.|
   |**Pouze**|Určuje, jestli objekt musí být agregován.|

- **Rozhraní**

   Určuje typ rozhraní, které podporuje objektu. Ve výchozím nastavení podporuje duální rozhraní objektu.

   |Možnost|Popis|
   |------------|-----------------|
   |**Duální**|Určuje, že objekt podporuje duální rozhraní (jeho vtable má funkce vlastního rozhraní a pozdní vazby `IDispatch` metody). Umožňuje oba klienti modelu COM a [spustila samostatná instance](../../mfc/automation-clients.md) pro přístup k objektu. Výchozí nastavení|
   |**Vlastní**|Určuje, že objekt podporuje vlastní rozhraní (jeho vtable má vlastní funkce rozhraní). Vlastní rozhraní může být rychlejší než duální rozhraní, zejména přes hranice procesu.<br /><br /> -   **Automatizace kompatibilní** kontrolery automatizace umožňuje přístup k objektu, který podporuje vlastní rozhraní.|

- **Podpora**

   Určuje další podporu pro objekt.

   |Možnost|Popis|
   |------------|-----------------|
   |**ISupportErrorInfo**|Vytvoří podpora [ISupportErrorInfo](../../atl/reference/isupporterrorinfoimpl-class.md) rozhraní objektu lze klientovi vrátit informace o chybě.|
   |**Body připojení**|Umožňuje spojovací body pro svůj objekt tím, že jsou odvozeny z třídy objektu [IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md).|
   |**Volné zařazování vláken**|Vytvoří objekt volným zařazováním vláken a zařazování ukazatele rozhraní efektivně mezi vlákny v rámci stejného procesu. K dispozici se zadáním objektu **obě** jako model vláken.|
   |**IObjectWithSite** (podpora objektu aplikace Internet Explorer)|Implementuje [IObjectWithSiteImpl](../../atl/reference/iobjectwithsiteimpl-class.md), která poskytuje jednoduchý způsob, aby mohly podporovat komunikaci mezi objekt a jeho web v kontejneru.|

## <a name="see-also"></a>Viz také

[Průvodce jednoduchým objektem ATL](../../atl/reference/atl-simple-object-wizard.md)   
[Jednoduchý objekt knihovny ATL](../../atl/reference/adding-an-atl-simple-object.md)   
[Proces serveru potíže s vlákny](/windows/desktop/com/in-process-server-threading-issues)

