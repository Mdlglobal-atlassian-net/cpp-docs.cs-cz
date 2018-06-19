---
title: Zadání vloženého souboru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, inline files
- inline files [C++], specifying NMAKE
- files [C++], inline
ms.assetid: 393eccfb-3fc9-4bac-a30c-8ac8d221cca3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2c0d85436aef5ed48c0a8787f8bce330bf6d3e96
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32380102"
---
# <a name="specifying-an-inline-file"></a>Zadání vloženého souboru
Zadejte dvě lomené závorky (<<) v příkazu kde *filename* se má zobrazit. Makro rozšíření nemůže být lomené závorky.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<<[filename]  
```  
  
## <a name="remarks"></a>Poznámky  
 Při spuštění příkazu se nahrazují lomené závorky *filename*, pokud zadaný nebo jedinečný název generované NMAKE. -Li zadána, *filename* musí následovat lomené závorky bez mezera nebo kartě. Cestu je povolená. Žádné rozšíření je požadovaná nebo předpokládá, že. Pokud *filename* je zadaný soubor je vytvořen v aktuální nebo zadaný adresář přepsal všechny existující soubor s tímto názvem; jinak, je vytvořen v adresáři TMP (nebo v aktuálním adresáři, pokud TMP proměnné prostředí není definována). Pokud předchozí *filename* je opakovaně, NMAKE nahradí předchozí soubor.  
  
## <a name="see-also"></a>Viz také  
 [Soubory vložené do souboru pravidel](../build/inline-files-in-a-makefile.md)