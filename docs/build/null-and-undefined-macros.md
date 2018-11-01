---
title: Hodnota Null a nedefinovaná makra
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, undefined macros
- Null macros in NMAKE
- macros, null and undefined
- undefined macros and NMAKE
- NMAKE program, null macros
ms.assetid: 1db4611a-1755-4328-b00f-d35365af8b6c
ms.openlocfilehash: f6f294234f7244b65137742e1fe8abaa37a676a5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50498914"
---
# <a name="null-and-undefined-macros"></a>Hodnota Null a nedefinovaná makra

Hodnota null a Nedefinovaná makra rozšířit na řetězce s hodnotou null, ale je makro definované jako řetězec s hodnotou null se považuje za definované v předběžném zpracování výrazů. Chcete-li definovat makro jako řetězec s hodnotou null, zadejte žádné znaky kromě mezery ani tabulátory za znaménkem rovnítka (=) v příkazovém řádku nebo souboru příkazů a řetězec s hodnotou null nebo definice uzavřít do dvojitých uvozovek (""). Chcete-li zrušit makra, použijte **! UNDEF.** Další informace najdete v tématu [direktivy předběžného zpracování souboru pravidel](../build/makefile-preprocessing-directives.md).

## <a name="see-also"></a>Viz také

[Definice makra NMAKE](../build/defining-an-nmake-macro.md)