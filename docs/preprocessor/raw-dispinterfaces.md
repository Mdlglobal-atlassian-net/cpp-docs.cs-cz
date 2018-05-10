---
title: raw_dispinterfaces – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- raw_dispinterfaces
dev_langs:
- C++
helpviewer_keywords:
- raw_dispinterfaces attribute
ms.assetid: f762864d-29bf-445b-825a-ba7b29a95409
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1f2a0d91d0f0dd3d23886ade75072526e6c895f7
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
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