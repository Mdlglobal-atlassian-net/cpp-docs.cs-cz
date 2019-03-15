---
title: Direktivy s tečkou
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, dot directives
- dot directives in NMAKE
ms.assetid: ab35da65-30b6-48b7-87d6-61503d7faf9f
ms.openlocfilehash: 2c21e8a18c76331f86a4e8966b4f67c9c9bc9b7d
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57823164"
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

## <a name="see-also"></a>Viz také:

[NMAKE – referenční zdroje](nmake-reference.md)
