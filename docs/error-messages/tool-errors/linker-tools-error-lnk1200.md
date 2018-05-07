---
title: Chyba linkerů Lnk1200 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1200
dev_langs:
- C++
helpviewer_keywords:
- LNK1200
ms.assetid: 55771145-915e-4006-ac6c-ac702041eb2f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ab32939c55dce5e27f907f3d23e639b24741cdc3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-error-lnk1200"></a>Chyba linkerů LNK1200
Chyba při čtení databáze programu 'název souboru.  
  
 Nepodařilo se přečíst databázi programu (PDB).  
  
 Tato chyba může být způsobeno poškození souboru.  
  
 Pokud `filename` je PDB soubor objektu znovu zkompiluje objekt souboru pomocí [/Zi](../../build/reference/z7-zi-zi-debug-information-format.md).  
  
 Pokud `filename` je PDB pro hlavní výstupní soubor a k této chybě došlo během přírůstkové odkaz, odstraňte PDB a znovu připojit.