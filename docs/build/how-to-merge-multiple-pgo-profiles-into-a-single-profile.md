---
title: 'Postupy: Sloučení několika profilů PGO do jediného profilu'
ms.date: 03/14/2018
helpviewer_keywords:
- merging profiles
- profile-guided optimizations, merging profiles
ms.assetid: aab686b5-59dd-40d1-a04b-5064690f65a6
ms.openlocfilehash: 451c0f30a271f5dce3974e172766da4a23340b93
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62188870"
---
# <a name="how-to-merge-multiple-pgo-profiles-into-a-single-profile"></a>Postupy: Sloučení několika profilů PGO do jediného profilu

Optimalizace na základě profilu (PGO) je skvělý nástroj pro vytváření optimalizovaných binárních souborů v závislosti na scénáři, který je profilované. Ale co dělat v případě, že máte aplikaci, která má několik důležitých, ale u různých scénářů? Jak můžete vytvořit jeden profil, který PGO může použít z několika různých scénářů? V aplikaci Visual Studio PGO Manager [pgomgr. exe](pgomgr.md)tuto úlohu provede za vás.

Syntaxe pro slučování profilů je:

`pgomgr /merge[:num] [.pgc_files] .pgd_files`

kde `num` je volitelná váha, která se má použít pro soubory. pgc přidané tímto sloučením Váhy se běžně používají, pokud existují některé scénáře, které jsou důležitější než jiné, nebo pokud existují scénáře, které se mají spustit několikrát.

> [!NOTE]
> PGO Manager nepracuje se zastaralými daty profilu. Chcete-li sloučit soubor. pgc do souboru. PGD, musí být soubor. pgc vytvořen spustitelným souborem, který byl vytvořen stejným voláním propojení, které vygenerovalo soubor. pgd.

## <a name="examples"></a>Příklady

V tomto příkladu PGO Manager přidá pgcFile. pgc do pgdFile. pgd šest časů:

`pgomgr /merge:6 pgcFile.pgc pgdFile.pgd`

V tomto příkladu PGO Manager přidá pgcFile1. pgc a pgcFile2. pgc do pgdFile. PGD, dvakrát pro každý soubor. pgc:

`pgomgr /merge:2 pgcFile1.pgc pgcFile2.pgc pgdFile.pgd`

Pokud je PGO Manager spuštěn bez argumentů souboru. pgc, hledá místní adresář pro všechny soubory. pgc, které mají stejný základní název jako soubor. pgd následovaný vykřičníkem (!) a pak jedním nebo více libovolnými znaky. Například pokud má místní adresář soubory test. PGD, test! 1. pgc, Test2. pgc a test! Hello. pgc a následující příkaz je spuštěn z místního adresáře, pak **pgomgr** sloučí test! 1. pgc a test! Hello. pgc do souboru Test. pgd.

`pgomgr /merge test.pgd`

## <a name="see-also"></a>Viz také

[Optimalizace na základě profilu](profile-guided-optimizations.md)
