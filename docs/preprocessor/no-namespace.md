---
title: no_namespace | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- no_namespace
dev_langs:
- C++
helpviewer_keywords:
- no_namespace attribute
ms.assetid: 5d81b741-a558-451b-b493-1f3b18967337
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a02919e1e96717c1accc6343ecff32a66968cbcc
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46378813"
---
# <a name="nonamespace"></a>no_namespace
**Specifické pro C++**  
  
Určuje, že název oboru názvů není generovaný kompilátorem.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
no_namespace  
```  
  
## <a name="remarks"></a>Poznámky  
 
Obsah knihovny typů v `#import` soubor hlaviček jsou obvykle definovány v oboru názvů. Byl zadán název oboru názvů `library` příkaz v původním souboru IDL. Pokud **no_namespace** zadán atribut, pak tento obor názvů není generovaný kompilátorem.  
  
Pokud chcete použít jiný obor názvů, použijte [rename_namespace](../preprocessor/rename-namespace.md) místo atributu.  
  
**Specifické pro END C++**  
  
## <a name="see-also"></a>Viz také  
 
[atributů #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import – direktiva](../preprocessor/hash-import-directive-cpp.md)