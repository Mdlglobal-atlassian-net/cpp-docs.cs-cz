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
ms.openlocfilehash: cf2dce2132cc1e7065cb0b93f1debd403f7a8342
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57417226"
---
# <a name="null-and-undefined-macros"></a>Hodnota Null a nedefinovaná makra

Hodnota null a Nedefinovaná makra rozšířit na řetězce s hodnotou null, ale je makro definované jako řetězec s hodnotou null se považuje za definované v předběžném zpracování výrazů. Chcete-li definovat makro jako řetězec s hodnotou null, zadejte žádné znaky kromě mezery ani tabulátory za znaménkem rovnítka (=) v příkazovém řádku nebo souboru příkazů a řetězec s hodnotou null nebo definice uzavřít do dvojitých uvozovek (""). Chcete-li zrušit makra, použijte **! UNDEF.** Další informace najdete v tématu [direktivy předběžného zpracování souboru pravidel](../build/makefile-preprocessing-directives.md).

## <a name="see-also"></a>Viz také:

[Definice makra NMAKE](../build/defining-an-nmake-macro.md)
