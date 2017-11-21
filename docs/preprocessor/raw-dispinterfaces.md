---
title: "raw_dispinterfaces – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: raw_dispinterfaces
dev_langs: C++
helpviewer_keywords: raw_dispinterfaces attribute
ms.assetid: f762864d-29bf-445b-825a-ba7b29a95409
caps.latest.revision: "4"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c73a30779bf85e39ca97d0e6f4979c070de4e00c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="rawdispinterfaces"></a>raw_dispinterfaces
**Konkrétní C++**  
  
 Určuje, kompilátor generovat funkce nízké úrovně obálku pro dispinterface metody a vlastnosti, které volají **volání metody IDispatch::Invoke** a vrátíte se `HRESULT` kód chyby.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
raw_dispinterfaces  
```  
  
## <a name="remarks"></a>Poznámky  
 Pokud není tento atribut zadaný, jenom nejdůležitější jsou generovány obálky, které vyvolávají výjimky jazyka C++ v případě selhání.  
  
 **Konkrétní END C++**  
  
## <a name="see-also"></a>Viz také  
 [#import – atributy](../preprocessor/hash-import-attributes-cpp.md)   
 [#import – direktiva](../preprocessor/hash-import-directive-cpp.md)