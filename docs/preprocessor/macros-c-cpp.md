---
title: Makra (C/C++) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- preprocessor
- preprocessor, macros
- Visual C++, preprocessor macros
ms.assetid: a7bfc5d4-2537-4fe0-bef0-70cec0b43388
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: e68ca7ef9033e14b5463c4d2db11620a71e0d94e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="macros-cc"></a>Makra (C/C++)
Předběžné zpracování rozšíří makra v všechny řádky, které nejsou preprocesor – direktivy (řádky, které nemají  **#**  jako první znak prázdných znaků) a v části některé direktivy, které nejsou v rámci přeskočeny Podmíněná kompilace. Direktivy „podmíněné kompilace“ umožňují potlačit kompilace částí zdrojového souboru testováním konstantního výrazu nebo identifikátoru k určení, které textové bloky jsou předány kompilátoru a které textové bloky jsou odstraněny ze zdrojového souboru během předběžného zpracování.  
  
 Direktiva `#define` je obvykle použita pro přiřazení smysluplných identifikátorů konstantám, klíčovým slovům a běžně používaným příkazům a výrazům. Identifikátory, které představují konstanty, jsou někdy označovány jako „symbolické konstanty“ nebo „konstanty manifestu“. Identifikátory, které představují příkazy nebo výrazy, jsou označovány jako „makra“. V této dokumentaci preprocesoru se používá pouze termín „makro“.  
  
 Po rozpoznání názvu makra ve zdrojovém textu programu nebo v argumentech určitých dalších příkazů preprocesoru je toto makro považováno za volání makra. Název makra je nahrazen kopií těla makra. Pokud makro přijímá argumenty, jsou v těle makra argumenty za názvem makra nahrazeny skutečnými parametry. Proces nahrazení volání makra zpracovanou kopií těla se nazývá „rozšíření“ volání makra.  
  
 V praxi existují dva typy maker. Makra „objektového typu“ nepřijímají žádné argumenty, kdežto makra „funkčního typu“ lze definovat pro přijímání argumentů tak, že se budou chovat a vypadat jako volání funkce. Vzhledem k tomu, že makra negenerují volání skutečné funkce, je někdy možné zvýšit rychlost programů nahrazením volání funkcí makry. (V jazyce C++ jsou často upřednostňovanou metodou vložené funkce.) Makra však mohou působit problémy, pokud nejsou definována a používána opatrně. U definice maker bude možná zapotřebí používat závorky spolu s argumenty, aby bylo možné zachovat správnou prioritu ve výrazu. Makra také nemusí správně zpracovávat výrazy s vedlejšími účinky. Najdete v článku `getrandom` příkladu [#define – direktiva](../preprocessor/hash-define-directive-c-cpp.md) Další informace.  
  
 Po definování makra jej nelze předefinovat na jinou hodnotu, aniž by byla nejdříve odstraněna původní definice. Je však možné předefinovat makro stejnou definicí. Stejná definice se tedy v programu může objevit více než jednou.  
  
 #**Undef** – direktiva odebere definici makra. Po odebrání definice lze makro upravit na jinou hodnotu. [#Define – direktiva](../preprocessor/hash-define-directive-c-cpp.md) a [#undef – direktiva](../preprocessor/hash-undef-directive-c-cpp.md) popisují `#define` a `#undef` direktivy, v uvedeném pořadí.  
  
 Další informace najdete v tématu,  
  
-   [Makra a jazyk C++](../preprocessor/macros-and-cpp.md)  
  
-   [Variadická makra](../preprocessor/variadic-macros.md)  
  
-   [Předdefinovaná makra](../preprocessor/predefined-macros.md)  
  
## <a name="see-also"></a>Viz také  
 [C/C++ – referenční dokumentace preprocesoru](../preprocessor/c-cpp-preprocessor-reference.md)