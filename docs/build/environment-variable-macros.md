---
title: Makra proměnné prostředí | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, environment variable macros
- environment variables, macros in NMAKE
- macros, environment-variable
ms.assetid: f8e96635-0906-47b0-9f56-12a6fdf5e347
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9ebebb6e7d237746f96c7ac7e27c249244ff825b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
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