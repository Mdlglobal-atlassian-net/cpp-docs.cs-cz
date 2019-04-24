---
title: Možnosti Průvodce stránky komponentami ATL Active Server
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.class.atl.asp.options
helpviewer_keywords:
- ATL Active Server Page Component Wizard, options
ms.assetid: 54f34e26-53c7-4456-9675-cb86e356bde0
ms.openlocfilehash: 7e9740a67f265484c349a4df644be882dba30c13
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62197364"
---
# <a name="options-atl-active-server-page-component-wizard"></a>Možnosti Průvodce stránky komponentami ATL Active Server

Pomocí této stránce průvodce komponenty ATL Active Server stránky můžete navrhnout poskytují zvýšenou efektivitu a chyba podpory pro objekt.

Další informace o projekty knihovny ATL a třídy knihovny ATL modelu COM, naleznete v tématu [desktopové komponenty ATL COM](../../atl/atl-com-desktop-components.md).

- **Model vláken**

   Označuje metodu pro správu vlákna. Ve výchozím nastavení, že projekt používá **objektu Apartment** dělení na vlákna.

   Zobrazit [určení modelu vláken projektu](../../atl/specifying-the-threading-model-for-a-project-atl.md) Další informace.

   |Možnost|Popis|
   |------------|-----------------|
   |**Jeden**|Určuje, že objekt používá jeden model vláken. V jedné modelu vláken objekt vždy běží v primárním vláknu COM. Zobrazit [jedno vláknové objekty apartment](/windows/desktop/com/single-threaded-apartments) a [InprocServer32](/windows/desktop/com/inprocserver32) Další informace.|
   |**Apartment**|Určuje, že objekt používá podprocesový model apartment. Odpovídá jediné vlákně. Každý objekt jako součást podprocesový model apartment je přiřazena objektu apartment pro jeho vlákna po celou dobu životnosti objektu. více vláken však můžete použít pro více objektů. Každý apartment se váže na konkrétní vlákno a má pumpu zpráv Windows (výchozí).<br /><br /> Zobrazit [jedno vláknové objekty apartment](/windows/desktop/com/single-threaded-apartments) Další informace.|
   |**Obojí**|Určuje, zda objekt můžete používat objektu apartment nebo volných vláken, ze které druh vlákno je vytvořen v závislosti.|
   |**Free**|Určuje, že objekt používá volných vláken. Volných vláken je ekvivalentní s více vlákny typu apartment modelu. Zobrazit [s více vlákny objekty apartment](/windows/desktop/com/multithreaded-apartments) Další informace.|
   |**Neutrální**|Určuje, že objekt pokyny pro vícevláknové izolované prostory se však můžete spustit na jakékoliv vlákno.|

- **Agregace**

   Označuje, zda objekt používá [agregace](/windows/desktop/com/aggregation). Agregovaný objekt zvolí, které rozhraní k tomu, aby klienti a jsou rozhraní vystavena jako by implementoval agregovaný objekt. Klienti agregovaný objekt komunikovat jen s agregovaný objekt.

   |Možnost|Popis|
   |------------|-----------------|
   |**Ano**|Určuje, že objekt se dají agregovat. Výchozí nastavení|
   |**Ne**|Určuje, že není agregovaný objekt.|
   |**Pouze**|Určuje, jestli objekt musí být agregován.|

- **Podpora**

   Další možnosti podpory:

   |Možnost|Popis|
   |------------|-----------------|
   |**ISupportErrorInfo**|Vytvoří podpora [ISupportErrorInfo](../../atl/reference/isupporterrorinfoimpl-class.md) rozhraní objektu lze klientovi vrátit informace o chybě.|
   |**Body připojení**|Umožňuje spojovací body pro svůj objekt tím, že jsou odvozeny z třídy objektu [IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md).|
   |**Volné zařazování vláken**|Vytvoří objekt volným zařazováním vláken a zařazování ukazatele rozhraní efektivně mezi vlákny v rámci stejného procesu. K dispozici pro objekt zadat buď **obě** nebo **Free** jako model vláken.|

## <a name="see-also"></a>Viz také:

[Průvodce komponentami ATL Active Server Pages](../../atl/reference/atl-active-server-page-component-wizard.md)<br/>
[Komponenta knihovny ATL Active Server Page](../../atl/reference/adding-an-atl-active-server-page-component.md)
