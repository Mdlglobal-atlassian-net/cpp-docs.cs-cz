---
title: Psaní vlastních manipulátorů bez argumentů
ms.date: 11/04/2016
helpviewer_keywords:
- manipulators
ms.assetid: 2dc62d09-45b7-454d-bd9d-55f3c72c206d
ms.openlocfilehash: 0c3037c007e9388485f9553f9d2b0a69a1980b9a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62410821"
---
# <a name="writing-your-own-manipulators-without-arguments"></a>Psaní vlastních manipulátorů bez argumentů

Zápis manipulátory, které nepoužívají argumenty vyžaduje odvození třídy ani používají složité makra. Předpokládejme, že tiskárna vyžaduje dvojici \<ESC > [do tučné režimu. Tento pár můžete vložit přímo do datového proudu:

```cpp
cout << "regular " << '\033' << '[' << "boldface" << endl;
```

Nebo můžete definovat `bold` manipulátor, která vloží znaky:

```cpp
ostream& bold(ostream& os) {
    return os << '\033' << '[';
}
cout << "regular " << bold << "boldface" << endl;
```

Globálně definované `bold` funkce přebírá `ostream` odkazovat na argument a vrátí `ostream` odkaz. Není členská funkce nebo přátelská protože nepotřebuje přístup k prvkům žádné soukromé třídy. `bold` Funkce připojí k datového proudu, protože datový proud `<<` je operátor přetížen tak, aby přijímal tento druh funkce, pomocí deklarace, která vypadá přibližně takto:

```cpp
_Myt& operator<<(ios_base& (__cdecl *_Pfn)(ios_base&))
{
    // call ios_base manipulator
    (*_Pfn)(*(ios_base *)this);

    return (*this);
}
```

Tuto funkci můžete použít k rozšíření jiné přetížené operátory. V takovém případě je náhodné, který `bold` vloží znaků do datového proudu. Funkce je volána, když je vložen do datového proudu, ne tedy nutně vytištěné sousedících znaků. Díky tomu se může zpozdit tisk z důvodu ukládání do vyrovnávací paměti datového proudu.

## <a name="see-also"></a>Viz také:

[Výstupní streamy](../standard-library/output-streams.md)<br/>
