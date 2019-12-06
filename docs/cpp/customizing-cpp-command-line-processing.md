---
title: Přizpůsobení zpracování příkazového řádku jazyka C++
ms.date: 11/04/2016
f1_keywords:
- _setenvp
- _setargv
helpviewer_keywords:
- command line [C++], processing
- command-line processing
- startup code, customizing command-line processing
- environment, environment-processing routine
- _setargv function
- command line [C++], processing arguments
- suppressing environment processing
- _setenvp function
ms.assetid: aae01cbb-892b-48b8-8e1f-34f22421f263
ms.openlocfilehash: 1541840521695658b5c4d809ba7e11767b1330a2
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857551"
---
# <a name="customizing-c-command-line-processing"></a>Přizpůsobení zpracování příkazového řádku jazyka C++

**Specifické pro společnost Microsoft**

Pokud aplikace nepřijímá argumenty příkazového řádku, je možné ušetřit malé množství místa potlačením použití rutiny knihovny, která vykonává zpracování příkazového řádku. Tato rutina se nazývá `_setargv` a je popsána v tématu [rozšíření zástupných znaků](../cpp/wildcard-expansion.md). Chcete-li potlačit jeho použití, definujte rutinu, která neprovede nic v souboru obsahujícím funkci `main` a pojmenujte ji `_setargv`. Volání `_setargv` je pak vyhovující vaší definicí `_setargv`a verze knihovny není načtena.

Podobně pokud nikdy nepřistupujete k tabulce prostředí pomocí argumentu `envp`, můžete poskytnout vlastní prázdnou rutinu, která bude použita místo `_setenvp`, rutiny zpracování prostředí. Stejně jako u funkce `_setargv` musí být `_setenvp` deklarované jako **extern "C"** .

Váš program může volat do `spawn` nebo `exec` rodinu rutin v knihovně run-time jazyka C. Jde-li o tento případ, neměla by být rutina zpracování prostředí potlačena, protože slouží k předání prostředí z nadřazeného procesu podřízenému procesu.

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také:

[main: spuštění programu](../cpp/main-program-startup.md)