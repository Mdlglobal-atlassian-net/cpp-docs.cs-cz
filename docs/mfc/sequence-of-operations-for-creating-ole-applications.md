---
title: "Posloupnost operací při vytváření aplikací OLE | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- OLE applications [MFC], creating
- OLE applications [MFC]
- applications [OLE], creating
- applications [OLE]
ms.assetid: 84b0f606-36c1-4253-9cea-44427f0074b9
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d746baa0e279e309d78db4f111fb766cf471f692
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="sequence-of-operations-for-creating-ole-applications"></a>Posloupnost operací při vytváření aplikací OLE
Následující tabulka uvádí vaše role a role rozhraní framework při vytváření OLE propojování a vkládání aplikace. Tyto představují možnosti k dispozici pro místo posloupnost kroků provést.  
  
### <a name="creating-ole-applications"></a>Vytváření aplikací OLE  
  
|Úloha|Můžete provést|Nepodporuje rozhraní|  
|----------|------------|------------------------|  
|Vytvoření komponenty COM.|Spusťte Průvodce aplikací MFC. Zvolte **úplný server** nebo **mini serveru** v **složené podporu dokumentu** kartě.|Rozhraní framework generuje kostru aplikace s možnosti komponenty COM, které umožňují. Všechny funkce COM lze přenést do vaší stávající aplikace s pouze mírné úpravy.|  
|Vytvoření aplikace kontejnerů od začátku.|Spusťte Průvodce aplikací MFC. Zvolte **kontejneru** v **složené podporu dokumentu** kartě. Pomocí zobrazení tříd, přejděte do editoru zdrojového kódu. Zadejte kód pro funkce COM obslužné rutiny.|Rozhraní framework generuje kostru aplikace, které můžete vložit COM – objekty vytvořené pomocí aplikací modelu COM součást (server).|  
|Vytvořte aplikaci, která podporuje automatizace od začátku.|Spusťte Průvodce aplikací MFC. Zvolte **automatizace** z **upřesňující funkce** kartě. Pomocí zobrazení tříd vystavit metod a vlastností v aplikaci pro automatizaci.|Rozhraní framework generuje kostru aplikace, které je možné aktivovat a automatizované jiné aplikace.|  
  
## <a name="see-also"></a>Viz také  
 [Vytváření v rozhraní Framework](../mfc/building-on-the-framework.md)   
 [Posloupnost operací při sestavování aplikací MFC](../mfc/sequence-of-operations-for-building-mfc-applications.md)   
 [Posloupnost operací při vytváření ovládacích prvků ActiveX](../mfc/sequence-of-operations-for-creating-activex-controls.md)   
 [Posloupnost operací při vytváření databázových aplikací](../mfc/sequence-of-operations-for-creating-database-applications.md)
