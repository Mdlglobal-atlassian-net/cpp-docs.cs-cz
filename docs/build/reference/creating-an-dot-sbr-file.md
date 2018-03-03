---
title: "Vytváření. Soubor SBR | Microsoft Docs"
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
- SBR files
- BSCMAKE, input files
- .sbr files
- source browser files
- local symbols in browse information
- symbols
ms.assetid: bdb4b93c-a88a-441a-84fd-01087d03be25
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d87b71daaf5d7b37e67c2c0e56e844bd5251a490
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="creating-an-sbr-file"></a>Vytvoření souboru .Sbr
Vstupní soubory pro BSCMAKE jsou soubory .sbr. Kompilátor vytvoří soubor .sbr pro každý objekt soubor (.obj) kompilaci. Při vytvoření nebo aktualizaci vaší soubor s informacemi o procházení, všechny soubory .sbr pro svůj projekt musí být k dispozici na disku.  
  
 Pokud chcete vytvořit soubor .sbr všechny možné informace, zadejte [/FR](../../build/reference/fr-fr-create-dot-sbr-file.md).  
  
 Pokud chcete vytvořit soubor .sbr, který neobsahuje lokální symboly, zadejte [/Fr](../../build/reference/fr-fr-create-dot-sbr-file.md). Pokud soubory .sbr obsahují lokální symboly, můžete stále vynechat je ze souboru BSC programem BSCMAKE společnosti pomocí [/El – možnost](../../build/reference/bscmake-options.md)`.`  
  
 Můžete vytvořit soubor .sbr bez provedení úplné kompilace. Například můžete zadat /Zs – možnost kompilátoru provést kontrolu syntaxe a pokud zadáte /FR nebo /Fr. stále vytvořit soubor .sbr  
  
 Proces sestavení může být efektivnější, pokud jsou soubory .sbr nejdřív zabalit odebrat neodkazované definice. Kompilátor automaticky sady soubory .sbr.  
  
## <a name="see-also"></a>Viz také  
 [Sestavení souboru .Bsc](../../build/reference/building-a-dot-bsc-file.md)