---
title: Možnosti, průvodce komponentami Active Server stránky knihovny ATL
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.class.atl.asp.options
helpviewer_keywords:
- ATL Active Server Page Component Wizard, options
ms.assetid: 54f34e26-53c7-4456-9675-cb86e356bde0
ms.openlocfilehash: c76ab7730256b007b66d54ca6753409926f7ae89
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495305"
---
# <a name="options-atl-active-server-page-component-wizard"></a>Možnosti, průvodce komponentami Active Server stránky knihovny ATL

Pomocí této stránky průvodce komponentami ATL Active Server Page Design můžete zvýšit efektivitu a podporu chyb pro daný objekt.

Další informace o projektech ATL a třídách ATL COM naleznete v tématu [komponenty ATL com Desktop](../../atl/atl-com-desktop-components.md).

- **Model vláken**

   Určuje metodu pro správu vláken. Ve výchozím nastavení používá projekt vlákno **Apartment** .

   Další informace najdete v tématu [Určení modelu vláken v projektu](../../atl/specifying-the-threading-model-for-a-project-atl.md) .

   |Možnost|Popis|
   |------------|-----------------|
   |**Konkrétní**|Určuje, že objekt používá model s jedním vláknem. V modelu jediného vlákna je objekt vždy spuštěn v primárním vlákně COM. Další informace najdete v tématu [s jedním vláknem](/windows/win32/com/single-threaded-apartments) a [InprocServer32](/windows/win32/com/inprocserver32) .|
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

- **Podpora**

   Další možnosti podpory:

   |Možnost|Popis|
   |------------|-----------------|
   |**ISupportErrorInfo**|Vytvoří podporu pro rozhraní [ISupportErrorInfo](../../atl/reference/isupporterrorinfoimpl-class.md) , aby mohl objekt vracet informace o chybách klientovi.|
   |**Body připojení**|Umožňuje spojovací body pro váš objekt tím, že třída objektu je odvozena od [IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md).|
   |**Zařazovací modul s volnými vlákny**|Vytvoří objekt zařazovacího modulu s volnými vlákny pro efektivní zařazování ukazatelů rozhraní mezi vlákny ve stejném procesu. K dispozici pro objekt, který jako model vláken Určuje buď **obojí** , nebo **Free** .|

## <a name="see-also"></a>Viz také:

[Průvodce komponentami ATL Active Server Pages](../../atl/reference/atl-active-server-page-component-wizard.md)<br/>
[Komponenta Active Server stránky ATL](../../atl/reference/adding-an-atl-active-server-page-component.md)
