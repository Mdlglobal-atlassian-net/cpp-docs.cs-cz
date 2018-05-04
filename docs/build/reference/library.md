---
title: KNIHOVNA | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- LIBRARY
dev_langs:
- C++
helpviewer_keywords:
- LIBRARY .def file statement
ms.assetid: 1d7ccc92-e088-4ef7-9ef0-25c3862cc051
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0d2fb7e69b0557bf96601666c390b3d59412b5a0
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="library"></a>KNIHOVNA
Oznamuje odkaz pro vytvoření knihovny DLL. Ve stejnou dobu propojení vytvoří knihovnu importu, pokud soubor .exp není použit v sestavení.  
  
```  
LIBRARY [library][BASE=address]  
```  
  
## <a name="remarks"></a>Poznámky  
 *Knihovny* argument určuje název knihovny DLL. Můžete také [/OUT](../../build/reference/out-output-file-name.md) – možnost linkeru k zadání názvu výstupní knihovnu DLL.  
  
 ZÁKLADNÍ =*adresu* argument nastaví základní adresu, která používá operační systém načíst knihovnu DLL. Tento argument přepíše výchozí umístění knihovny DLL 0x10000000. Viz popis [/základní](../../build/reference/base-base-address.md) možnost Podrobnosti o základní adresy.  
  
 Nezapomeňte použít [/dll](../../build/reference/dll-build-a-dll.md) – možnost linkeru při sestavování knihovny DLL.  
  
## <a name="see-also"></a>Viz také  
 [Pravidla pro příkazy definice modulu](../../build/reference/rules-for-module-definition-statements.md)