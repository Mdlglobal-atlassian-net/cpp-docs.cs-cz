---
title: "Práce s importovanými knihovnami a exportovanými soubory | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- LIB [C++], /DEF option
- import libraries
- LIB [C++], import libraries and export files
- export files
- import libraries, creating
ms.assetid: d8175596-9773-4c2f-959d-b05b065a5161
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: a78f6e4c7cdb5dbd25354d93d9bafc2892098c7d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="working-with-import-libraries-and-export-files"></a>Práce s importovanými knihovnami a exportovanými soubory
LIB s parametrem/DEF slouží k vytvoření knihovnu importu a souboru exportu. ODKAZ používá exportu souboru k vytvoření programu, který obsahuje vyexportuje (obvykle dynamické knihovny (DLL)) a používá knihovny importu odkazy na tyto exporty v jiných aplikacích.  
  
 Všimněte si, že když vytvoříte své knihovny importu v předběžný krok před vytvořením vaší .dll, je nutné předat stejnou sadu soubory objektů při sestavování .dll, jako předaný při sestavení knihovny importu.  
  
 Ve většině případů není potřeba použít k vytvoření knihovny importu LIB. Při propojení programu (spustitelného souboru nebo knihovny DLL), který obsahuje Exportuje odkaz automaticky vytvoří knihovnu importu, který popisuje exporty. Později když připojujete program, který odkazuje na tyto exporty, zadejte knihovnu, import.  
  
 Ale při programu, který umožňuje importovat taková také z provede export knihovny DLL, jestli přímo ani nepřímo, používejte LIB k jeho vytvoření knihoven importovat. Když LIB vytvoří knihovnu importu, také vytvoří soubor exportu. Při propojování jednu z knihoven DLL, je nutné použít soubor exportu.  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace LIB](../../build/reference/lib-reference.md)