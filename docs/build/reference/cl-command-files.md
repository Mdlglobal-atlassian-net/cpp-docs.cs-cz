---
title: "Soubory příkazů CL | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- cl
dev_langs:
- C++
helpviewer_keywords:
- cl.exe compiler, command files
- command files
- command files, CL compiler
ms.assetid: ec3cea06-2af0-4fe9-a94c-119c9d31b3a9
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a711b2f4a484a6370af828c5d0aad522686ca3f1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cl-command-files"></a>Soubory příkazů CL
Příkaz Soubor je textový soubor, který obsahuje možnosti a názvy souborů, v opačném případě zadejte na [příkazového řádku](../../build/reference/compiler-command-line-syntax.md) nebo zadejte pomocí [proměnné prostředí CL](../../build/reference/cl-environment-variables.md). CL příkazového řádku kompilátoru přijímá jako argument v proměnné prostředí CL nebo na příkazovém řádku. Na rozdíl od příkazového řádku nebo proměnné prostředí CL umožňuje soubor příkazů použít několik řádků parametrů a názvů souborů.  
  
 Možnosti a názvy souborů v souboru příkaz se zpracovávají podle umístění v rámci proměnné prostředí CL nebo na příkazovém řádku příkaz název souboru. Ale pokud/Link možnost se zobrazí v příkazového řádku, všechny možnosti na zbytek řádku jsou předány linkeru. Možnosti v následujících řádcích v příkazového řádku a možnosti na příkazovém řádku po vyvolání příkazu souboru jsou stále přijato jako – možnosti kompilátoru. Další informace o jak ovlivňuje pořadí možnosti jejich interpretace najdete v tématu [pořadí možností CL](../../build/reference/order-of-cl-options.md).  
  
 Soubor příkazů nesmí obsahovat příkaz CL. Každá možnost musí začínat a končit na stejné přímce; nemůžete použít zpětné lomítko (\\) kombinovat možnost na dvou řádcích.  
  
 Soubor příkazů je určeného znaku zavináče (@) následuje název souboru; Název souboru můžete zadat absolutní nebo relativní cesta.  
  
 Například, pokud je v souboru s názvem od následující příkaz:  
  
```  
/Og /link LIBC.LIB  
```  
  
 a zadejte následující příkaz CL:  
  
```  
CL /Ob2 @RESP MYAPP.C  
```  
  
 příkaz pro CL vypadá takto:  
  
```  
CL /Ob2 /Og MYAPP.C /link LIBC.LIB  
```  
  
 Všimněte si, efektivně kombinaci příkazového řádku a příkazy příkazového řádku.  
  
## <a name="see-also"></a>Viz také  
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)   
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)