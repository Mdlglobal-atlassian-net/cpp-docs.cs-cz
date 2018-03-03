---
title: "přepínač Statement (C) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- switch
dev_langs:
- C++
helpviewer_keywords:
- switch keyword [C]
ms.assetid: fbede014-23bd-4ab1-8094-c8d9d9cb963a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 84594f668d0fc807ebb815cc519c7d45f62e8b12
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="switch-statement-c"></a>switch – příkaz (C)
`switch` a **případ** příkazy Nápověda ovládacího prvku složité podmíněného větvení operace a. `switch` Příkaz předá řízení příkaz v jeho textu.  
  
## <a name="syntax"></a>Syntaxe  
 *Výběr příkaz*:  
 **přepínače (** *výraz* **)** *– příkaz*  
  
 *příkaz s popiskem*:  
 **případ***konstantní výraz***:***– příkaz*   
  
 **Výchozí:***– příkaz*   
  
 Ovládací prvek předává do příkazu, jehož **případ** *konstantní výraz* odpovídá hodnotě **přepínače (** *výraz* **)**. `switch` Výraz může obsahovat libovolný počet **případ** instance, ale žádné dvě konstanty případu v téže `switch` příkaz může mít stejnou hodnotu. Provádění těla příkazu začíná na vybraný příkaz a pokračuje až do konce text, nebo dokud **zalomení** příkaz přenosy ovládacího prvku z textu.  
  
 Použití `switch` příkaz obvykle vypadá nějak takto:  
  
 `switch`( *výraz* )  
  
 **{**  
  
 *deklarace*  
  
 .  
  
 .  
  
 .  
  
 **případ** *konstantní výraz* **:**  
  
 *příkazy provést, pokud se rovná výraz*  
  
 *Hodnota výrazu – konstanta*  
  
 .  
  
 .  
  
 .  
  
 **Rozdělit;**  
  
 **Výchozí hodnota:**  
  
 *příkazy provést, pokud výraz se nerovná*  
  
 *jakýkoli případu konstanta – výraz*  
  
 **}**  
  
 Můžete použít **zalomení** příkaz k ukončení zpracování konkrétní případu v rámci `switch` příkaz a větve na konec `switch` příkaz. Bez **zalomení**, program nadále další případě provádění příkazy, dokud **zalomení** nebo je dosaženo konce příkaz. V některých situacích může být žádoucí tento pokračování.  
  
 **Výchozí** je spustit příkaz, pokud žádné **případ** *konstantní výraz* se rovná hodnotě **přepínače (**  *výraz* **)**. Pokud **výchozí** příkaz je vynechán a ne **případ** je nalezena shoda, žádné příkazy v `switch` provedení textu. Může být maximálně jedna **výchozí** příkaz. **Výchozí** příkaz nemusí pocházet na konci; může vyskytovat kdekoli v textu `switch` příkaz. A **případ** nebo **výchozí** popisek může být použit pouze uvnitř `switch` příkaz.  
  
 Typ `switch` *výraz* a **případ** *konstantní výraz* musí být celočíselné. Hodnota jednotlivých **případ** *konstantní výraz* musí být jedinečný v rámci těla příkazu.  
  
 **Případ** a **výchozí** popisky `switch` těla příkazu jsou důležitá pouze v počátečním testu, který určuje, kde začít provádění do těla příkazu. Mohou být vnořené příkazy přepínače. Všechny statické proměnné se inicializují před spuštěním do jakéhokoli `switch` příkazy.  
  
> [!NOTE]
>  Deklarace můžete se zobrazí v první pozice tvořící složený příkaz `switch` textu, ale inicializacích součástí deklarací se neprovádí. `switch` Příkaz přenáší přímo do spustitelného souboru příkazu v textu, obejitím řádky, které obsahují inicializacích ovládací prvek.  
  
 Následující příklady ilustrují `switch` příkazy:  
  
```  
switch( c )   
{  
    case 'A':  
        capa++;  
    case 'a':  
        lettera++;  
    default :  
        total++;  
}  
```  
  
 Všechny tři prohlášení o `switch` textu v tomto příkladu jsou provést, pokud `c` rovná `'A'` od **zalomení** příkaz nezobrazí před následující případ. Řízení provádění se přenese na prvním příkazem (`capa++;`) a pokračuje v pořadí procházení zbývající části textu. Pokud `c` rovná `'a'`, `lettera` a `total` se zvýší. Pouze `total` se zvýší, pokud `c` se nerovná `'A'` nebo `'a'`.  
  
```  
switch( i )   
{  
    case -1:  
        n++;  
        break;  
    case 0 :  
        z++;  
        break;  
    case 1 :  
        p++;  
        break;  
}  
```  
  
 V tomto příkladu **zalomení** příkaz následuje každý příkaz `switch` textu. **Zalomení** příkaz vynutí ukončení z textu příkaz po provedení jeden příkaz. Pokud `i` je rovno -1, pouze `n` se zvýší. **Zalomení** následující příkaz `n++;` způsobí, že řízení provádění předat mimo těla příkazu, obcházení zbývající příkazy. Podobně pokud `i` rovná 0, pouze `z` se zvýší; Pokud `i` se rovná 1, pouze `p` se zvýší. Konečné **zalomení** příkaz není nezbytně nutné, protože ovládací prvek předává z textu na konci složené příkaz, ale je zahrnuté pro konzistence.  
  
 Jediný příkaz přenášet více **případ** štítků, jak ukazuje následující příklad:  
  
```  
case 'a' :  
case 'b' :  
case 'c' :  
case 'd' :  
case 'e' :  
case 'f' :  hexcvt(c);  
```  
  
 V tomto příkladu Pokud *konstantní výraz* rovná jakékoli písmeno mezi `'a'` a `'f'`, `hexcvt` funkce je volána.  
  
 **Konkrétní Microsoft**  
  
 Microsoft C neomezuje počet případů hodnot v `switch` příkaz. Číslo je omezena pouze dostupné paměti. ANSI C vyžaduje alespoň 257 případu popisky povolené v `switch` příkaz.  
  
 Výchozí nastavení pro Microsoft C je, že jsou povolené rozšíření Microsoft. Použijte /Za – možnost kompilátoru zakázání tyto rozšíření.  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [switch – příkaz (C++)](../cpp/switch-statement-cpp.md)