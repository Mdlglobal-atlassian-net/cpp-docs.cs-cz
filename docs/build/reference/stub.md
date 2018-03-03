---
title: "SE ZAKÁZANÝM INZEROVÁNÍM | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- STUB
dev_langs:
- C++
helpviewer_keywords:
- STUB .def file statement
ms.assetid: 0a3b9643-19ed-47e9-8173-ee16bc8ed056
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 58430f8211f8859b65103b53d1f98a173c4635ee
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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