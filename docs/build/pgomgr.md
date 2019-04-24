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

Přidá data profilu z jednoho nebo více souborů .pgc do souboru .pgd.

## <a name="syntax"></a>Syntaxe

> **pgomgr** [*options*] *pgcfiles* *pgdfile*

### <a name="parameters"></a>Parametry

*Možnosti*<br/>
Je možné zadat následující možnosti pro **pgomgr**:

- **/ help** nebo **/?** Zobrazí dostupné **pgomgr** možnosti.

- **/ clear** způsobí, že soubor .pgd vymazání všech informací o profilu. Nelze zadat .pgc souboru, když **/clear** je zadán.

- **/ detail** zobrazuje podrobné statistiky, včetně informací o pokrytí grafu toku.

- **/ summary** zobrazí jednotlivých funkcích statistiky.

- **/ Jedinečný** při použití s **/summary**, způsobí, že dekorované názvy funkce k zobrazení. Výchozí nastavení, když **/ jedinečný** nepoužívá, je pro názvy nedekorovaných funkce má být zobrazen.

- **/ merge**\[**:**<em>n</em>] způsobí, že data v souboru .pgc nebo soubory, které mají být přidány do souboru .pgd. Volitelný parametr *n*, umožňuje určit, že má být přidána data *n* časy. Například pokud scénář obvykle bude Hotovo šestkrát tak, aby odrážely, jak často se provádí zákazníky, můžete provést jednou při spuštění testů a přidat do souboru .pgd šestkrát s **pgomgr /merge:6**.

*pgcfiles*<br/>
.Pgc jeden nebo více soubory, jejichž data profilu, které chcete sloučit do souboru .pgd. Můžete určit soubor .pgc jeden nebo více soubory .pgc. Pokud nezadáte žádné soubory .pgc **pgomgr** sloučí všechny soubory .pgc, jejichž názvy souborů jsou stejné jako soubor .pgd.

*pgdfile*<br/>
Soubor .pgd, do které provádíte sloučení dat ze souboru .pgc nebo soubory.

## <a name="remarks"></a>Poznámky

> [!NOTE]
> Tento nástroj můžete spustit pouze z příkazového řádku pro vývojáře Visual Studio. Nelze provést toto spuštění z příkazového řádku systému nebo Průzkumníka souborů.

## <a name="example"></a>Příklad

Příkaz v tomto příkladu vymaže myapp.pgd soubor dat profilu:

`pgomgr /clear myapp.pgd`

Příkaz v tomto příkladu přidá data profilu v myapp1.pgc do souboru .pgd třikrát:

`pgomgr /merge:3 myapp1.pgc myapp.pgd`

V tomto příkladu se k souboru myapp.pgd přidá data profilu ze všech vygenerovaných souborů myapp # .pgc.

`pgomgr -merge myapp1.pgd`

## <a name="see-also"></a>Viz také:

[Optimalizace na základě profilu](profile-guided-optimizations.md)<br/>
[PgoAutoSweep](pgoautosweep.md)<br/>
[pgosweep](pgosweep.md)<br/>
