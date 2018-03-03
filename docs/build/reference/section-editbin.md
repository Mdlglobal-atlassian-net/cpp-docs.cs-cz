---
title: "-SECTION (NÁSTROJE EDITBIN) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /section
dev_langs:
- C++
helpviewer_keywords:
- -SECTION editbin option
- SECTION editbin option
- alignment characters in sections
- /SECTION editbin option
ms.assetid: 4680ab4e-c984-4251-8241-93440cad7615
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 91ffb9bd0645cab51e4140697c41e5b715380fe8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="section-editbin"></a>/SECTION (EDITBIN)
```  
/SECTION:name[=newname][,attributes][alignment]  
```  
  
## <a name="remarks"></a>Poznámky  
 Tato možnost změní atributy oddílu, přepsání atributy, které byly nastaveny při zkompilovat nebo propojené objekt souboru pro oddíl.  
  
 Po dvojtečkou ( **:** ), zadejte *název* oddílu. Chcete-li změnit název oddílu, postupujte podle *název* znak rovná se (=) a *newname* pro oddíl.  
  
 Nastavit nebo změnit v části `attributes`, zadejte do čárkami (**,**) následuje jeden nebo více atributů znaků. Chcete-li negate atribut, uveďte před jeho znak s vykřičníkem (!). Následující znaky zadejte atributy paměti:  
  
|Atribut|Nastavení|  
|---------------|-------------|  
|c|kód|  
|d|Discardable|  
|e|spustitelný soubor|  
|Mohu|inicializovaného dat|  
|K|v mezipaměti virtuální paměti|  
|m|Odebrat odkaz|  
|O|informace o propojení|  
|P|stránkové virtuální paměti|  
|R|read|  
|s|shared|  
|u|Neinicializovaný dat|  
|w|write|  
  
 Ovládací prvek *zarovnání*, zadejte znak **A** následuje jeden z následujících znaků nastavit velikost zarovnání v bajtech, následujícím způsobem:  
  
|Znak|Zarovnání velikost v bajtech|  
|---------------|-----------------------------|  
|1|1|  
|2|2|  
|4|4|  
|8|8|  
|P|16|  
|t|32|  
|s|64|  
|x|bez zarovnání|  
  
 Zadejte `attributes` a *zarovnání* znaků jako řetězec s bez mezer. Znaky se nerozlišují malá a velká písmena.  
  
## <a name="see-also"></a>Viz také  
 [EDITBIN – možnosti](../../build/reference/editbin-options.md)