---
title: 'Pole Specifikace formátu: funkce scanf a wscanf | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
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
dev_langs:
- C++
helpviewer_keywords:
- width, specifications in scanf function
- scanf format specifications
- scanf width specifications
- scanf type field characters
- type fields, scanf function
- format specification fields for scanf function
- type fields
ms.assetid: 7e95de1b-0b71-4de3-9f81-c9560c78e039
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c99b951e0cbbb5d2a295eb336a856bdb6c4cc0e1
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32391945"
---
# <a name="format-specification-fields-scanf-and-wscanf-functions"></a>Pole specifikace formátu: funkce scanf a wscanf
Zde uvedené informace platí pro celou `scanf` řadu funkcí, včetně zabezpečené verze a popisuje symboly použité říct `scanf` funguje jak analyzovat vstupního datového proudu, jako je například vstupního datového proudu `stdin` pro `scanf`, do hodnoty, které jsou vloženy do programu proměnné.  
  
 Specifikace formátu má následující formát:  
  
 `%`[`*`] [[šířka](../c-runtime-library/scanf-width-specification.md)] [{[h &#124; l &#124; udou &#124; I64 &#124; L](../c-runtime-library/scanf-width-specification.md)}][typu](../c-runtime-library/scanf-type-field-characters.md)  
  
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