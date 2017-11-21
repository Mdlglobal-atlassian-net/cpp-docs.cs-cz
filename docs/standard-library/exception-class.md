---
title: "Třída Exception | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: exception
dev_langs: C++
helpviewer_keywords: exception class
ms.assetid: 4f181f67-5888-4b50-89a6-745091ffb2fe
caps.latest.revision: "19"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ba3900e88cd4e307eb89bc386ec6b6005d2a6e24
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="exception-class"></a>Třída exception
Třída slouží jako základní třída pro všechny výjimky vydané určité výrazy a standardní knihovny C++.  
  
## <a name="syntax"></a>Syntaxe  
```  
class exception {
   public:
   exception();
   exception(const char* const &message);
   exception(const char* const &message, int);
   exception(const exception &right);
   exception& operator=(const exception &right);
   virtual ~exception();
   virtual const char *what() const;
   };  
``` 
## <a name="remarks"></a>Poznámky  
 Konkrétně tato základní třída je kořenem standardní výjimka tříd definovaných v [ \<stdexcept – >](../standard-library/stdexcept.md). C řetězce hodnoty vrácené `what` vlevo je neurčené výchozí konstruktor, ale může být konstruktory pro určité odvozené třídy definována jako řetězec definované implementací C. Žádná z členské funkce throw jakékoli výjimky.  
  
 `int` Parametr umožňuje určit, že by měla být přidělená není dostatek paměti. Hodnota `int` je ignorována.  
  
> [!NOTE]
>  Konstruktory `exception(const char* const &message)` a `exception(const char* const &message, int)` jsou rozšíření Microsoft pro standardní knihovna C++.  
  
## <a name="example"></a>Příklad  
 Příklady použití třídy standardní výjimek, které dědí od `exception` naleznete v některé z tříd definovaných v [ \<stdexcept – >](../standard-library/stdexcept.md).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<výjimka >  
  
 **Namespace:** – std  
  
## <a name="see-also"></a>Viz také  
 [Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)



