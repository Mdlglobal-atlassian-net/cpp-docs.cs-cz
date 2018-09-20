---
title: rename_namespace | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- rename_namespace
dev_langs:
- C++
helpviewer_keywords:
- rename_namespace attribute
ms.assetid: 45006d2b-36cd-4bec-98b9-3b8ec45299e3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7608255b5369443ce1045f896b776cb283fdb1cb
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46411856"
---
# <a name="renamenamespace"></a>rename_namespace
**Specifické pro C++**  
  
Přejmenuje obor názvů, který obsahuje obsah knihovny typů.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
rename_namespace("NewName")  
```  
  
### <a name="parameters"></a>Parametry  
*NewName*  
Nový název oboru názvů.  
  
## <a name="remarks"></a>Poznámky  
 
Přijímá jeden argument, *NewName*, která určuje nový název pro obor názvů.  
  
Chcete-li odebrat obor názvů, použijte [no_namespace](../preprocessor/no-namespace.md) místo atributu.  
  
**Specifické pro END C++**  
  
## <a name="see-also"></a>Viz také  
 
[atributů #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import – direktiva](../preprocessor/hash-import-directive-cpp.md)