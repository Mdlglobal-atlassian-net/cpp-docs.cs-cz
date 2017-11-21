---
title: "#<a name=\"error-directive-cc--microsoft-docs\"></a>Chyba – direktiva (C/C++) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: '#error'
dev_langs: C++
helpviewer_keywords:
- '#error directive'
- preprocessor, directives
- error directive (#error directive)
ms.assetid: d550a802-ff19-4347-9597-688935d23b2b
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 5bb05612ed7262b9daf287793c93ccce654306d6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="error-directive-cc"></a>#error – direktiva (C++)
`#error` – Direktiva vysílá uživatelem zadanou chybovou zprávu v době kompilace a ukončí kompilace.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#errortoken-string  
```  
  
## <a name="remarks"></a>Poznámky  
 Chybová zpráva, která tato direktiva vysílá zahrnují *token řetězec* parametr. `token-string` Parametr není předmětem makro rozšíření. Tato direktiva je velmi užitečné při předběžném zpracování pro upozornění na vývojáře nekonzistence program nebo porušení omezení. Následující příklad ukazuje Chyba při zpracování při předběžném zpracování:  
  
```  
#if !defined(__cplusplus)  
#error C++ compiler required.  
#endif  
```  
  
## <a name="see-also"></a>Viz také  
 [Preprocesor – direktivy](../preprocessor/preprocessor-directives.md)