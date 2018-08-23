---
title: raw_dispinterfaces – | Dokumentace Microsoftu
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
ms.openlocfilehash: 093c994de24b947c53bfc19d33213e77f3ec2593
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/10/2018
ms.locfileid: "42466381"
---
# <a name="rawdispinterfaces"></a>raw_dispinterfaces
**Specifické pro C++**  
  
Instruuje kompilátor, aby generovat funkce nízké úrovně obálky pro dispinterface metody a vlastnosti, které volají `IDispatch::Invoke` a vrátí kód chyby: HRESULT.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
raw_dispinterfaces  
```  
  
## <a name="remarks"></a>Poznámky  
 
Pokud tento atribut není zadaný, pouze vysoké úrovně jsou generovány obálky, které vyvolají výjimky C++ v případě selhání.  
  
**Specifické pro END C++**  
  
## <a name="see-also"></a>Viz také  
 
[atributů #import](../preprocessor/hash-import-attributes-cpp.md)   
[#import – direktiva](../preprocessor/hash-import-directive-cpp.md)