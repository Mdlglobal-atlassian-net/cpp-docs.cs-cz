---
title: "#Chyba – direktiva (C/C++) | Microsoft Docs"
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
ms.workload: cplusplus
ms.openlocfilehash: a14786834843046fc1e6cf551eaf95d1b28a8624
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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