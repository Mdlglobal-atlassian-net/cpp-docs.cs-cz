---
title: Místo definice maker | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- defining macros
- macros, NMAKE
- NMAKE program, defining macros
ms.assetid: 0fc59ec5-5f58-4644-b7da-7b021f7001af
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 29a2899d7dba0b34c0ac3319c253c8056912d883
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45713814"
---
# <a name="where-to-define-macros"></a>Místo definice maker

V příkazovém řádku, souboru příkazů, souboru pravidel nebo souboru Tools.ini definice maker.

V souboru pravidel nebo soubor Tools.ini každé definici makra musí být na samostatném řádku a nesmí začínat mezera nebo tabulátor. Mezery ani tabulátory znaménku rovná se ignorují. Všechny [řetězec znaků](../build/defining-an-nmake-macro.md) jsou literálu, včetně uvozovek a vložené mezery.

V příkazovém řádku nebo v souboru příkazů mezerami a tabulátory vymezení argumenty a nelze před a za znaménko rovná se. Pokud `string` obsahuje vložené mezery nebo tabulátory, samotný řetězec nebo celé makro uzavřete do dvojitých uvozovek ("").

## <a name="see-also"></a>Viz také

[Definice makra NMAKE](../build/defining-an-nmake-macro.md)