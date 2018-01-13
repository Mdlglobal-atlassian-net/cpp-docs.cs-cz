---
title: "Hodnota Null a Nedefinovaná makra | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- NMAKE program, undefined macros
- Null macros in NMAKE
- macros, null and undefined
- undefined macros and NMAKE
- NMAKE program, null macros
ms.assetid: 1db4611a-1755-4328-b00f-d35365af8b6c
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9581b152057655c510f1cbcd4ab29ba8339070b8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="null-and-undefined-macros"></a>Hodnota Null a nedefinovaná makra
Hodnota null a Nedefinovaná makra rozšířit do řetězce null, ale makra definován jako řetězec null se považuje za definované v předběžném zpracování výrazy. Makra, definovat jako řetězec hodnotu null, zadejte žádné znaky s výjimkou mezery nebo karty Po znaménku rovná se (=), v příkazovém řádku nebo příkazového řádku a řetězec null nebo definice uzavřít do uvozovek (""). Chcete-li nedefinované makra, použijte **! UNDEF.** Další informace najdete v tématu [předběžné zpracování direktiv souboru pravidel](../build/makefile-preprocessing-directives.md).  
  
## <a name="see-also"></a>Viz také  
 [Definice makra NMAKE](../build/defining-an-nmake-macro.md)