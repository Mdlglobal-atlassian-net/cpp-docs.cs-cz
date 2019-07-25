---
title: '&lt; Přetížení&lt; operátoru pro vaše vlastní třídy'
ms.date: 11/04/2016
helpviewer_keywords:
- operator<<, overloading for your own classes
- operator <<, overloading for your own classes
ms.assetid: ad1d2c49-d84e-48a8-9c09-121f28b10bf0
ms.openlocfilehash: c470bb7335a5997ae26327f99b8c5f31d20b4edb
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68452057"
---
# <a name="overloading-the-ltlt-operator-for-your-own-classes"></a>&lt; Přetížení&lt; operátoru pro vaše vlastní třídy

Výstupní datové proudy používají operátor`<<`vložení () pro standardní typy. Můžete také přetížit `<<` operátor pro vlastní třídy.

## <a name="example"></a>Příklad

Příklad funkce ukázal použití `Date`struktury. `write` Datum je ideální kandidát pro C++ třídu, ve které jsou datové členy (měsíc, den a rok) ze zobrazení skryté. Výstupní datový proud je logickým cílem pro zobrazení takové struktury. Tento kód zobrazí datum pomocí `cout` objektu:

```cpp
Date dt(1, 2, 92);

cout <<dt;
```

Chcete- `cout` li `Date` přijmout objekt za operátorem vložení, přečtěte operátor `ostream` vložení pro rozpoznání objektu vlevo a `Date` na pravé straně. Funkce přetíženého `<<` operátoru musí být deklarována jako Friend třídy `Date` , aby mohla přistupovat k soukromým datům v rámci `Date` objektu.

```cpp
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

Přetížený operátor vrací odkaz na původní `ostream` objekt, což znamená, že můžete kombinovat vložení:

```cpp
cout <<"The date is" <<dt <<flush;
```

## <a name="see-also"></a>Viz také:

[Výstupní streamy](../standard-library/output-streams.md)
