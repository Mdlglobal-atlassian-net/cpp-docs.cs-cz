---
title: pgomgr – | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2018
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- pgomgr program
- profile-guided optimizations, pgomgr
ms.assetid: 74589126-df18-42c9-8739-26d60e148d6a
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 743665bbe0ee9c3df08d197d203e95d08542f613
ms.sourcegitcommit: 0523c88b24d963c33af0529e6ba85ad2c6ee5afb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/10/2018
---
# <a name="pgomgr"></a>pgomgr

Přidá data profilu z jednoho nebo více souborů .pgc .pgd souboru.

## <a name="syntax"></a>Syntaxe

> **pgomgr** [*options*] *pgcfiles* *pgdfile*

### <a name="parameters"></a>Parametry

*Možnosti*<br/>
Tyto možnosti lze zadat do **pgomgr –**:

- **/ help** nebo **/?** Zobrazí dostupné **pgomgr –** možnosti.

- **/ clear** způsobí, že soubor .pgd vymazat všechny informace o profilu. Nelze zadat .pgc souboru, když **/clear** je zadán.

- **/ podrobností** zobrazuje podrobné statistiky, včetně toku grafu pokrytí informací.

- **/ souhrnné** zobrazí za – funkce statistiky.

- **/ Jedinečný** při použití s **nebo souhrnných**, příčiny dekorované názvy funkcí pro zobrazení. Výchozí nastavení, když **/ jedinečný** nepoužívá, je pro názvy bez upraveného funkce, který se má zobrazit.

- **/ merge**[**: *** n*] způsobí, že data v .pgc soubor nebo soubory, které mají být přidány do souboru .pgd. Volitelný parametr *n*, umožňuje určit, že má být přidána data *n* časy. Například pokud scénáři běžně by done šestkrát tak, aby odrážela, jak často se provádí zákazníci, můžete to provést jednou spustit test a přidat jej do souboru .pgd šestkrát s **pgomgr – /merge:6**.

*pgcfiles*<br/>
.Pgc jeden nebo více souborů, jejichž data profilu můžete sloučit do souboru .pgd. Můžete zadat soubor .pgc jeden nebo více souborů .pgc. Pokud nezadáte žádné soubory .pgc **pgomgr –** slučuje všechny .pgc soubory, jejichž názvy souborů jsou stejné jako soubor .pgd.

*pgdfile* .pgd souboru, do kterého jsou slučování dat z .pgc soubor či soubory.

## <a name="remarks"></a>Poznámky

> [!NOTE]
> Tento nástroj můžete spustit pouze z příkazového řádku vývojáře Visual Studio. Nelze ji spustit z příkazového řádku systému nebo v Průzkumníku souborů.

## <a name="example"></a>Příklad

Tento ukázkový příkaz vymaže myapp.pgd soubor data profilu:

`pgomgr /clear myapp.pgd`

Tento ukázkový příkaz přidá data profilu v myapp1.pgc soubor .pgd třikrát:

`pgomgr /merge:3 myapp1.pgc myapp.pgd`

V tomto příkladu se data profilu z všechny soubory # .pgc Moje aplikace přidá do souboru myapp.pgd.

`pgomgr -merge myapp1.pgd`

## <a name="see-also"></a>Viz také

[Optimalizace na základě profilu](profile-guided-optimizations.md)<br/>
[PgoAutoSweep](pgoautosweep.md)<br/>
[pgosweep](pgosweep.md)<br/>
