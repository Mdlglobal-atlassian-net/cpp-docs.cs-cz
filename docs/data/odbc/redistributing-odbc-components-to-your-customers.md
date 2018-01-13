---
title: "Redistribuce součástí rozhraní ODBC vašim zákazníkům | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- ODBC components, redistributing
- ODBC, distributing components
- components [C++], distributing
- ODBC Administrator
- components [C++]
- components [C++], redistributing
ms.assetid: 17b065b4-a307-4b89-99ac-d05831cfab87
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: aad9f1dbd4542ad763e7303d9a750f1856208025
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="redistributing-odbc-components-to-your-customers"></a>Redistribuce součástí rozhraní ODBC vašim zákazníkům
Pokud zahrnete funkci programů správce rozhraní ODBC do své aplikace, je nutné také distribuovat uživatelům. soubory, které spustit tyto programy. Tyto soubory rozhraní ODBC jsou umístěny v adresáři \OS\System z disku CD-ROM Visual C++. Soubor Redistrb.wri a licenční smlouvy ve stejném adresáři obsahovat seznam ODBC soubory, které je možné znovu distribuovat.  
  
 V dokumentaci pro všechny ODBC – ovladače, které máte v plánu pro odeslání. Budete muset určit, které knihovny DLL a další soubory pro odeslání. Doporučujeme přečíst [Redistribuce součástí rozhraní ODBC vašim zákazníkům](../../data/odbc/redistributing-odbc-components-to-your-customers.md), která vysvětluje, jak Redistribuce součástí rozhraní ODBC.  
  
 Kromě toho musíte zahrnout jeden další soubor ve většině případů. Odbccr32.dll je knihovna kurzorů rozhraní ODBC. Tato knihovna nabízí ovladače úrovně 1 schopnosti produktu posun vpřed a zpět. Také nabízí možnost podpory snímků. Další informace o knihovny kurzorů ODBC najdete v tématu [ODBC: knihovny kurzorů ODBC](../../data/odbc/odbc-the-odbc-cursor-library.md).  
  
 Následující témata obsahují další informace o použití rozhraní ODBC s třídami databází:  
  
-   [ODBC: Knihovna kurzorů rozhraní ODBC](../../data/odbc/odbc-the-odbc-cursor-library.md)  
  
-   [ODBC: Konfigurace zdroje dat ODBC](../../data/odbc/odbc-configuring-an-odbc-data-source.md)  
  
-   [ODBC: Přímé volání funkcí rozhraní API ODBC](../../data/odbc/odbc-calling-odbc-api-functions-directly.md)  
  
## <a name="see-also"></a>Viz také  
 [ODBC – základy](../../data/odbc/odbc-basics.md)   
 [Správce rozhraní ODBC](../../data/odbc/odbc-administrator.md)