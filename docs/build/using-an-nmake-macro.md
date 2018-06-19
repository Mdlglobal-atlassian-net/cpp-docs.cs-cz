---
title: Použití makra NMAKE | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- macros, NMAKE
- NMAKE macros, using
ms.assetid: 95c87fbc-76e6-48c0-8536-9bfe179f328e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c6bf098a3723aa7b067b8192bf503975998e4e98
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32380573"
---
# <a name="using-an-nmake-macro"></a>Použití makra NMAKE
Pomocí makra, uzavřete jeho název v závorkách sebou znak dolaru ($) následujícím způsobem.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
$(macroname)  
```  
  
## <a name="remarks"></a>Poznámky  
 Žádné mezery. Závorky jsou volitelné Pokud *makro* je jeden znak. Řetězec definice nahrazuje $(*makro*); Nedefinovaná makra je nahrazena řetězec null.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o?  
 [Nahrazení makra](../build/macro-substitution.md)  
  
## <a name="see-also"></a>Viz také  
 [Makra a příkaz NMAKE](../build/macros-and-nmake.md)