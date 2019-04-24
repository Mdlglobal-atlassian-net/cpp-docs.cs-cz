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
ms.openlocfilehash: 0f4905473dd6914547ad6ac129d34e438992c2af
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62320497"
---
# <a name="null-and-undefined-macros"></a>Hodnota Null a nedefinovaná makra

Hodnota null a Nedefinovaná makra rozšířit na řetězce s hodnotou null, ale je makro definované jako řetězec s hodnotou null se považuje za definované v předběžném zpracování výrazů. Chcete-li definovat makro jako řetězec s hodnotou null, zadejte žádné znaky kromě mezery ani tabulátory za znaménkem rovnítka (=) v příkazovém řádku nebo souboru příkazů a řetězec s hodnotou null nebo definice uzavřít do dvojitých uvozovek (""). Chcete-li zrušit makra, použijte **! UNDEF.** Další informace najdete v tématu [direktivy předběžného zpracování souboru pravidel](makefile-preprocessing-directives.md).

## <a name="see-also"></a>Viz také:

[Definice makra NMAKE](defining-an-nmake-macro.md)
