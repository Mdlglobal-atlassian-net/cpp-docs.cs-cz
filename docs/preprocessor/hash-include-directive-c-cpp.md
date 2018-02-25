---
title: "#include – direktiva (C/C++) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- '#include'
dev_langs:
- C++
helpviewer_keywords:
- preprocessor, directives
- '#include directive'
- include directive (#include)
ms.assetid: 17067dc0-8db1-4f2d-b43e-ec12ecf83238
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cee268b68d9be823c6919780f8f4f25e78e1eb74
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="include-directive-cc"></a>#include – direktiva (C++)
Informuje preprocesor zacházet s obsah zadaného souboru, jako kdyby se objeví v zdrojový program v místě, kde se zobrazí direktivu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      #include  "path-spec"  
#include  <path-spec>  
```  
  
## <a name="remarks"></a>Poznámky  
 Můžete uspořádat definice konstanta a makro do zahrnout soubory a pak použít `#include` direktivy je přidáte do jakékoli zdrojový soubor. Zahrnout soubory jsou užitečné pro zahrnutí deklarace externích proměnných a komplexními datovými typy. Typy může být definovaný a s názvem pouze jednou v souboru začlenění pro tento účel vytvořit.  
  
 `path-spec` Je název souboru, který může volitelně předcházet specifikaci adresáře. Název existující soubor musí být název souboru. Syntaxe `path-spec` závisí na operačním systému, na kterém je program zkompilovat.  
  
 Informace o tom, jak odkazovat na sestavení v aplikaci C++, který se zkompiluje pomocí [/CLR](../build/reference/clr-common-language-runtime-compilation.md), najdete v části [#using](../preprocessor/hash-using-directive-cpp.md).  
  
 Obě různé formy způsobit směrnice nahradit za celý obsah zadaný soubor. Rozdíl mezi dvěma formuláře je v pořadí, ve kterém preprocesor vyhledá soubory hlaviček-li úplně zadána cesta. Následující tabulka ukazuje rozdíl mezi dvě různé formy.  
  
|Syntaxe formuláře|Akce|  
|-----------------|------------|  
|Uvozovkách formuláře|Preprocesor hledá zahrnout soubory v tomto pořadí:<br /><br /> 1) ve stejném adresáři jako soubor, který obsahuje `#include` příkaz.<br /><br /> 2) v adresáře aktuálně otevřenou obsahovat soubory, v opačném pořadí, ve kterém byly otevřen. Hledání začíná v adresáři nadřazené zahrnout soubor a pokračuje směrem nahoru adresáře žádné nadřazený zahrnout soubory.<br /><br /> 3) v cestě, který je určen podle jednotlivých /I – možnost kompilátoru.<br /><br /> 4)<br /><br /> Podél cesty, které jsou určené proměnnou prostředí zahrnout.|  
|Formulář ostré závorky|Preprocesor hledá zahrnout soubory v tomto pořadí:<br /><br /> 1) v cestě, který je určen podle jednotlivých /I – možnost kompilátoru.<br /><br /> 2) kompilování Pokud probíhá na příkazový řádek podél cesty, které jsou určené proměnnou prostředí zahrnout.|  
  
 Preprocesor – zastaví hledání také soubor s daným názvem najde. Pokud uzavřete specifikaci dokončení, jednoznačným cestu pro soubor zahrnutí mezi dvojitých uvozovek nahoře (""), preprocesor vyhledá pouze specifikace této cesty a ignoruje standardní adresáře.  
  
 Pokud název souboru, který má uzavřena v uvozovkách představuje specifikaci neúplné cesta, vyhledá preprocesoru první k adresáři se souborem "nadřazená". Nadřazený soubor je soubor, který obsahuje `#include` – direktiva. Například pokud obsahovat soubor s názvem `file2` do souboru s názvem `file1`, `file1` je nadřazeném souboru.  
  
 Vložené soubory mohou být "vnořené"; To znamená `#include` – direktiva se mohou objevit v souboru, který je pojmenován jiným `#include` – direktiva. Například `file2` můžou zahrnovat `file3`. V takovém případě `file1` bude stále nadřazeného `file2`, ale bylo by "nadřazený" z `file3`.  
  
 Když zahrnout soubory jsou vnořené a při kompilování dojde na příkazovém řádku, vyhledávání directory začíná adresáře nadřazeném souboru a poté pokračuje prostřednictvím adresáře všechny soubory nadřazený. To znamená hledání začne vůči adresáři, která obsahuje daný zdroj, který se právě zpracovává. Pokud soubor nebyl nalezen, hledání se přesune do adresáře, které jsou určené /I – možnost kompilátoru. Prohledají se nakonec adresáře, které jsou určené proměnnou prostředí zahrnout.  
  
 Z vývojového prostředí je ignorován proměnné prostředí zahrnout. Informace o tom, jak nastavit adresáře, které se vyhledávají zahrnout soubory – to platí také pro proměnná prostředí LIB – viz [stránka vlastností adresářů VC ++](../ide/vcpp-directories-property-page.md).  
  
 Tento příklad ukazuje zahrnutí souborů pomocí ostrých závorek:  
  
