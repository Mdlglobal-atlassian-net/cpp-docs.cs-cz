---
title: Testování internetových aplikací
ms.date: 11/04/2016
helpviewer_keywords:
- Web applications [MFC], testing
- debugging Web applications [MFC], testing applications
- testing [MFC], Internet applications
- debugging [MFC], Web applications
- Internet debugging and testing
ms.assetid: ac4c74e3-d4ad-4e19-8f6c-e270de067f01
ms.openlocfilehash: e582fd006a49e672fb21c86b054b8d35f489698f
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57290937"
---
# <a name="testing-internet-applications"></a>Testování internetových aplikací

Existují některé jedinečné výzvy testování na Internetu, hlavně pro aplikace spuštěné na webovém serveru. Počáteční testování pravděpodobně se provede pomocí jednoho uživatele klienta připojení k serveru pro test. To bude užitečné pro ladění kódu.

Budete také chtít otestovat v podmínkách reálného: s více klientů připojených přes vysokorychlostní připojení, jakož i sériového portu řádky pomalé, včetně připojení modemu. Může být obtížné simulovat skutečné podmínky, ale určitě stojí útraty času návrhu možných scénářů a jejich spuštění. Pokud je to možné také můžete použít nástroje pro provádění kapacity a zátěžové testování. Určité třídy chyb, jako je například časování chyb, které je obtížné najít a reprodukovat.

Jedním z problémů programování na Internetu je viditelnost. Počet přístupů na váš web může zapříčinit zpomalení serveru. Chcete serveru služby a řádná degradace. Budete chtít zabránit cokoli, co může být destruktivní na počítači uživatele, pokud vaše aplikace selže (třeba poškození dat při zápisu do registru nebo při zápisu souborů cookie na straně klienta).

## <a name="see-also"></a>Viz také:

[Úlohy internetového programování MFC](../mfc/mfc-internet-programming-tasks.md)<br/>
[Základy internetového programování v prostředí MFC](../mfc/mfc-internet-programming-basics.md)
