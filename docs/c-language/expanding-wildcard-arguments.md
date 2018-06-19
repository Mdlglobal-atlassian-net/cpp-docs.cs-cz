---
title: Rozbalení argumentů zástupných znaků | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- asterisk wildcard
- question mark, wildcard
- expanding wildcard arguments
- wildcards, expanding
ms.assetid: 80a11c4b-0199-420e-a342-cf1d803be5bc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 69d7a9fc75e23a03e4db232bc798c89f89083e62
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32383628"
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