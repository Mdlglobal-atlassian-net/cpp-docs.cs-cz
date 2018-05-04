---
title: ODDÍLY (C/C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- SECTIONS
dev_langs:
- C++
helpviewer_keywords:
- SECTIONS .def file statement
ms.assetid: 7b974366-9ef5-4e57-bbcc-73a1df6f8857
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4c433bf49ee4c56833ac7291bcc4a0f90e32f4e5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="sections-cc"></a>ODDÍLY (C/C++)
Představuje oddíl jednoho nebo více `definitions` , které jsou specifikátory přístupu v části v projektu na výstupní soubor.  
  
```  
SECTIONS  
definitions  
```  
  
## <a name="remarks"></a>Poznámky  
 Každý definice musí být na samostatném řádku. `SECTIONS` – Klíčové slovo může být na stejném řádku jako první definice nebo na předchozí řádek. .Def soubor může obsahovat jednu nebo více `SECTIONS` příkazy.  
  
 To `SECTIONS` příkaz nastaví atributy pro jeden nebo více oddílů v souboru bitové kopie a je možné přepsat výchozí atributy pro každý typ oddílu.  
  
 Formát pro `definitions` je:  
  
 `.section_name specifier`  
  
 kde `.section_name` je název oddílu v bitové kopii programu a `specifier` je jeden nebo více následujících modifikátory přístupu:  
  
|Modifikátor|Popis|  
|--------------|-----------------|  
|`EXECUTE`|V části je spustitelný soubor|  
|`READ`|Umožňuje operace čtení dat|  
|`SHARED`|Sdílené složky v části mezi všechny procesy, které načíst obrázek|  
|`WRITE`|Umožňuje operací zápisu na data|  
  
 Specifikátor názvy oddělte mezerou. Příklad:  
  
```  
SECTIONS  
.rdata READ WRITE  
```  
  
 `SECTIONS` Označuje začátek seznam části `definitions`. Každý `definition` musí být na samostatném řádku. `SECTIONS` – Klíčové slovo může být na stejném řádku jako první `definition` nebo na předchozí řádek. .Def soubor může obsahovat jednu nebo více `SECTIONS` příkazy. `SEGMENTS` – Klíčové slovo je podporovaný jako synonymum pro `SECTIONS`.  
  
 Podporuje starší verze aplikace Visual C++:  
  
```  
section [CLASS 'classname'] specifier  
```  
  
 `CLASS` – Klíčové slovo je podporována pro kompatibility, ale je ignorován.  
  
 Je ekvivalentní způsob určit atributy oddílu [/SECTION](../../build/reference/section-specify-section-attributes.md) možnost.  
  
## <a name="see-also"></a>Viz také  
 [Pravidla pro příkazy definice modulu](../../build/reference/rules-for-module-definition-statements.md)