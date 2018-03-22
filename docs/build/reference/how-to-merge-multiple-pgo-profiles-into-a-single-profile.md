---
title: 'Postupy: sloučení několika profilů PGO do jediného profilu | Microsoft Docs'
ms.custom: ''
ms.date: 03/14/2018
ms.technology:
- cpp-tools
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- merging profiles
- profile-guided optimizations, merging profiles
ms.assetid: aab686b5-59dd-40d1-a04b-5064690f65a6
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 450aa6c763c44176ce6cb03313abcb419dc7315c
ms.sourcegitcommit: ee7d74683af7631441c8c7f65ef5ceceaee4a5ee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/22/2018
---
# <a name="how-to-merge-multiple-pgo-profiles-into-a-single-profile"></a>Postupy: Sloučení několika profilů PGO do jediného profilu

Optimalizace na základě profilu (PGO) je skvělý nástroj pro vytváření optimalizované binární soubory podle scénáře, který je vytvořený profil. Ale co když máte aplikaci, která má několik důležitých, ještě odlišné scénáře? Jak vytvořit jeden profil, který můžete použít PGO z několika různých scénářů? V sadě Visual Studio, správce PGO [pgomgr.exe](pgomgr.md), tato úloha provede za vás.

Slučování profilů syntaxe je:

`pgomgr /merge[:num] [.pgc_files] .pgd_files`

kde `num` je volitelné váhy použít pro soubory .pgc přidal tento sloučení. Vah se běžně používají, pokud je několik scénářů, které jsou důležitější než jiná, nebo pokud existují scénáře, které se mají spustit vícekrát.

> [!NOTE]
> Správce PGO nefunguje s daty zastaralé profilu. Pokud chcete soubor .pgc do souboru .pgd, musí být vygenerovaný soubor .pgc spustitelný soubor, který byl vytvořen ve stejné generovaný soubor .pgd vyvolání odkazu.

## <a name="examples"></a>Příklady

V tomto příkladu správce PGO přidá pgcFile.pgc pgdFile.pgd šestkrát:

`pgomgr /merge:6 pgcFile.pgc pgdFile.pgd`

V tomto příkladu správce PGO přidá pgcFile1.pgc a pgcFile2.pgc pgdFile.pgd dvakrát pro každý soubor .pgc:

`pgomgr /merge:2 pgcFile1.pgc pgcFile2.pgc pgdFile.pgd`

Pokud správce PGO je spustit bez argumentů souboru .pgc, prohledává místní adresář pro všechny .pgc soubory, které mají stejné základní název jako soubor .pgd následovaný vykřičníkem (!) a potom nejméně jeden libovolný znak. Pokud místní adresář má test.pgd soubory, test!1.pgc, test2.pgc a test!hello.pgc a je z místního adresáře pak spusťte následující příkaz například **pgomgr –** slučuje test!1.pgc a test!hello.pgc do test.pgd.

`pgomgr /merge test.pgd`

## <a name="see-also"></a>Viz také

[Optimalizace na základě profilu](../../build/reference/profile-guided-optimizations.md)
