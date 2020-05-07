---
title: pgomgr
ms.date: 03/14/2018
helpviewer_keywords:
- pgomgr program
- profile-guided optimizations, pgomgr
ms.assetid: 74589126-df18-42c9-8739-26d60e148d6a
ms.openlocfilehash: 4e3eb08c88db9d0ed4e47649014a600c3e0ccb78
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62295236"
---
# <a name="pgomgr"></a>pgomgr

Přidá data profilu z jednoho nebo více souborů. pgc do souboru. pgd.

## <a name="syntax"></a>Syntaxe

> **pgomgr** [*Možnosti*] *pgcfiles* *pgdfile*

### <a name="parameters"></a>Parametry

*nastavení*<br/>
K **pgomgr**lze zadat následující možnosti:

- **/help** nebo **/?** Zobrazí dostupné možnosti **pgomgr** .

- **/clear** Způsobí vymazání souboru. pgd všechny informace o profilu. Když je zadaný **/clear** , nemůžete zadat soubor. pgc.

- **/Detail** Zobrazí podrobné statistiky, včetně informací o pokrytí grafu Flow.

- **/summary** Zobrazí statistiku pro jednotlivé funkce.

- **/Unique** Při použití s **/summary**způsobí, že se dekorují názvy funkcí, které se mají zobrazit. Výchozí hodnota, pokud se **/Unique** nepoužívá, je pro zobrazení nedekorovaných názvů funkcí.

- **/Merge**\[**:**<em>n</em>] způsobí, že jsou data v souboru. pgc nebo soubory přidány do souboru. pgd. Volitelný parametr *n*umožňuje určit, že data by se měla přidat *n* krát. Například pokud by byl scénář obvykle proveden šestkrát, aby odrážel, jak často ho zákazníci provádějí, můžete to provést v rámci testovacího běhu a po šesti časech ho přidat do souboru. pgd pomocí **pgomgr/Merge: 6**.

*pgcfiles*<br/>
Jeden nebo více souborů. pgc, jejichž data profilu chcete sloučit do souboru. pgd. Můžete zadat jeden soubor. pgc nebo více souborů. pgc. Pokud nezadáte žádné soubory. pgc, **pgomgr** sloučí všechny soubory. pgc, jejichž názvy souborů jsou stejné jako soubor. pgd.

*pgdfile*<br/>
Soubor. PGD, do kterého slučujete data ze souboru. pgc nebo souborů.

## <a name="remarks"></a>Poznámky

> [!NOTE]
> Tento nástroj můžete spustit pouze z příkazového řádku pro vývojáře v aplikaci Visual Studio. Nemůžete ho spustit z příkazového řádku systému nebo z Průzkumníka souborů.

## <a name="example"></a>Příklad

Tento ukázkový příkaz vymaže soubor MyApp. pgd s daty profilu:

`pgomgr /clear myapp.pgd`

Tento ukázkový příkaz přičítá data profilu v souboru Myapp1. pgc do souboru. pgd třikrát:

`pgomgr /merge:3 myapp1.pgc myapp.pgd`

V tomto příkladu jsou data profilu ze všech souborů MyApp #. pgc přidána do souboru MyApp. pgd.

`pgomgr -merge myapp1.pgd`

## <a name="see-also"></a>Viz také

[Optimalizace na základě profilu](profile-guided-optimizations.md)<br/>
[PgoAutoSweep](pgoautosweep.md)<br/>
[pgosweep](pgosweep.md)<br/>
