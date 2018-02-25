---
title: "Přetížení &gt; &gt; operátor pro vaše vlastní třídy | Microsoft Docs"
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
- operator>>
- operator>>, overloading for your own classes
- operator >>, overloading for your own classes
ms.assetid: 40dab4e0-3f97-4745-9cc8-b86e740fa246
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8fb029ee7e20a50ef00c2902bda0cca9fb48dbe2
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="overloading-the-gtgt-operator-for-your-own-classes"></a>Přetížení &gt; &gt; operátor pro vaše vlastní třídy
Vstupní datové proudy použít extrahování (`>>`) operátor pro standardní typy. Můžete napsat podobné operátorů extrakce pro vlastní typy; váš úspěch závisí na přesněji pomocí prázdné znaky.  
  
 Tady je příklad operátor extrakce `Date` třídy uvedené výše:  
  
```  
istream& operator>> (istream& is, Date& dt)  
{  
    is>> dt.mo>> dt.da>> dt.yr;  
    return is;  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Vstupní streamy](../standard-library/input-streams.md)

