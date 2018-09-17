---
title: Hodnota Null a Nedefinovaná makra | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, undefined macros
- Null macros in NMAKE
- macros, null and undefined
- undefined macros and NMAKE
- NMAKE program, null macros
ms.assetid: 1db4611a-1755-4328-b00f-d35365af8b6c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: eee6e713715e4709af990878224261a41f5470e3
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45702634"
---
# <a name="null-and-undefined-macros"></a>Hodnota Null a nedefinovaná makra

Hodnota null a Nedefinovaná makra rozšířit na řetězce s hodnotou null, ale je makro definované jako řetězec s hodnotou null se považuje za definované v předběžném zpracování výrazů. Chcete-li definovat makro jako řetězec s hodnotou null, zadejte žádné znaky kromě mezery ani tabulátory za znaménkem rovnítka (=) v příkazovém řádku nebo souboru příkazů a řetězec s hodnotou null nebo definice uzavřít do dvojitých uvozovek (""). Chcete-li zrušit makra, použijte **! UNDEF.** Další informace najdete v tématu [direktivy předběžného zpracování souboru pravidel](../build/makefile-preprocessing-directives.md).

## <a name="see-also"></a>Viz také

[Definice makra NMAKE](../build/defining-an-nmake-macro.md)