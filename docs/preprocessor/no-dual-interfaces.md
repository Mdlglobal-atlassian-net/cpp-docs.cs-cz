---
title: no_dual_interfaces – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- no_dual_interfaces
dev_langs:
- C++
helpviewer_keywords:
- no_dual_interfaces attribute
ms.assetid: 9acd5d9d-4a49-4cdc-9470-73a2c23cf512
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a8923adb4cf2e92d72bf656064c6de8fc66e2a91
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33850779"
---
# <a name="nodualinterfaces"></a>no_dual_interfaces
**Konkrétní C++**  
  
 Změny způsob kompilátor generuje funkce obálku pro metody duální rozhraní.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
no_dual_interfaces  
```  
  
## <a name="remarks"></a>Poznámky  
 Za normálních okolností obálku bude volat metodu prostřednictvím tabulky virtuální funkce pro rozhraní. S `no_dual_interfaces`, místo toho volá obálku **volání metody IDispatch::Invoke** k vyvolání metody.  
  
 **Konkrétní END C++**  
  
## <a name="see-also"></a>Viz také  
 [#import – atributy](../preprocessor/hash-import-attributes-cpp.md)   
 [#import – direktiva](../preprocessor/hash-import-directive-cpp.md)