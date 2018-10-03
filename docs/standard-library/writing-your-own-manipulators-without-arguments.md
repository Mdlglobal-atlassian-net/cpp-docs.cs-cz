---
title: Psaní vlastních manipulátorů bez argumentů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- manipulators
ms.assetid: 2dc62d09-45b7-454d-bd9d-55f3c72c206d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e8bfad1919863a58554604fe6d32b4563e57a14a
ms.sourcegitcommit: 1d9bd38cacbc783fccd3884b7b92062161c91c84
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2018
ms.locfileid: "48235708"
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
