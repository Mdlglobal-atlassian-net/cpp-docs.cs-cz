---
title: Přetížení &gt; &gt; operátor pro vaše vlastní třídy | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- operator>>
- operator>>, overloading for your own classes
- operator >>, overloading for your own classes
ms.assetid: 40dab4e0-3f97-4745-9cc8-b86e740fa246
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d98372009090b0241d9f0190a1d53a9416bbd7ba
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33853489"
---
# <a name="overloading-the-gtgt-operator-for-your-own-classes"></a>Přetížení &gt; &gt; operátor pro vaše vlastní třídy

Vstupní datové proudy použít extrahování (`>>`) operátor pro standardní typy. Můžete napsat podobné operátorů extrakce pro vlastní typy; váš úspěch závisí na přesněji pomocí prázdné znaky.

Tady je příklad operátor extrakce `Date` třídy uvedené výše:

```cpp
istream& operator>> (istream& is, Date& dt)
{
    is>> dt.mo>> dt.da>> dt.yr;
    return is;
}
```

## <a name="see-also"></a>Viz také

[Vstupní streamy](../standard-library/input-streams.md)<br/>
