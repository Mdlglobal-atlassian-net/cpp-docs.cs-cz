---
title: Závažná chyba C1902 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1902
dev_langs:
- C++
helpviewer_keywords:
- C1902
ms.assetid: 2dc066cc-fcb1-4725-8bcb-9f44dd0905b7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b23507b6531f9ee4e5ce5efd5b60a1977206635c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="fatal-error-c1902"></a>Závažná chyba C1902
Neshoda správce databáze programu; Zkontrolujte, zda vaše instalace  
  
Soubor databáze programu (.pdb) byl vytvořen pomocí novější verze mspdb*XXX*.dll než ten, který kompilátor v systému nalezena. Tato chyba obvykle označuje, že mspdbsrv.exe nebo mspdbcore.dll chybí, nebo mají různé verze než mspdb*XXX*.dll. ( *XXX* zástupný symbol v mspdb*XXX*.dll změny názvu souboru při každém vydání produktu. Například v sadě Visual Studio 2015 název souboru je mspdb140.dll.)  
  
Zajistěte odpovídající verze mspdbsrv.exe, mspdbcore.dll a mspdb*XXX*.dll jsou nainstalovány ve vašem systému. Ujistěte se, že neodpovídající verze nebyly byl zkopírován do adresáře, který obsahuje nástroje kompilátoru a odkaz pro svou cílovou platformu. Například, pravděpodobně jste zkopírovali soubory, může vyvolat nástroj kompilátoru nebo odkaz na příkazovém řádku bez nastavení **cesta** proměnnou prostředí odpovídajícím způsobem.