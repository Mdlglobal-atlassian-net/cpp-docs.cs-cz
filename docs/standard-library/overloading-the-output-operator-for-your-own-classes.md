---
title: Přetížení &lt; &lt; operátor pro vaše vlastní třídy
ms.date: 11/04/2016
helpviewer_keywords:
- operator<<, overloading for your own classes
- operator <<, overloading for your own classes
ms.assetid: ad1d2c49-d84e-48a8-9c09-121f28b10bf0
ms.openlocfilehash: 290491f7afb22873d60abb6662b470d8e7abefc1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50486928"
---
# <a name="overloading-the-ltlt-operator-for-your-own-classes"></a>Přetížení &lt; &lt; operátor pro vaše vlastní třídy

Výstupní datové proudy použít vložení (`<<`) operátor pro standardní typy. Můžete také přetížit `<<` operátor pro vaše vlastní třídy.

## <a name="example"></a>Příklad

`write` Příklad funkce jsme si ukázali, použití `Date` struktury. Datum je ideální volbou pro třídu jazyka C++, ve kterém jsou skryté datové členy (měsíc, den a rok) ze zobrazení. Výstupní datový proud je logický cíl pro zobrazení této struktury. Tento kód zobrazí datum pomocí `cout` objektu:

```cpp
Date dt(1, 2, 92);

cout <<dt;
```

Chcete-li získat `cout` tak, aby přijímal `Date` objektu po vložení operátoru, přetížit operátor vkládání rozpoznat `ostream` objekt na levé straně a `Date` na pravé straně. Přetížené `<<` by pak funkci operátoru musí být deklarována jako přátelská třída `Date` tak měl přístup k soukromým datům v rámci `Date` objektu.

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

Přetíženého operátoru vrátí odkaz na původní `ostream` objekt, což znamená, že zkombinujete vložené položky:

```cpp
cout <<"The date is" <<dt <<flush;
```

## <a name="see-also"></a>Viz také:

[Výstupní streamy](../standard-library/output-streams.md)<br/>
