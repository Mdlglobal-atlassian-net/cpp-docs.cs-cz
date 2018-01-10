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
ms.workload: cplusplus
ms.openlocfilehash: fcbda9dd9d7ca5ecb99e46b9916fb95c2c560e49
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="nmake-warning-u4004"></a>Upozornění nástroje NMAKE U4004
příliš mnoho pravidel pro cíl targetname  
  
 Byl zadán více než jeden blok popis pro danou cílovou pomocí jednom dvojtečky (**:**) jako oddělovače. NMAKE spustit příkazy v bloku první popis a ignorovány novější bloky.  
  
 Pro zadání stejného cíle ve více závislostí, použijte dvojité dvojtečky (`::`) jako oddělovač v každém řádku závislostí.