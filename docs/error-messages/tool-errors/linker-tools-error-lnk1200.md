---
title: "Chyba linkerů Lnk1200 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK1200
dev_langs: C++
helpviewer_keywords: LNK1200
ms.assetid: 55771145-915e-4006-ac6c-ac702041eb2f
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 70bf262d4f99c807e3488c1f9b2ed9e73b1eb715
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-error-lnk1200"></a>Chyba linkerů LNK1200
Chyba při čtení databáze programu 'název souboru.  
  
 Nepodařilo se přečíst databázi programu (PDB).  
  
 Tato chyba může být způsobeno poškození souboru.  
  
 Pokud `filename` je PDB soubor objektu znovu zkompiluje objekt souboru pomocí [/Zi](../../build/reference/z7-zi-zi-debug-information-format.md).  
  
 Pokud `filename` je PDB pro hlavní výstupní soubor a k této chybě došlo během přírůstkové odkaz, odstraňte PDB a znovu připojit.