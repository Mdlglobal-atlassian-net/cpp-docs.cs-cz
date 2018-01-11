---
title: "Chyba kompilátoru prostředků RC2001 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: RC2001
dev_langs: C++
helpviewer_keywords: RC2001
ms.assetid: 92bfb4c0-1879-4606-bb9f-ef7368707b4a
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7c04110898780495f918c1e37c0068daead340a4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="resource-compiler-error-rc2001"></a>Chyba kompilátoru prostředků RC2001
nový řádek v konstantě  
  
 Řetězcová konstanta pokračuje na druhém řádku bez buď zpětné lomítko (**\\**) nebo zavřením a otevřením dvojitých uvozovek nahoře (**"**).  
  
 Pokud chcete rozdělit na řetězcovou konstantu, který je na dva řádky v zdrojový soubor, proveďte jednu z následujících:  
  
-   Ukončení první řádek s znak pokračování řádku, zpětné lomítko.  
  
-   Řetězec na první řádek s uvozovky zavřete a otevřete řetězec na dalším řádku s jinou dvojité uvozovky.  
  
 Není dostatečná pro ukončení první řádek s \n, řídicí sekvence pro vložení znak nového řádku do řetězcová konstanta.