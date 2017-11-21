---
title: "Testování internetových aplikací | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Web applications [MFC], testing
- debugging Web applications [MFC], testing applications
- testing [MFC], Internet applications
- debugging [MFC], Web applications
- Internet debugging and testing
ms.assetid: ac4c74e3-d4ad-4e19-8f6c-e270de067f01
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d246c6951b397e2eb888483f8afcdf2a822fd56d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="testing-internet-applications"></a>Testování internetových aplikací
Existují některé jedinečné testování výzvy na Internetu, zejména pro aplikace spuštěné na webovém serveru. Počáteční testování bude pravděpodobně provedeno pomocí připojení k serveru testovacího klienta jednoho uživatele. To bude hodit pro ladění kódu.  
  
 Budete také chtít otestovat v podmínkách reálného: s více klientů připojených přes vysokorychlostní připojení, jakož i sériové řádky nízkou rychlostí, včetně připojení modemu. Může být obtížné simulovat skutečné podmínky, ale určitě stojí výdaje možné scénáře doby návrhu a jejich spuštění. Pokud je to možné budete také chtít použít nástroje pro proveďte kapacitu a zátěžové testování. Určité třídy chyb, jako je například časování chyb, je obtížné najít a reprodukujte.  
  
 Jedním z problémů programování Internetu je jeho viditelnosti. Váš server může zpomalit mnoho přístupů k vaší lokality. Chcete server, abyste mohli řádně snížit. Chcete zabránit nic, které by mohly být destruktivní na počítači uživatele, pokud vaše aplikace selže (například poškození dat při zápisu do registru nebo při zápisu souborů cookie na straně klienta).  
  
## <a name="see-also"></a>Viz také  
 [Úlohy internetového programování MFC](../mfc/mfc-internet-programming-tasks.md)   
 [Základy internetového programování MFC](../mfc/mfc-internet-programming-basics.md)

