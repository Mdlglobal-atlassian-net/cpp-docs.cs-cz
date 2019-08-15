---
title: Možnosti, Průvodce jednoduchým objektem ATL
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.class.atl.simple.options
helpviewer_keywords:
- ATL Simple Object Wizard, options
ms.assetid: 125fe179-942d-4181-8b82-33e92e1fd779
ms.openlocfilehash: e92f4909907645fc317590fbcc3601887346c642
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495160"
---
# <a name="options-atl-simple-object-wizard"></a>Možnosti, Průvodce jednoduchým objektem ATL

Pomocí této stránky Průvodce jednoduchým objektem ATL lze navrhnout zvýšení efektivity a podpory chyb pro objekt.

Další informace o projektech ATL a třídách ATL COM naleznete v tématu [komponenty ATL com Desktop](../../atl/atl-com-desktop-components.md).

- **Model vláken**

   Určuje metodu pro správu vláken. Ve výchozím nastavení používá projekt vlákno **Apartment** .

   Další informace najdete v tématu [Určení modelu vláken v projektu](../../atl/specifying-the-threading-model-for-a-project-atl.md) .

   |Možnost|Popis|
   |------------|-----------------|
   |**Konkrétní**|Určuje, že se objekt vždy spouští v primárním vlákně COM. Další informace najdete v tématu [s jedním vláknem](/windows/win32/com/single-threaded-apartments) a [InprocServer32](/windows/win32/com/inprocserver32) .|
   |**Apartment**|Určuje, že objekt používá vlákning Apartment. Ekvivalent jediného izolovaného vlákna. Každý objekt komponenty s vlákny typu Apartment je přiřazen k vláknu pro své vlákno, a to po dobu života objektu; Nicméně více vláken lze použít pro více objektů. Každý objekt Apartment je vázaný na konkrétní vlákno a má čerpadlo zpráv Windows (výchozí).<br /><br /> Další informace najdete v tématu [s jedním vláknem Apartment](/windows/win32/com/single-threaded-apartments) .|
   |**Protokoly**|Určuje, že objekt může použít buď Apartment, nebo volné vlákno, v závislosti na tom, jaký druh vlákna je vytvořen.|
   |**Free**|Určuje, že objekt používá volná vlákna. Bezplatné dělení na vlákna je ekvivalentní modelu apartment s více vlákny. Další informace najdete v tématu vícevláknové objekty [Apartment](/windows/win32/com/multithreaded-apartments) .|
   |**Jazyk**|Určuje, že objekt dodržuje pokyny pro vícevláknové objekty Apartment, ale lze ji provést na jakémkoli typu vlákna.|

- **Agregace**

   Určuje, zda objekt používá [agregaci](/windows/win32/com/aggregation). Agregovaný objekt slouží k výběru rozhraní, která se mají zpřístupnit klientům, a rozhraní jsou vystavena, jako by to agregovaný objekt implementoval. Klienti agregovaného objektu komunikují pouze s agregovaným objektem.

   |Možnost|Popis|
   |------------|-----------------|
   |**Ano**|Určuje, že objekt může být agregovaný. Výchozí nastavení|
   |**Ne**|Určuje, že objekt není agregovaný.|
   |**Pouze**|Určuje, že objekt musí být agregovaný.|

- **Rozhraní**

   Určuje typ rozhraní, které objekt podporuje. Ve výchozím nastavení objekt podporuje duální rozhraní.

   |Možnost|Popis|
   |------------|-----------------|
   |**Možnost**|Určuje, že objekt podporuje duální rozhraní (jeho vtable má funkce vlastního rozhraní a metody pozdní vazby `IDispatch` ). Umožňuje klientům modelu COM a [Automatizačním řadičům](../../mfc/automation-clients.md) přístup k objektu. Výchozí nastavení|
   |**Vlastní**|Určuje, že objekt podporuje vlastní rozhraní (jeho vtable má funkce vlastního rozhraní). Vlastní rozhraní může být rychlejší než duální rozhraní, zejména napříč hranicemi procesů.<br /><br /> - **Kompatibilní** s automatizací Umožňuje řadičům automatizace přístup k objektu, který má vlastní podporu rozhraní.|

- **Podpora**

   Označuje další podporu objektu.

   |Možnost|Popis|
   |------------|-----------------|
   |**ISupportErrorInfo**|Vytvoří podporu pro rozhraní [ISupportErrorInfo](../../atl/reference/isupporterrorinfoimpl-class.md) , aby mohl objekt vracet informace o chybách klientovi.|
   |**Body připojení**|Umožňuje spojovací body pro váš objekt tím, že třída objektu je odvozena od [IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md).|
   |**Zařazovací modul s volnými vlákny**|Vytvoří objekt zařazovacího modulu s volnými vlákny pro efektivní zařazování ukazatelů rozhraní mezi vlákny ve stejném procesu. K dispozici pro objekt, který určuje jak model vláken.|
   |**IObjectWithSite** (Podpora objektů IE)|Implementuje [IObjectWithSiteImpl](../../atl/reference/iobjectwithsiteimpl-class.md), která poskytuje jednoduchý způsob, jak podporovat komunikaci mezi objektem a jeho lokalitou v kontejneru.|

## <a name="see-also"></a>Viz také:

[Průvodce jednoduchým objektem ATL](../../atl/reference/atl-simple-object-wizard.md)<br/>
[Jednoduchý objekt ATL](../../atl/reference/adding-an-atl-simple-object.md)<br/>
[Problémy s vlákny v procesových procesech serveru](/windows/win32/com/in-process-server-threading-issues)
