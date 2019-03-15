---
title: Místo definice maker
ms.date: 11/04/2016
helpviewer_keywords:
- defining macros
- macros, NMAKE
- NMAKE program, defining macros
ms.assetid: 0fc59ec5-5f58-4644-b7da-7b021f7001af
ms.openlocfilehash: dc03644adea4619b3eabe33c481d71f704a9f410
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57823350"
---
# <a name="where-to-define-macros"></a>Místo definice maker

V příkazovém řádku, souboru příkazů, souboru pravidel nebo souboru Tools.ini definice maker.

V souboru pravidel nebo soubor Tools.ini každé definici makra musí být na samostatném řádku a nesmí začínat mezera nebo tabulátor. Mezery ani tabulátory znaménku rovná se ignorují. Všechny [řetězec znaků](defining-an-nmake-macro.md) jsou literálu, včetně uvozovek a vložené mezery.

V příkazovém řádku nebo v souboru příkazů mezerami a tabulátory vymezení argumenty a nelze před a za znaménko rovná se. Pokud `string` obsahuje vložené mezery nebo tabulátory, samotný řetězec nebo celé makro uzavřete do dvojitých uvozovek ("").

## <a name="see-also"></a>Viz také:

[Definice makra NMAKE](defining-an-nmake-macro.md)
