---
title: Chyba kompilátoru prostředků RC2001 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RC2001
dev_langs:
- C++
helpviewer_keywords:
- RC2001
ms.assetid: 92bfb4c0-1879-4606-bb9f-ef7368707b4a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0ef1fd5d29fc5784ee418a8456cacec37e943b73
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="resource-compiler-error-rc2001"></a>Chyba kompilátoru prostředků RC2001
nový řádek v konstantě  
  
 Řetězcová konstanta pokračuje na druhém řádku bez buď zpětné lomítko (**\\**) nebo zavřením a otevřením dvojitých uvozovek nahoře (**"**).  
  
 Pokud chcete rozdělit na řetězcovou konstantu, který je na dva řádky v zdrojový soubor, proveďte jednu z následujících:  
  
-   Ukončení první řádek s znak pokračování řádku, zpětné lomítko.  
  
-   Řetězec na první řádek s uvozovky zavřete a otevřete řetězec na dalším řádku s jinou dvojité uvozovky.  
  
 Není dostatečná pro ukončení první řádek s \n, řídicí sekvence pro vložení znak nového řádku do řetězcová konstanta.