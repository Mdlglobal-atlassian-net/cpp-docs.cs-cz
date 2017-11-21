---
title: "ODDÍLY (C/C++) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SECTIONS
dev_langs: C++
helpviewer_keywords: SECTIONS .def file statement
ms.assetid: 7b974366-9ef5-4e57-bbcc-73a1df6f8857
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 9d1564d068f4d69c3190b8bb24a32e7efb01dbef
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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
  
 `SECTIONS`Označuje začátek seznam části `definitions`. Každý `definition` musí být na samostatném řádku. `SECTIONS` – Klíčové slovo může být na stejném řádku jako první `definition` nebo na předchozí řádek. .Def soubor může obsahovat jednu nebo více `SECTIONS` příkazy. `SEGMENTS` – Klíčové slovo je podporovaný jako synonymum pro `SECTIONS`.  
  
 Podporuje starší verze aplikace Visual C++:  
  
```  
section [CLASS 'classname'] specifier  
```  
  
 `CLASS` – Klíčové slovo je podporována pro kompatibility, ale je ignorován.  
  
 Je ekvivalentní způsob určit atributy oddílu [/SECTION](../../build/reference/section-specify-section-attributes.md) možnost.  
  
## <a name="see-also"></a>Viz také  
 [Pravidla pro příkazy definice modulu](../../build/reference/rules-for-module-definition-statements.md)