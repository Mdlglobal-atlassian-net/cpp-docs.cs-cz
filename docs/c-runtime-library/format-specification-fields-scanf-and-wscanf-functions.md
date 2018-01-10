---
title: "Pole Specifikace formátu: funkce scanf a wscanf | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apilocation:
- msvcr80.dll
- msvcr110.dll
- msvcr90.dll
- msvcr100.dll
- msvcr110_clr0400.dll
- msvcr120.dll
apitype: DLLExport
f1_keywords:
- wscanf
- scanf
dev_langs: C++
helpviewer_keywords:
- width, specifications in scanf function
- scanf format specifications
- scanf width specifications
- scanf type field characters
- type fields, scanf function
- format specification fields for scanf function
- type fields
ms.assetid: 7e95de1b-0b71-4de3-9f81-c9560c78e039
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2286d7a6b82cf917c264cc43b82dec3939af6d94
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="format-specification-fields-scanf-and-wscanf-functions"></a>Pole specifikace formátu: funkce scanf a wscanf
Zde uvedené informace platí pro celou `scanf` řadu funkcí, včetně zabezpečené verze a popisuje symboly použité říct `scanf` funguje jak analyzovat vstupního datového proudu, jako je například vstupního datového proudu `stdin` pro `scanf`, do hodnoty, které jsou vloženy do programu proměnné.  
  
 Specifikace formátu má následující formát:  
  
 `%`[`*`] [[šířka](../c-runtime-library/scanf-width-specification.md)] [{[h &#124; p &#124; udou &#124; I64 &#124; L](../c-runtime-library/scanf-width-specification.md)}][typu](../c-runtime-library/scanf-type-field-characters.md)  
  
 `format` Argument určuje interpretace vstupu a může obsahovat jedno nebo více následujících akcí:  
  
-   Prázdné znaky: prázdný (""); Karta ('\t'); nebo nový řádek (\n). Prázdný znak způsobí, že `scanf` číst, ale nejsou uložené všech po sobě jdoucí prázdné znaky ve vstupu až do další znaku prázdný znak. Jeden prázdný znak ve formátu odpovídá jakékoli číslo (včetně 0) a kombinace prázdné znaky ve vstupu.  
  
-   Non prázdné znaky, s výjimkou znak procenta (`%`). Prázdné znaky znak způsobí, že `scanf` číst, ale nejsou uložené odpovídající znaku prázdný znak. Pokud další znak v vstupního datového proudu neodpovídá, `scanf` ukončí.  
  
-   Formátování specifikace, zaváděné znak procenta (`%`). Specifikace formátu způsobí, že `scanf` ke čtení a převést znaky ve vstupu hodnoty zadaného typu. Hodnota je přiřazena k argumentu v seznamu argumentů.  
  
 Formát je pro čtení zleva doprava. Znaky, které nejsou specifikace formátu se očekává tak, aby odpovídala pořadí znaků v vstupního datového proudu; odpovídající znaky v vstupního datového proudu jsou zkontrolovány, ale není uložené. Pokud je znak ve vstupní datový proud v konfliktu s specifikace formátu `scanf` ukončí, a znak je ponechán v vstupního datového proudu jako v případě, kdyby byla přečtena.  
  
 Když je zjištěna první specifikace formátu, hodnotu první vstupní pole převedena podle této specifikaci a uložené v umístění, která je zadána první `argument`. Druhý specifikace formátu způsobí, že druhý vstupní pole nutné převést a uložit do druhého `argument`, a tak dále až do konce řetězec formátu.  
  
 Vstupní pole není definováno jako všechny znaky první prázdný znak (mezera, tabulátor nebo nový řádek), nebo až první je dosaženo znak, který nelze převést podle specifikace formátu, nebo dokud šířka pole (Pokud je zadána). Pokud jsou příliš mnoho argumentů pro danou specifikace, jsou navíc argumenty vyhodnocen ale ignorovány. Výsledky mohou být nepředvídatelné, pokud nejsou k dispozici dostatečný počet argumentů pro specifikaci formátu.  
  
 Každé pole Specifikace formátu je jeden znak nebo číslo, což svědčí o tom možností konkrétní formátu. `type` Znaku, který se zobrazí po poslední pole volitelné formátu, určuje, zda vstupní pole interpretována jako znak, řetězec nebo číslo.  
  
 Nejjednodušší specifikace formátu obsahuje pouze znak procenta a `type` znaků (například `%s`). Pokud znakem procent (`%`) následuje znak, má žádný význam jako formát – řídicí znak, který znak a tyto znaky (až další znak procenta) jsou považovány za obyčejnou řady znaků, tedy posloupnost znaky, které se musí shodovat vstupu. Například použít k určení, že znak znak procenta má být vstup, `%%`.  
  
 Znak hvězdičky (`*`) následující znak procenta potlačí přiřazení další vstupní pole, které je interpretována jako pole zadaného typu. Pole je zkontrolovat, ale není uložené.  
  
 Bezpečné verze (ty s `_s` příponu) z `scanf` řady funkcí vyžadovat, že parametr velikost vyrovnávací paměti by být předána okamžitě následující každý parametr typu `c`, `C`, `s`, `S`nebo `[`. Další informace o zabezpečení verzích `scanf` řadu funkcí, najdete v části [scanf_s –, _scanf_s_l –, wscanf_s –, _wscanf_s_l –](../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md).  
  
## <a name="see-also"></a>Viz také  
 [Specifikace šířky scanf](../c-runtime-library/scanf-width-specification.md)   
 [Znaky pole typu scanf](../c-runtime-library/scanf-type-field-characters.md)   
 [scanf, _scanf_l –, wscanf, _wscanf_l –](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)   
 [scanf_s, _scanf_s_l, wscanf_s, _wscanf_s_l](../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)