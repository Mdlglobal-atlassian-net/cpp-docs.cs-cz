---
title: "SE ZAKÁZANÝM INZEROVÁNÍM | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: STUB
dev_langs: C++
helpviewer_keywords: STUB .def file statement
ms.assetid: 0a3b9643-19ed-47e9-8173-ee16bc8ed056
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 27d7ee77d527e8d8715d182609f1cb847b10a3d4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="stub"></a>Zástupný procedura
Při použití v souboru definice modulu, který sestaví ovladač virtuálního zařízení (VxD), můžete zadat název souboru, který obsahuje strukturu IMAGE_DOS_HEADER (definovanou v WINNT. H) pro použití v ovladač virtuálního zařízení (VxD), místo výchozí záhlaví.  
  
```  
STUB:filename  
```  
  
## <a name="remarks"></a>Poznámky  
 Ekvivalentní způsob, jak určit *filename* je pomocí [/STUB](../../build/reference/stub-ms-dos-stub-file-name.md) – možnost linkeru.  
  
 Se zakázaným INZEROVÁNÍM je v souboru definice modulu platná, pouze při vytváření VxD –.  
  
## <a name="see-also"></a>Viz také  
 [Pravidla pro příkazy definice modulu](../../build/reference/rules-for-module-definition-statements.md)