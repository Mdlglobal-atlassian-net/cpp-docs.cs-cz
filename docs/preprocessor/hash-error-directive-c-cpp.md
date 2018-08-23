---
title: '#Chyba – direktiva (C++) | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- '#error'
dev_langs:
- C++
helpviewer_keywords:
- '#error directive'
- preprocessor, directives
- error directive (#error directive)
ms.assetid: d550a802-ff19-4347-9597-688935d23b2b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d2da939fe52e41e122ecd4926e34fb9c4be735ae
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/10/2018
ms.locfileid: "42465091"
---
# <a name="error-directive-cc"></a>#error – direktiva (C++)
**#Error** – direktiva generuje zadané uživatelem chybovou zprávu v době kompilace a ukončí kompilace.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#errortoken-string  
```  
  
## <a name="remarks"></a>Poznámky  
 
Obsahuje chybovou zprávu, která tato direktiva generuje *řetězci tokenu* parametru. *Řetězci tokenu* parametr není řídí podle rozšíření makra. Tato direktiva je nejužitečnější při předběžném zpracování oznamujících developer program nekonzistence nebo porušení omezení. Následující příklad ukazuje Chyba při zpracování během předběžného zpracování:  
  
```  
#if !defined(__cplusplus)  
#error C++ compiler required.  
#endif  
```  
  
## <a name="see-also"></a>Viz také  
 
[Preprocesor – direktivy](../preprocessor/preprocessor-directives.md)