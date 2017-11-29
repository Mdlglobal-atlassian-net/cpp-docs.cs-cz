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
ms.openlocfilehash: 9cbbef3b1f83b1b39c92ef689d5924b8962f32b6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="enabling-and-disabling-ole-db-services"></a>Povolení a zákaz služeb OLE DB
OLE DB služby Component Manager porovná zadány uživatelem těm, které jsou podporované poskytovatelem k určení, jestli jednotlivé komponenty služby může být volána pro uspokojení rozšířené funkce požadoval příjemce vlastnosti. Například pokud aplikace požaduje posuvný kurzor a poskytovatel podporuje jen dopředné kurzoru, že správce součástí služby vyvolá součást služby klientský kurzor stroj pro poskytnutí posuvného. Pokud se aplikace spoléhá na rozšířené funkce podporované ve výchozím nastavení v sadě řádků zprostředkovatele a aplikace explicitně nenastaví vlastností do žádosti o funkce, funkce nemusí zobrazit v sada řádků vrácená klientem Modul kurzoru. Být umožňuje vzájemnou spolupráci, musí aplikace vždy nastavená vlastností explicitní žádost o rozšířené funkce tam, kde je potřeba.  
  
 V některých případech může být potřeba zakázat jednotlivé služby rozhraní OLE DB pro práci s existující aplikacemi, které počítají týkající se vlastností poskytovatele. Služby rozhraní OLE DB zadejte možnost zakázat některé nebo všechny služby, na základě připojení připojení nebo pro všechny aplikace pomocí jednoho zprostředkovatele.  
  
## <a name="see-also"></a>Viz také  
 [OLE DB sdílení prostředků ve fondech a služby](../../data/oledb/ole-db-resource-pooling-and-services.md)