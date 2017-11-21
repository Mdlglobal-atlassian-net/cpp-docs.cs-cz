---
title: KNIHOVNA | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: LIBRARY
dev_langs: C++
helpviewer_keywords: LIBRARY .def file statement
ms.assetid: 1d7ccc92-e088-4ef7-9ef0-25c3862cc051
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 75f337f563707a1ab2b1dabe0042b678c03172e7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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