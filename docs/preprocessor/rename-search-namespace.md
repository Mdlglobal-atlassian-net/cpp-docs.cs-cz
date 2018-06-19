---
title: rename_search_namespace – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- rename_search_namespace
dev_langs:
- C++
helpviewer_keywords:
- rename_search_namespace attribute
ms.assetid: 47c9d7fd-59dc-4c62-87a1-9011a0040167
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 367294991b9cbb07ee7c852d757842a20c51cc30
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33850252"
---
# <a name="renamesearchnamespace"></a>rename_search_namespace
**Konkrétní C++**  
  
 Má stejné funkce jako [rename_namespace –](../preprocessor/rename-namespace.md) atribut ale se používá na knihovny typů, které používají #import – direktiva s [auto_search –](../preprocessor/auto-search.md) atribut.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
rename_search_namespace("NewName")  
```  
  
#### <a name="parameters"></a>Parametry  
 `NewName`  
 Nový název oboru názvů.  
  
## <a name="remarks"></a>Poznámky  
 **Konkrétní END C++**  
  
## <a name="see-also"></a>Viz také  
 [#import – atributy](../preprocessor/hash-import-attributes-cpp.md)   
 [#import – direktiva](../preprocessor/hash-import-directive-cpp.md)