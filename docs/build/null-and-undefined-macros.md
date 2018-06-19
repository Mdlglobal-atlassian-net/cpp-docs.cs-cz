---
title: Hodnota Null a Nedefinovaná makra | Microsoft Docs
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
ms.openlocfilehash: 494a084ee5ba1da29c132aa632b647b37f305855
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32368467"
---
# <a name="null-and-undefined-macros"></a>Hodnota Null a nedefinovaná makra
Hodnota null a Nedefinovaná makra rozšířit do řetězce null, ale makra definován jako řetězec null se považuje za definované v předběžném zpracování výrazy. Makra, definovat jako řetězec hodnotu null, zadejte žádné znaky s výjimkou mezery nebo karty Po znaménku rovná se (=), v příkazovém řádku nebo příkazového řádku a řetězec null nebo definice uzavřít do uvozovek (""). Chcete-li nedefinované makra, použijte **! UNDEF.** Další informace najdete v tématu [předběžné zpracování direktiv souboru pravidel](../build/makefile-preprocessing-directives.md).  
  
## <a name="see-also"></a>Viz také  
 [Definice makra NMAKE](../build/defining-an-nmake-macro.md)