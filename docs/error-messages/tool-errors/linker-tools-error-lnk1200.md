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
ms.openlocfilehash: 792c81e36b99bbac6c0417f0230bb1ea2bb1787c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="linker-tools-error-lnk1200"></a>Chyba linkerů LNK1200
Chyba při čtení databáze programu 'název souboru.  
  
 Nepodařilo se přečíst databázi programu (PDB).  
  
 Tato chyba může být způsobeno poškození souboru.  
  
 Pokud `filename` je PDB soubor objektu znovu zkompiluje objekt souboru pomocí [/Zi](../../build/reference/z7-zi-zi-debug-information-format.md).  
  
 Pokud `filename` je PDB pro hlavní výstupní soubor a k této chybě došlo během přírůstkové odkaz, odstraňte PDB a znovu připojit.