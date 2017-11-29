---
title: "Určení typu přístupového objektu | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- rowsets [C++], data types
- accessors [C++], types
ms.assetid: 22483dd2-f4e0-4dcb-8e4d-cd43a9c1a3db
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 6eebc119186a5a57fa1cf2c5e0c80479ef4cdcf3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="determining-which-type-of-accessor-to-use"></a>Určení použitého typu přístupového objektu
Můžete určit typy dat pro sadu řádků v době kompilace nebo za běhu.  
  
 Pokud potřebujete určit datové typy při kompilaci, použijte statické přístupového objektu (například `CAccessor`). Datové typy můžete určit ručně nebo pomocí průvodce příjemcem knihovny ATL technologie OLE DB.  
  
 Pokud je nutné určit typy dat za běhu, použijte dynamický (`CDynamicAccessor` nebo jejích podřízených objektech) nebo ruční přistupující objekt (`CManualAccessor`). V těchto případech můžete volat `GetColumnInfo` na sadě řádků k vrácení informací vazba sloupce, ze kterého můžete určit typy.  
  
 Následující tabulka uvádí typy přístupových objektů, které jsou součástí šablony příjemce. Každý přistupující objekt má své výhody a nevýhody. V závislosti na vaší situaci jeden typ přístupového objektu by měl vyhovovat vašim potřebám.  
  
|Třída přístupového objektu|Vazba|Parametr|Komentář|  
|--------------------|-------------|---------------|-------------|  
|`CAccessor`|Vytvořte záznam uživatele s `COLUMN_ENTRY` makra. Makra vazby datového člena v tomto záznamu na přistupující objekt. Při vytváření sady řádků, nesmí nevázaných sloupců.|Ano, pomocí **PARAM_MAP** makro položku. Jednou vázán, nelze parametry.|Nejrychlejší přistupující objekt z důvodu malou část kódu.|  
|`CDynamicAccessor`|Automatické.|Ne.|Užitečné, pokud neznáte typ dat v sadě řádků.|  
|`CDynamicParameterAccessor`|Automatické, ale může být [přepsat](../../data/oledb/overriding-a-dynamic-accessor.md).|Ano, pokud zprostředkovatel podporuje `ICommandWithParameters`. Parametry navázat automaticky.|Nižší než `CDynamicAccessor` ale užitečná pro volání obecných uložených procedur.|  
|**CDynamicStringAccessor [A, W]**|Automatické.|Ne.|Načte data z úložiště dat jako řetězce data.|  
|`CManualAccessor`|Ruční pomocí `AddBindEntry`.|Ručně pomocí `AddParameterEntry`.|Velmi rychlé; parametry a sloupce vázány pouze jednou. Můžete určit typ data se mají použít. (Viz [DBVIEWER](http://msdn.microsoft.com/en-us/07620f99-c347-4d09-9ebc-2459e8049832) ukázku příklad.) Vyžaduje více kódu než `CDynamicAccessor` nebo `CAccessor`. Je to spíše jako přímé volání OLE DB.|  
|`CXMLAccessor`|Automatické.|Ne.|Načte data z úložiště dat jako řetězce data a zformátuje ho jako značky jazyka XML data.|  
  
## <a name="see-also"></a>Viz také  
 [Použití přístupových objektů](../../data/oledb/using-accessors.md)