---
title: Psaní vlastních manipulátorů bez argumentů
ms.date: 11/04/2016
helpviewer_keywords:
- manipulators
ms.assetid: 2dc62d09-45b7-454d-bd9d-55f3c72c206d
ms.openlocfilehash: 9a1f72ae3e6860d8ab532a72a1776b77c7204f48
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68450908"
---
# <a name="writing-your-own-manipulators-without-arguments"></a>Psaní vlastních manipulátorů bez argumentů

Zápisy s použitím argumentů, které nepoužívají argumenty, nevyžadují odvození třídy ani použití složitých maker. Předpokládejme, že tiskárna vyžaduje dvojici \<Esc > [k zadání tučného režimu. Tuto dvojici můžete vložit přímo do datového proudu:

```cpp
cout << "regular " << '\033' << '[' << "boldface" << endl;
```

Případně můžete definovat `bold` manipulátor, který vloží tyto znaky:

```cpp
ostream& bold(ostream& os) {
    return os << '\033' << '[';
}
cout << "regular " << bold << "boldface" << endl;
```

Globálně definovaná `bold` funkce `ostream` přijímá `ostream` odkazový argument a vrací odkaz. Nejedná se o členskou funkci ani o přítele, protože nepotřebuje přístup k žádným soukromým prvkům třídy. Funkce se připojuje ke streamu, protože `<<` operátor datového proudu je přetížený, aby přijal tento typ funkce, a to pomocí deklarace, která vypadá nějak takto: `bold`

```cpp
_Myt& operator<<(ios_base& (__cdecl *_Pfn)(ios_base&))
{
    // call ios_base manipulator
    (*_Pfn)(*(ios_base *)this);

    return (*this);
}
```

Tuto funkci můžete použít k rozšiřování dalších přetížených operátorů. V tomto případě je to náhodná, `bold` která do datového proudu vloží znaky. Funkce je volána, když je vložena do datového proudu, nikoli nutně při vytištění sousedících znaků. Proto může být tisk zpožděn z důvodu ukládání do vyrovnávací paměti datového proudu.

## <a name="see-also"></a>Viz také:

[Výstupní streamy](../standard-library/output-streams.md)
