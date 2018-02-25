---
title: "Přetížení &lt; &lt; operátor pro vaše vlastní třídy | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- operator<<, overloading for your own classes
- operator <<, overloading for your own classes
ms.assetid: ad1d2c49-d84e-48a8-9c09-121f28b10bf0
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: eed1ff7819e93236e6baad192887494e6f956ac2
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="overloading-the-ltlt-operator-for-your-own-classes"></a>Přetížení &lt; &lt; operátor pro vaše vlastní třídy
Výstupní datové proudy použít vložení (`<<`) operátor pro standardní typy. Můžete také přetížení `<<` operátor pro vaše vlastní třídy.  
  
## <a name="example"></a>Příklad  
 `write` Funkce příklad ukázal použití `Date` struktury. Datum je ideální volbou pro třídu C++, ve kterém jsou v zobrazení skrytá datové členy (měsíc, den a rok). Výstupní proud je logické cíl pro zobrazení této struktury. Tento kód zobrazí datum pomocí `cout` objektu:  
  
```  
Date dt(1, 2, 92);

cout <<dt;  
```  
  
 Chcete-li získat `cout` tak, aby přijímal `Date` objektu po vložení operátor, operátor vložení rozpoznat přetížení `ostream` objekt na levé straně a `Date` na pravé straně. Přetížené `<<` operátor funkce musí být deklarován pak jako přítele třídy `Date` , má přístup k privátním dat v rámci `Date` objektu.  
  
```  
// overload_date.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
class Date  
{  
    int mo, da, yr;  
public:  
    Date(int m, int d, int y)  
    {  
        mo = m; da = d; yr = y;  
    }  
    friend ostream& operator<<(ostream& os, const Date& dt);  
};  
  
ostream& operator<<(ostream& os, const Date& dt)  
{  
    os << dt.mo << '/' << dt.da << '/' << dt.yr;  
    return os;  
}  
  
int main()  
{  
    Date dt(5, 6, 92);  
    cout << dt;  
}  
```  
  
```Output  
5/6/92  
```  
  
## <a name="remarks"></a>Poznámky  
 Přetížené operátor vrátí odkaz na původní `ostream` objekt, což znamená, můžete kombinovat vložení:  
  
```  
cout <<"The date is" <<dt <<flush;  
```  
  
## <a name="see-also"></a>Viz také  
 [Výstupní streamy](../standard-library/output-streams.md)

