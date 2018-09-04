---
title: Určení typu přístupového objektu použití | Dokumentace Microsoftu
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
ms.openlocfilehash: e8dbfecf52e974330360714763da3bd4c81117ad
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43679721"
---
# <a name="determining-which-type-of-accessor-to-use"></a>Určení použitého typu přístupového objektu
V době kompilace nebo za běhu, můžete určit typy dat pro sadu řádků.  
  
 Pokud je potřeba určit datové typy v době kompilace, použijte statického následovníka (například `CAccessor`). Datové typy, které můžete určit ručně nebo pomocí průvodce příjemcem ATL OLE DB.  
  
 Pokud je potřeba určit datové typy v době běhu, použít dynamickou (`CDynamicAccessor` nebo její podřízené jednotce) nebo ruční přístupového objektu (`CManualAccessor`). V těchto případech můžete volat `GetColumnInfo` pro řádků vrátit informace o vazbě sloupec, ze kterého můžete určit typy.  
  
 Následující tabulka uvádí typy přístupových objektů, které jsou součástí šablony příjemce. Každý přistupující objekt má své výhody a nevýhody. V závislosti na vaší situaci jeden typ přístupového objektu by měl vyhovovat vašim potřebám.  
  
|Přístupový objekt třídy|Vazba|Parametr|Komentář|  
|--------------------|-------------|---------------|-------------|  
|`CAccessor`|S makry COLUMN_ENTRY vytvořte záznam uživatele. Makra svázat datový člen v daném záznamu přistupujícího objektu. Když se v sadě řádků, sloupců nelze odvázat.|Ano, s použitím makra PARAM_MAP. Jednou vázán, nelze odvázat parametry.|Nejrychlejší přistupující objekt z důvodu malé množství kódu.|  
|`CDynamicAccessor`|Automatické.|Ne.|Je užitečné, pokud si nejste jisti typ dat v sadě řádků.|  
|`CDynamicParameterAccessor`|Automaticky, ale může být [přepsat](../../data/oledb/overriding-a-dynamic-accessor.md).|Ano, pokud poskytovatel podporuje `ICommandWithParameters`. Parametry automaticky svázán.|Pomalejší než `CDynamicAccessor` ale užitečná pro volání obecné uložené procedury.|  
|`CDynamicStringAccessor[A,W]`|Automatické.|Ne.|Načte data z úložiště dat jako řetězec data.|  
|`CManualAccessor`|Ruční použití `AddBindEntry`.|Ručně pomocí `AddParameterEntry`.|Velmi rychlé zpracování; parametry a sloupce vázané jenom jednou. Můžete určit typ data se mají použít. (Viz [DBVIEWER](https://github.com/Microsoft/VCSamples) Vzorový příklad.) Vyžaduje další kód než `CDynamicAccessor` nebo `CAccessor`. Je to spíše jako přímé volání OLE DB.|  
|`CXMLAccessor`|Automatické.|Ne.|Načte data z úložiště dat jako řetězce data a ji naformátuje jako XML příznakem data.|  
  
## <a name="see-also"></a>Viz také  
 [Použití přístupových objektů](../../data/oledb/using-accessors.md)