---
title: no_namespace – | Microsoft Docs
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
ms.openlocfilehash: b3d4558b0fd6a4014bc9601d5260882af444f87e
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33912742"
---
# <a name="nonamespace"></a>no_namespace
**Konkrétní C++**  
  
 Určuje, že název oboru názvů není generované kompilátorem.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
no_namespace  
```  
  
## <a name="remarks"></a>Poznámky  
 Knihovny typů obsah v `#import` soubor hlaviček jsou obvykle definovány v oboru názvů. Název oboru názvů je zadán v **knihovny** prohlášení o původní soubor IDL. Pokud `no_namespace` zadaný atribut, bude tento obor názvů není generované kompilátorem.  
  
 Pokud chcete použít jiný obor názvů název, použijte [rename_namespace –](../preprocessor/rename-namespace.md) atribut místo.  
  
 **Konkrétní END C++**  
  
## <a name="see-also"></a>Viz také  
 [#import – atributy](../preprocessor/hash-import-attributes-cpp.md)   
 [#import – direktiva](../preprocessor/hash-import-directive-cpp.md)