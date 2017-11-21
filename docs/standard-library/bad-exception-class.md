---
title: "Třída bad_exception | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: exception/std::bad_exception
dev_langs: C++
helpviewer_keywords: bad_exception class
ms.assetid: 5ae2c4ef-c7ad-4469-8a9e-a773e86bb000
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c3a322ce0ed9621e1413009092b0afb9572196a9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="badexception-class"></a>Třída bad_exception
Třída popisuje výjimku, která může být vyvolána z neočekávané obslužné rutiny.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class bad_exception    : public exception {};  
```  
  
## <a name="remarks"></a>Poznámky  
 [neočekávané](../standard-library/exception-functions.md#unexpected) vyvolá výjimku `bad_exception` místo ukončení nebo namísto volání jinou funkci zadaným [set_unexpected –](../standard-library/exception-functions.md#set_unexpected) Pokud `bad_exception` je uveden v seznamu throw funkce.  
  
 Hodnoty vrácené **co** je řetězec definované implementací C. Žádná z členské funkce throw jakékoli výjimky.  
  
 Pro seznam členů zdědí `bad_exception` třídy najdete v tématu [třída exception](../standard-library/exception-class.md).  
  
## <a name="example"></a>Příklad  
 V tématu [set_unexpected –](../standard-library/exception-functions.md#set_unexpected) příklad použití [neočekávané](../standard-library/exception-functions.md#unexpected) vyvolání `bad_exception`.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<výjimka >  
  
 **Namespace:** – std  
  
## <a name="see-also"></a>Viz také  
[Třída Exception](../standard-library/exception-class.md) [bezpečný přístup z více vláken ve standardní knihovna C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)

