---
title: "Závažná chyba C1902 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C1902
dev_langs: C++
helpviewer_keywords: C1902
ms.assetid: 2dc066cc-fcb1-4725-8bcb-9f44dd0905b7
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 89354565f67c8704eee8c8b5f9dcb94523800c63
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="fatal-error-c1902"></a>Závažná chyba C1902
Neshoda správce databáze programu; Zkontrolujte, zda vaše instalace  
  
Soubor databáze programu (.pdb) byl vytvořen pomocí novější verze mspdb*XXX*.dll než ten, který kompilátor v systému nalezena. Tato chyba obvykle označuje, že mspdbsrv.exe nebo mspdbcore.dll chybí, nebo mají různé verze než mspdb*XXX*.dll. ( *XXX* zástupný symbol v mspdb*XXX*.dll změny názvu souboru při každém vydání produktu. Například v sadě Visual Studio 2015 název souboru je mspdb140.dll.)  
  
Zajistěte odpovídající verze mspdbsrv.exe, mspdbcore.dll a mspdb*XXX*.dll jsou nainstalovány ve vašem systému. Ujistěte se, že neodpovídající verze nebyly byl zkopírován do adresáře, který obsahuje nástroje kompilátoru a odkaz pro svou cílovou platformu. Například, pravděpodobně jste zkopírovali soubory, může vyvolat nástroj kompilátoru nebo odkaz na příkazovém řádku bez nastavení **cesta** proměnnou prostředí odpovídajícím způsobem.