```  
#include <stdio.h>  
```  
  
 Tento příklad přidá obsah souboru s názvem STDIO. H na zdrojový program. Lomené závorky způsobit preprocesor k vyhledání adresáře, které jsou určené proměnnou prostředí zahrnout pro STDIO. H, po prohledává adresáře, které jsou určené /I – možnost kompilátoru.  
  
 Další příklad ukazuje zahrnutí souborů pomocí uvozovkách formuláře:  
  
```  
#include "defs.h"  
```  
  
 Tento příklad přidá obsah souboru, která je zadána DEFS. H na zdrojový program. Uvozovky znamená, že preprocesor nejprve hledat adresář, který obsahuje zdrojový soubor nadřazené.  
  
 Vnoření zahrnout soubory můžete pokračovat až 10 úrovně. Když vnořeného `#include` je zpracování preprocesor pokračuje vložení nadřazených soubor do původní zdrojový soubor.  
  
 **Microsoft Specific**  
  
 Najít includable zdrojové soubory, preprocesoru první hledání adresáře, které jsou určené /I – možnost kompilátoru. Pokud není k dispozici možnost /I nebo selže, preprocesor používá proměnnou prostředí pro zahrnutí nalézt žádné soubory zahrnout v rámci lomené závorky. Zahrnout prostředí proměnnou a /I – možnost kompilátoru může obsahovat více cest, oddělených středníkem (;). Pokud se více než jeden adresář se zobrazí jako součást možnost /I nebo v rámci proměnné prostředí zahrnout, preprocesor je prohledává v pořadí, ve kterém jsou zobrazeny.  
  
 Například příkaz  
  
```  
CL /ID:\MSVC\INCLUDE MYPROG.C  
```  
  
 způsobí, že preprocesor pro vyhledávání v adresáři D:\MSVC\INCLUDE\ pro zahrnout soubory, jako je například STDIO. H. Příkazy  
  
```  
SET INCLUDE=D:\MSVC\INCLUDE  
CL MYPROG.C  
```  
  
 mají stejný účinek. Pokud selžou obě sady hledání, vygeneruje se kompilátoru závažné chybě.  
  
 Pokud název souboru je plně zadaná pro vloženého souboru, který má cestu, který obsahuje dvojtečku (například F:\MSVC\SPECIAL\INCL\TEST. H), preprocesor sleduje cestu.  
  
 Pro zahrnout soubory, které jsou určeny jako `#include` "`path-spec`", vyhledávání directory začíná adresáři nadřazeném souboru a poté pokračuje prostřednictvím adresáře všechny soubory nadřazený. To znamená, hledání začne vůči adresáři, který obsahuje zdrojový soubor, který obsahuje `#include` direktiva, která je zpracovávána. Pokud není dostupný žádný nadřazený soubor a soubor nebyl nalezen, vyhledávání bude pokračovat, jako kdyby měla název souboru uzavřené v lomených závorkách.  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Preprocesor – direktivy](../preprocessor/preprocessor-directives.md)