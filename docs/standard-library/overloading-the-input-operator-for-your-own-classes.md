---
title: '&gt; Přetížení&gt; operátoru pro vaše vlastní třídy'
ms.date: 11/04/2016
helpviewer_keywords:
- operator>>
- operator>>, overloading for your own classes
- operator >>, overloading for your own classes
ms.assetid: 40dab4e0-3f97-4745-9cc8-b86e740fa246
ms.openlocfilehash: 672dfb7ec40b2f18cbde0adc92522d3194a5e738
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68450126"
---
# <a name="overloading-the-gtgt-operator-for-your-own-classes"></a>&gt; Přetížení&gt; operátoru pro vaše vlastní třídy

Vstupní datové proudy používají operátor`>>`extrakce () pro standardní typy. Můžete psát podobné operátory extrakce pro vlastní typy; úspěch bude záviset na používání prázdného místa přesně.

Zde je příklad operátoru extrakce pro třídu, `Date` která je uvedena dříve:

```cpp
istream& operator>> (istream& is, Date& dt)
{
    is>> dt.mo>> dt.da>> dt.yr;
    return is;
}
```

## <a name="see-also"></a>Viz také:

[Vstupní streamy](../standard-library/input-streams.md)
