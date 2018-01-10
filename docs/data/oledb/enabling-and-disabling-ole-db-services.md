---
title: "Povolení a zákaz služeb OLE DB | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- OLE DB services [OLE DB], enabling and disabling
- service providers [OLE DB]
ms.assetid: 445f97eb-32a8-41c2-ad26-1169f78a074f
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 59b1a50c44d5719cf3c699a14e5139d9e9816938
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="enabling-and-disabling-ole-db-services"></a>Povolení a zákaz služeb OLE DB
OLE DB služby Component Manager porovná zadány uživatelem těm, které jsou podporované poskytovatelem k určení, jestli jednotlivé komponenty služby může být volána pro uspokojení rozšířené funkce požadoval příjemce vlastnosti. Například pokud aplikace požaduje posuvný kurzor a poskytovatel podporuje jen dopředné kurzoru, že správce součástí služby vyvolá součást služby klientský kurzor stroj pro poskytnutí posuvného. Pokud se aplikace spoléhá na rozšířené funkce podporované ve výchozím nastavení v sadě řádků zprostředkovatele a aplikace explicitně nenastaví vlastností do žádosti o funkce, funkce nemusí zobrazit v sada řádků vrácená klientem Modul kurzoru. Být umožňuje vzájemnou spolupráci, musí aplikace vždy nastavená vlastností explicitní žádost o rozšířené funkce tam, kde je potřeba.  
  
 V některých případech může být potřeba zakázat jednotlivé služby rozhraní OLE DB pro práci s existující aplikacemi, které počítají týkající se vlastností poskytovatele. Služby rozhraní OLE DB zadejte možnost zakázat některé nebo všechny služby, na základě připojení připojení nebo pro všechny aplikace pomocí jednoho zprostředkovatele.  
  
## <a name="see-also"></a>Viz také  
 [Sdružování prostředků OLE DB a služby](../../data/oledb/ole-db-resource-pooling-and-services.md)