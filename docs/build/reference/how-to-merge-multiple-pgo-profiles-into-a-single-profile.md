---
title: 'Postupy: Sloučení několika profilů PGO do jediného profilu'
ms.date: 03/14/2018
helpviewer_keywords:
- merging profiles
- profile-guided optimizations, merging profiles
ms.assetid: aab686b5-59dd-40d1-a04b-5064690f65a6
ms.openlocfilehash: 04730524fa756b0c6f1e505f3610609bdec6262a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50476541"
---
# <a name="how-to-merge-multiple-pgo-profiles-into-a-single-profile"></a>Postupy: Sloučení několika profilů PGO do jediného profilu

Profilově řízené optimalizace (PGO) je skvělým nástrojem k vytvoření optimalizované binárních souborů založené na scénářích, která je profilována. Ale co když máte aplikaci, která obsahuje několik důležitých, ještě odlišné scénáře? Jak vytvořit jeden profil, který můžete použít PGO z několika různých scénářů? V sadě Visual Studio, správce PGO [pgomgr.exe](pgomgr.md), dělá tuto práci za vás.

Slučování profilů syntaxe je:

`pgomgr /merge[:num] [.pgc_files] .pgd_files`

kde `num` je volitelné nenáročných až po použít pro soubory .pgc přidal toto sloučení. Váhy se běžně používají při některých scénářích, které jsou důležitější než jiné, nebo pokud existují scénáře, které se mají spustit více než jednou.

> [!NOTE]
> Správce PGO nefunguje s daty zastaralé profilu. Soubor .pgc sloučit do souboru .pgd, musí být soubor .pgc vygenerovaný spustitelný soubor, který byl vytvořen pomocí stejného při vyvolání odkazu, který vygeneroval soubor .pgd.

## <a name="examples"></a>Příklady

V tomto příkladu PGO správce přidá pgcFile.pgc pgdFile.pgd šestkrát:

`pgomgr /merge:6 pgcFile.pgc pgdFile.pgd`

V tomto příkladu přidá správce PGO pgcFile1.pgc a pgcFile2.pgc do pgdFile.pgd dvakrát pro každý soubor .pgc:

`pgomgr /merge:2 pgcFile1.pgc pgcFile2.pgc pgdFile.pgd`

Pokud správce PGO je spuštěn bez argumentů souboru .pgc, hledá místní adresář pro všechny soubory .pgc, které mají stejný základní název jako soubor .pgd, za nímž následuje vykřičník (!) a potom minimálně jeden libovolný znak. Například, pokud má místní adresář souborů test.pgd, test!1.pgc, test2.pgc a test!hello.pgc a následujícího příkazu spusťte z místního adresáře, pak **pgomgr** sloučí test!1.pgc a test!hello.pgc test.pgd.

`pgomgr /merge test.pgd`

## <a name="see-also"></a>Viz také:

[Optimalizace na základě profilu](../../build/reference/profile-guided-optimizations.md)
