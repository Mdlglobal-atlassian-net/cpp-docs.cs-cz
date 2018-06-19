---
title: SE ZAKÁZANÝM INZEROVÁNÍM | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- STUB
dev_langs:
- C++
helpviewer_keywords:
- STUB .def file statement
ms.assetid: 0a3b9643-19ed-47e9-8173-ee16bc8ed056
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 385e073f877a938a3b73fa79036d27cf50c1e4ec
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32375198"
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