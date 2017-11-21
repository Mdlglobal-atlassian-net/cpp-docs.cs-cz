---
title: "Upozornění nástroje NMAKE U4004 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: U4004
dev_langs: C++
helpviewer_keywords: U4004
ms.assetid: 5086bbcb-42d7-4677-a877-1a02202a86a2
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: b629bd2910b2820cc703824a5a97bf3361ac54b6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="nmake-warning-u4004"></a>Upozornění nástroje NMAKE U4004
příliš mnoho pravidel pro cíl targetname  
  
 Byl zadán více než jeden blok popis pro danou cílovou pomocí jednom dvojtečky (**:**) jako oddělovače. NMAKE spustit příkazy v bloku první popis a ignorovány novější bloky.  
  
 Pro zadání stejného cíle ve více závislostí, použijte dvojité dvojtečky (`::`) jako oddělovač v každém řádku závislostí.