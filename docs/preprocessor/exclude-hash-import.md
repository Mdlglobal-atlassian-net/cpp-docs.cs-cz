---
title: vyloučit (#import) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- exclude
dev_langs:
- C++
helpviewer_keywords:
- exclude attribute
ms.assetid: 0883248a-d4bf-420e-9848-807b28fa976e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e5798c7515c411b9abf9d10229a6185e01bb92f7
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46400195"
---
# <a name="exclude-import"></a>exclude (#import)
**Specifické pro C++**  
  
Vyloučí položky z generovaných souborů hlaviček knihoven typů.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
exclude("Name1"[, "Name2",...])  
```  
  
### <a name="parameters"></a>Parametry  
*Name1*  
První položka, která má být vyloučena.  
  
*Name2*  
Druhá položka, která má být vyloučena (je-li zapotřebí).  
  
## <a name="remarks"></a>Poznámky  
 
Knihovny typů mohou obsahovat definice položek definovaných v systémových hlavičkách nebo jiných knihovnách typů. Tento atribut může přijmout libovolný počet argumentů, přičemž každý z nich je položkou knihovny typů nejvyšší úrovně, která má být vyloučena.  
  
**Specifické pro END C++**  
  
## <a name="see-also"></a>Viz také  
 
[atributů #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import – direktiva](../preprocessor/hash-import-directive-cpp.md)