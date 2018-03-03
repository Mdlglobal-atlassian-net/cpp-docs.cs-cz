---
title: "Závažná chyba C1902 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C1902
dev_langs:
- C++
helpviewer_keywords:
- C1902
ms.assetid: 2dc066cc-fcb1-4725-8bcb-9f44dd0905b7
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4e5f6c22ea848a49a12cc85508fd80a4cfcb90e0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="fatal-error-c1902"></a>Závažná chyba C1902
Neshoda správce databáze programu; Zkontrolujte, zda vaše instalace  
  
Soubor databáze programu (.pdb) byl vytvořen pomocí novější verze mspdb*XXX*.dll než ten, který kompilátor v systému nalezena. Tato chyba obvykle označuje, že mspdbsrv.exe nebo mspdbcore.dll chybí, nebo mají různé verze než mspdb*XXX*.dll. ( *XXX* zástupný symbol v mspdb*XXX*.dll změny názvu souboru při každém vydání produktu. Například v sadě Visual Studio 2015 název souboru je mspdb140.dll.)  
  
Zajistěte odpovídající verze mspdbsrv.exe, mspdbcore.dll a mspdb*XXX*.dll jsou nainstalovány ve vašem systému. Ujistěte se, že neodpovídající verze nebyly byl zkopírován do adresáře, který obsahuje nástroje kompilátoru a odkaz pro svou cílovou platformu. Například, pravděpodobně jste zkopírovali soubory, může vyvolat nástroj kompilátoru nebo odkaz na příkazovém řádku bez nastavení **cesta** proměnnou prostředí odpovídajícím způsobem.