---
title: "Postupy: sloučení několika profilů PGO do jediného profilu | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- merging profiles
- profile-guided optimizations, merging profiles
ms.assetid: aab686b5-59dd-40d1-a04b-5064690f65a6
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 880e9fbba7852a9a7919e73f80b73e34394cd037
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-merge-multiple-pgo-profiles-into-a-single-profile"></a>Postupy: Sloučení několika profilů PGO do jediného profilu
Optimalizace na základě profilu (PGO) je skvělý nástroj pro vytváření optimalizované binární soubory podle scénáře, který je vytvořený profil. Ale co když máte aplikaci, který má několik důležitých, ještě odlišné scénáře; jak vytvořit jeden profil, který můžete použít PGO z několika různých scénářů? V sadě Visual Studio správce PGO Pgomgr.exe, provede tuto úlohu.  
  
 Slučování profilů syntaxe je:  
  
```  
pgomgr /merge[:num] [.pgc_files] .pgd_files  
```  
  
 kde `num` je volitelné váhy, který se používá pro tento sloučení. Vah se běžně používají, pokud je několik scénářů, které jsou důležitější než jiná, nebo pokud existují scénáře, které se mají spustit vícekrát.  
  
> [!NOTE]
>  Správce PGO nebude pracovat s daty zastaralé profilu. Pokud chcete soubor .pgc do souboru .pgd, musí být vygenerovaný soubor .pgc spustitelný soubor, který byl vytvořen ve stejné generovaný soubor .pgd vyvolání odkazu.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu správce PGO přidá pgcFile.pgc pgdFile.pgd šestkrát.  
  
```  
pgomgr /merge:6 pgcFile.pgc pgdFile.pgd  
```  
  
## <a name="example"></a>Příklad  
 V tomto příkladu bude PGO Manager přidat pgcFile1.pgc a pgcFile2.pgc do pgdFile.pgd dvakrát pro každý soubor .pgc.  
  
```  
pgomgr /merge:2 pgcFile1.pgc pgcFile2.pgc pgdFile.pgd  
```  
  
## <a name="example"></a>Příklad  
 Pokud je spuštěn správce PGO bez souboru .pgc prohledá místní adresář pro všechny .pgc soubory, které mají stejný název jako soubor .pgd spolu s vykřičníkem (!) následuje libovolný znaků. Pokud má místní adresář souborů test.pgd, test!1.pgc, test2.pgc a test!hello.pgc a spuštění následujícího příkazu z místního adresáře, pak test!1.pgc a test!hello.pgc budou sloučena do test.pgd.  
  
```  
pgomgr /merge test.pgd  
```  
  
## <a name="see-also"></a>Viz také  
 [Optimalizace na základě profilu](../../build/reference/profile-guided-optimizations.md)