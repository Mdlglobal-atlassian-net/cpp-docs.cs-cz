---
title: NÁZEV (C/C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- name
dev_langs:
- C++
helpviewer_keywords:
- NAME .def file statement
ms.assetid: 5c9b6bd8-9275-46a5-afba-f17a5936dc26
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a94b82a65cf68d9802d7bf9620e4128ab6b35071
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
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