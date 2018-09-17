---
title: Dot direktivy | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, dot directives
- dot directives in NMAKE
ms.assetid: ab35da65-30b6-48b7-87d6-61503d7faf9f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f2f4b984bcfe1aa89fd8e0229c7381c0d01f8685
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45714608"
---
# <a name="dot-directives"></a>Direktivy s tečkou

Zadejte direktivy s tečkou mimo blok popis na začátku řádku. Direktivy s tečkou začínat tečkou (. ) a jsou následovaný dvojtečkou (:). Jsou povoleny mezerami a tabulátory. Tečka direktiv názvy jsou malá a velká písmena a velká písmena.

|– Direktiva|Účel|
|---------------|-------------|
|**. IGNORUJTE:**|Ignoruje nenulový ukončovací kód vrácený příkazy z místa, který je zadaný na konec souboru pravidel. Ve výchozím nastavení NMAKE zastaví, pokud příkaz vrátí nenulový ukončovací kód. K obnovení, kontroly chyb, použijte **! CMDSWITCHES**. Chcete-li ignorovat ukončovací kód pro jediný příkaz, použijte modifikátor pomlčky (-). Chcete-li ignorovat ukončovací kód pro celý soubor, použijte / I.|
|**. DRAHÝMI:** *cíle*|Zachová *cíle* na disku při zastavení se příkazy k jejich aktualizaci; nemá vliv, pokud příkaz zpracovává přerušení odstraněním souboru. Cílové názvy oddělte mezery nebo tabulátory. Ve výchozím nastavení odstraní NMAKE cíl, pokud dojde k přerušení sestavení pomocí kombinace kláves CTRL + C nebo CTRL + BREAK. Každé použití klíčového **. CENNÝ** se vztahuje na celý soubor pravidel; více specifikace jsou kumulativní.|
|**. TICHÉ:**|Potlačí zobrazení provedených příkazů z místa, který je zadaný na konec souboru pravidel. Ve výchozím nastavení zobrazí NMAKE příkazy, které vyvolá. Chcete-li obnovit, zobrazování, použijte **! CMDSWITCHES**. Chcete-li potlačit zobrazení jediným příkazem, použijte **@** modifikátor. Potlačí zobrazování pro celý soubor, použijte/S.|
|**. PŘÍPONY:** `list`|Zobrazí seznam rozšíření pro porovnávání odvozené pravidlo; předdefinované zahrnují následující přípony: .exe .obj .asm .c .cpp .cxx BAS .cbl tlačítka .pas .res .rc .f .f90|

Chcete-li změnit **. PŘÍPONY** seznamu pořadí nebo pokud chcete zadat nový seznam, vymazání seznamu a zadejte nové nastavení. Vymazat seznam, zadejte žádná rozšíření po dvojtečka:

```
.SUFFIXES :
```

Chcete-li přidat další přípony na konec seznamu, zadejte

```
.SUFFIXES : suffixlist
```

kde *suffixlist* seznam obsahuje další přípony, oddělené mezerami nebo karty. Pokud chcete zobrazit aktuální nastavení **. PŘÍPONY**, spusťte s parametrem/p. NMAKE

## <a name="see-also"></a>Viz také

[NMAKE – referenční zdroje](../build/nmake-reference.md)