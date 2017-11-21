---
title: -REBASE | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /rebase
dev_langs: C++
helpviewer_keywords:
- base addresses [C++]
- -REBASE editbin option
- REBASE editbin option
- DLLs [C++], linking
- executable files [C++], base address
- /REBASE editbin option [C++]
ms.assetid: 3f89d874-af5c-485b-974b-fd205f6e1a4b
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 05b718b20ad941764158f2de461614885b0627fa
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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
|ZÁKLADNÍ**=***adresa*|Poskytuje počáteční adresa pro přeřazení základní adresy k souborům. Zadejte *adresu* v desítkový nebo jazyka C zápis. Pokud není zadán základní, je výchozí počáteční základní adresa 0x400000. Pokud je nižší použité, základní musí být zadán, a *adresu* Nastaví konec rozsahu základní adresy.|  
|BASEFILE|Vytvoří soubor s názvem COFFBASE. Soubory TXT, což je textový soubor ve formátu očekávaném pomocí odkazu a základní možnost.|  
|DOLŮ|Informuje nástroje EDITBIN přiřazení základní adresy dolů z koncová adresa. Soubory jsou přiřazeny v uvedeném pořadí s první soubor nachází v nejvyšší možné adrese níže konec rozsahu adres. ZÁKLADNÍ musí použít s nižší zajistit dostatečný Adresní prostor pro odvození soubory. K určení adresní prostor vyžaduje zadané soubory, spusťte nástroje EDITBIN s /REBASE na soubory a přidejte 64 KB na zobrazené celkovou velikost.|  
  
## <a name="see-also"></a>Viz také  
 [– Možnosti nástroje EDITBIN](../../build/reference/editbin-options.md)