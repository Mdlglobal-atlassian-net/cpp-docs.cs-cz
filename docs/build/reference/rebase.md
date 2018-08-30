---
title: -REBASE | Dokumentace Microsoftu
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
ms.openlocfilehash: 686306316e6950ba62ea7c44522b95f4d935be0b
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43216171"
---
# <a name="rebase"></a>/REBASE
```  
/REBASE[:modifiers]  
```  
  
## <a name="remarks"></a>Poznámky  
 Tato možnost nastaví bázové adresy pro zadané soubory. Editbin – přiřadí nové základní adresy v souvislých adresního prostoru podle velikosti jednotlivých souborů zaokrouhlena nejbližší 64 KB. Podrobnosti o základní adresy najdete v tématu [základní adresa](../../build/reference/base-base-address.md) (/ BASE) – možnost linkeru.  
  
 Zadejte spustitelné soubory a knihovny DLL v programu *soubory* argument v příkazovém řádku nástroje EDITBIN v pořadí, ve kterém mají být založen. Volitelně můžete zadat jeden nebo více *modifikátory*, každé oddělené čárkou (**,**):  
  
|Modifikátor|Akce|  
|--------------|------------|  
|**ZÁKLAD =**<em>adresu</em>|Obsahuje počáteční adresu pro opětovné přiřazení základní adresy k souborům. Zadejte *adresu* v desítkovém zápisu nebo v zápisu jazyka. Pokud základ není zadán, je výchozí počáteční základní adresa 0x400000. Pokud dolů je použit, základní musí být zadán, a *adresu* Nastaví konec rozsahu základní adresy.|  
|**BASEFILE**|Vytvoří soubor s názvem COFFBASE. TXT, který je textový soubor ve formátu očekávaném podle odkazu nebo základní možnosti.|  
|**DOLŮ**|Říká EDITBIN přiřazení základní adresy směrem dolů od koncových adres. Soubory jsou přiřazeny v uvedeném pořadí s první soubor umístěný v nejvyšší možné adresy dál konci rozsahu adres. ZÁKLADNÍ musí použít s dolů zajistit dostatečný Adresní prostor pro odvození soubory. K určení adresního prostoru vyžadované zadané soubory, spusťte nástroje EDITBIN s /REBASE na souborech a přidejte do zobrazeného celkové velikosti 64 KB.|  
  
## <a name="see-also"></a>Viz také  
 [EDITBIN – možnosti](../../build/reference/editbin-options.md)