---
title: "Povolení a zákaz služeb OLE DB | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB services [OLE DB], enabling and disabling
- service providers [OLE DB]
ms.assetid: 445f97eb-32a8-41c2-ad26-1169f78a074f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: dd98513201ef13f62a6eaf4a8ead90375df0f5ee
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="enabling-and-disabling-ole-db-services"></a>Povolení a zákaz služeb OLE DB
OLE DB služby Component Manager porovná zadány uživatelem těm, které jsou podporované poskytovatelem k určení, jestli jednotlivé komponenty služby může být volána pro uspokojení rozšířené funkce požadoval příjemce vlastnosti. Například pokud aplikace požaduje posuvný kurzor a poskytovatel podporuje jen dopředné kurzoru, že správce součástí služby vyvolá součást služby klientský kurzor stroj pro poskytnutí posuvného. Pokud se aplikace spoléhá na rozšířené funkce podporované ve výchozím nastavení v sadě řádků zprostředkovatele a aplikace explicitně nenastaví vlastností do žádosti o funkce, funkce nemusí zobrazit v sada řádků vrácená klientem Modul kurzoru. Být umožňuje vzájemnou spolupráci, musí aplikace vždy nastavená vlastností explicitní žádost o rozšířené funkce tam, kde je potřeba.  
  
 V některých případech může být potřeba zakázat jednotlivé služby rozhraní OLE DB pro práci s existující aplikacemi, které počítají týkající se vlastností poskytovatele. Služby rozhraní OLE DB zadejte možnost zakázat některé nebo všechny služby, na základě připojení připojení nebo pro všechny aplikace pomocí jednoho zprostředkovatele.  
  
## <a name="see-also"></a>Viz také  
 [Sdružování prostředků OLE DB a služby](../../data/oledb/ole-db-resource-pooling-and-services.md)