---
title: Určení typu přístupového objektu | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- rowsets [C++], data types
- accessors [C++], types
ms.assetid: 22483dd2-f4e0-4dcb-8e4d-cd43a9c1a3db
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 89a55127b8f7e5e0e7d338a9e7ba4f85e8c568d2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33104006"
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