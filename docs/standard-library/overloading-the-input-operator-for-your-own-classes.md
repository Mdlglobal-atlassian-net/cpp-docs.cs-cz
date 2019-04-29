---
title: Přetížení &gt; &gt; operátor pro vaše vlastní třídy
ms.date: 11/04/2016
helpviewer_keywords:
- operator>>
- operator>>, overloading for your own classes
- operator >>, overloading for your own classes
ms.assetid: 40dab4e0-3f97-4745-9cc8-b86e740fa246
ms.openlocfilehash: 86b8af963345c8eb9b3f44cfb16332bc09420bf3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62370720"
---
# <a name="overloading-the-gtgt-operator-for-your-own-classes"></a>Přetížení &gt; &gt; operátor pro vaše vlastní třídy

Vstupní datové proudy použít extrakce (`>>`) operátor pro standardní typy. Můžete napsat podobné operátorů extrakce pro vlastní typy; váš úspěch závisí na přesně pomocí prázdné znaky.

Tady je příklad operátoru extrakce pro `Date` třídy uvedené dříve:

```cpp
istream& operator>> (istream& is, Date& dt)
{
    is>> dt.mo>> dt.da>> dt.yr;
    return is;
}
```

## <a name="see-also"></a>Viz také:

[Vstupní streamy](../standard-library/input-streams.md)<br/>
