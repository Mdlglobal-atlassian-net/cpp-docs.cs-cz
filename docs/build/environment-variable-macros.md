---
title: "Makra proměnné prostředí | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- NMAKE program, environment variable macros
- environment variables, macros in NMAKE
- macros, environment-variable
ms.assetid: f8e96635-0906-47b0-9f56-12a6fdf5e347
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: b64e6c167df00d072b70a2f39e882a84357b4eab
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="environment-variable-macros"></a>Makra proměnné prostředí
NMAKE dědí definice maker pro proměnné prostředí, které existují před zahájením relace. Pokud proměnná nastavena v prostředí operačního systému, je k dispozici jako makra NMAKE. Zděděné názvy se převedou na velká písmena. Dědičnost dojde před předběžného zpracování. Pomocí možnosti /E způsobit makra zděděno z proměnných prostředí pro přepsání makra se stejným názvem v soubor pravidel.  
  
 Makra proměnné prostředí, můžete jej předefinovat v relaci, a tím změní odpovídající proměnné prostředí. Můžete také změnit proměnné prostředí pomocí příkazu SET. Chcete-li změnit proměnné prostředí v relaci pomocí příkazu SET nezmění odpovídající makro, ale.  
  
 Příklad:  
  
```  
PATH=$(PATH);\nonesuch  
  
all:  
    echo %PATH%  
```  
  
 V tomto příkladu, změna `PATH` změny odpovídající proměnnou prostředí `PATH`; přidá `\nonesuch` pro vaši cestu.  
  
 Pokud proměnná prostředí je definováno jako řetězec, který bude v souboru pravidel správnou syntaxi, vytvoření žádné makra a žádné upozornění je generováno. Pokud hodnota proměnné obsahuje znak dolaru ($), NMAKE interpretovat jako začátek makro volání. Použití makra může způsobit neočekávané chování.  
  
## <a name="see-also"></a>Viz také  
 [Speciální makra NMAKE](../build/special-nmake-macros.md)