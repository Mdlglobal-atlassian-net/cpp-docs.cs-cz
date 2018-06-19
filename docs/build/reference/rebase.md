---
title: -REBASE | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /rebase
dev_langs:
- C++
helpviewer_keywords:
- base addresses [C++]
- -REBASE editbin option
- REBASE editbin option
- DLLs [C++], linking
- executable files [C++], base address
- /REBASE editbin option [C++]
ms.assetid: 3f89d874-af5c-485b-974b-fd205f6e1a4b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4a5e2b68768b01d71532c358a14c53d8a033e1ed
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32377086"
---
# <a name="rebase"></a>/REBASE
```  
/REBASE[:modifiers]  
```  
  
## <a name="remarks"></a>Poznámky  
 Tento parametr nastaví základní adresy pro zadané soubory. Editbin – přiřadí nové základní adresy souvislý adresního prostoru podle velikosti jednotlivých souborů zaokrouhleno směrem nahoru na nejbližší 64 KB. Podrobnosti o základní adresy najdete v tématu [základní adresa](../../build/reference/base-base-address.md) (/ základní) – možnost linkeru.  
  
 Zadejte spustitelné soubory a knihovny DLL v programu *soubory* argumentů na příkazový řádek EDITBIN v pořadí, ve kterém jsou založena. Volitelně můžete zadat jednu nebo více *modifikátory*, každé oddělené čárkou (**,**):  
  
|Modifikátor|Akce|  
|--------------|------------|  
|ZÁKLADNÍ **= *** adresa*|Poskytuje počáteční adresa pro přeřazení základní adresy k souborům. Zadejte *adresu* v desítkový nebo jazyka C zápis. Pokud není zadán základní, je výchozí počáteční základní adresa 0x400000. Pokud je nižší použité, základní musí být zadán, a *adresu* Nastaví konec rozsahu základní adresy.|  
|BASEFILE|Vytvoří soubor s názvem COFFBASE. Soubory TXT, což je textový soubor ve formátu očekávaném pomocí odkazu a základní možnost.|  
|DOLŮ|Informuje nástroje EDITBIN přiřazení základní adresy dolů z koncová adresa. Soubory jsou přiřazeny v uvedeném pořadí s první soubor nachází v nejvyšší možné adrese níže konec rozsahu adres. ZÁKLADNÍ musí použít s nižší zajistit dostatečný Adresní prostor pro odvození soubory. K určení adresní prostor vyžaduje zadané soubory, spusťte nástroje EDITBIN s /REBASE na soubory a přidejte 64 KB na zobrazené celkovou velikost.|  
  
## <a name="see-also"></a>Viz také  
 [EDITBIN – možnosti](../../build/reference/editbin-options.md)