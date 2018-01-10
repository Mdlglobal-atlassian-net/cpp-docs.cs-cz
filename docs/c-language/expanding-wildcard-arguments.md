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
ms.workload: cplusplus
ms.openlocfilehash: f710cc1695579bf1a6f873229c347966888bc745
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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
 [main – spuštění funkce a programu](../c-language/main-function-and-program-execution.md)