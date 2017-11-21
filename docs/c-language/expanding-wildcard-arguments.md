---
title: "Rozbalení argumentů zástupných znaků | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- asterisk wildcard
- question mark, wildcard
- expanding wildcard arguments
- wildcards, expanding
ms.assetid: 80a11c4b-0199-420e-a342-cf1d803be5bc
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b0c1deca52e74241b56c3c152e66a74d652b4829
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="expanding-wildcard-arguments"></a>Rozbalení argumentů zástupných znaků
**Konkrétní Microsoft**  
  
 Při spuštění programu C, můžete použít buď dva zástupné znaky – otazník (?) a hvězdička (*) – chcete zadat název souboru a cesta argument v příkazovém řádku.  
  
 Ve výchozím nastavení nejsou zástupné znaky rozšířit argumentů příkazového řádku. Můžete nahradit vektoru normální argument `argv` načítání rutiny s verzí, která pomocí propojení se souborem setargv.obj nebo wsetargv.obj rozbalte zástupné znaky. Pokud váš program používá `main` funkce, odkaz s setargv.obj. Pokud váš program používá `wmain` funkce, odkaz s wsetargv.obj. Mají obě tyto ekvivalentní chování.  
  
 Odkaz s setargv.obj nebo wsetargv.obj, použijte **/link** možnost. Příklad:  
  
 **setargv.obj/Link example.c cl**  
  
 Zástupné znaky jsou rozšířit stejným způsobem jako příkazy operačního systému. (Viz příručka uživatele operačního systému, pokud jste obeznámeni s zástupné znaky.)  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Možnosti odkazů](../c-runtime-library/link-options.md)   
 [hlavní funkce a spuštění programu](../c-language/main-function-and-program-execution.md)