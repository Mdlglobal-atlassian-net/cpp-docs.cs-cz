---
title: "no_dual_interfaces – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: no_dual_interfaces
dev_langs: C++
helpviewer_keywords: no_dual_interfaces attribute
ms.assetid: 9acd5d9d-4a49-4cdc-9470-73a2c23cf512
caps.latest.revision: "4"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 42501c329b5c040f762b692e9298b184a2035d7d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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