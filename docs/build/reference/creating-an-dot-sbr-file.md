---
title: "Vytváření. Soubor SBR | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- SBR files
- BSCMAKE, input files
- .sbr files
- source browser files
- local symbols in browse information
- symbols
ms.assetid: bdb4b93c-a88a-441a-84fd-01087d03be25
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 1fb3638f70d19d88228b8ff65eb78c479868f1b9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="creating-an-sbr-file"></a>Vytvoření souboru .Sbr
Vstupní soubory pro BSCMAKE jsou soubory .sbr. Kompilátor vytvoří soubor .sbr pro každý objekt soubor (.obj) kompilaci. Při vytvoření nebo aktualizaci vaší soubor s informacemi o procházení, všechny soubory .sbr pro svůj projekt musí být k dispozici na disku.  
  
 Pokud chcete vytvořit soubor .sbr všechny možné informace, zadejte [/FR](../../build/reference/fr-fr-create-dot-sbr-file.md).  
  
 Pokud chcete vytvořit soubor .sbr, který neobsahuje lokální symboly, zadejte [/Fr](../../build/reference/fr-fr-create-dot-sbr-file.md). Pokud soubory .sbr obsahují lokální symboly, můžete stále vynechat je ze souboru BSC programem BSCMAKE společnosti pomocí [/El – možnost](../../build/reference/bscmake-options.md)`.`  
  
 Můžete vytvořit soubor .sbr bez provedení úplné kompilace. Například můžete zadat /Zs – možnost kompilátoru provést kontrolu syntaxe a pokud zadáte /FR nebo /Fr. stále vytvořit soubor .sbr  
  
 Proces sestavení může být efektivnější, pokud jsou soubory .sbr nejdřív zabalit odebrat neodkazované definice. Kompilátor automaticky sady soubory .sbr.  
  
## <a name="see-also"></a>Viz také  
 [Vytváření. Souboru BSC](../../build/reference/building-a-dot-bsc-file.md)