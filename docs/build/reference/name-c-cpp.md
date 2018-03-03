---
title: "NÁZEV (C/C++) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- name
dev_langs:
- C++
helpviewer_keywords:
- NAME .def file statement
ms.assetid: 5c9b6bd8-9275-46a5-afba-f17a5936dc26
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 33e81f63e7647cbdbdc89b37ffdcb309b79e9340
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="name-cc"></a>NÁZEV (C/C++)
Určuje název pro hlavní výstupní soubor.  
  
```  
NAME [application][BASE=address]  
```  
  
## <a name="remarks"></a>Poznámky  
 Ekvivalentní způsob zadejte název výstupního souboru je [/OUT](../../build/reference/out-output-file-name.md) – možnost linkeru a ekvivalentní způsob, jak základní adresa je [/základní](../../build/reference/base-base-address.md) – možnost linkeru. Pokud jsou zadány oba/přepsání na více systémů **název**.  
  
 Pokud vytvoříte knihovny DLL, bude název ovlivní pouze název souboru DLL.  
  
## <a name="see-also"></a>Viz také  
 [Pravidla pro příkazy definice modulu](../../build/reference/rules-for-module-definition-statements.md)