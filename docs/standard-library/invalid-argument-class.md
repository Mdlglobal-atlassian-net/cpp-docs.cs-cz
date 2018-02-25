---
title: "invalid_argument – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- stdexcept/std::invalid_argument
dev_langs:
- C++
helpviewer_keywords:
- invalid_argument class
ms.assetid: af6c227d-ad7c-4e63-9dee-67af81d83506
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cbd5762478ed5ddab2694469e93b1c3445026727
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="invalidargument-class"></a>invalid_argument – třída
Třída slouží jako základní třída pro všechny výjimky vydané nahlásit neplatný argument.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class invalid_argument : public logic_error {  
public:  
    explicit invalid_argument(const string& message);

    explicit invalid_argument(const char *message);

};  
```  
  
## <a name="remarks"></a>Poznámky  
 Hodnoty vrácené [co](../standard-library/exception-class.md) je kopie **zpráva**`.`[data](../standard-library/basic-string-class.md#data).  
  
## <a name="example"></a>Příklad  
  
```cpp  
// invalid_arg.cpp  
// compile with: /EHsc /GR  
#include <bitset>  
#include <iostream>  
  
using namespace std;  
  
int main( )  
{  
   try   
   {  
      bitset< 32 > bitset( string( "11001010101100001b100101010110000") );  
   }  
   catch ( exception &e )   
   {  
      cerr << "Caught " << e.what( ) << endl;  
      cerr << "Type " << typeid( e ).name( ) << endl;  
   };  
}  
\* Output:   
Caught invalid bitset<N> char  
Type class std::invalid_argument  
*\  
```  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<stdexcept – >  
  
 **Namespace:** – std  
  
## <a name="see-also"></a>Viz také  
 [logic_error – třída](../standard-library/logic-error-class.md)   
 [Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)

