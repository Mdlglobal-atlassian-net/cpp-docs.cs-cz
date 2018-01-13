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
ms.workload: cplusplus
ms.openlocfilehash: 71637c83eda0ee641a4b66d94ba113162baa7bf2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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