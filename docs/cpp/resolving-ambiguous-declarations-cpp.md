---
title: Řešení nejednoznačných deklarací (C++)
ms.date: 11/04/2016
ms.assetid: 3d773ee7-bbea-47de-80c2-cb0a9d4ec0b9
ms.openlocfilehash: 52e94f474d59505298cb4f78a477cedd21b90aad
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50507364"
---
# <a name="resolving-ambiguous-declarations-c"></a>Řešení nejednoznačných deklarací (C++)

Chcete-li provést explicitní převody z jednoho typu na jiný, je zapotřebí použít přetypování a určit název požadovaného typu. Některá přetypování způsobují nejednoznačnost syntaxe. Následující přetypování podobné funkci je nejednoznačné:

```cpp
char *aName( String( s ) );
```

Není jasné, zda se jedná o deklaraci funkce nebo objektu s přetypovat jako inicializátor function-style: může jít o deklaraci funkce vracející typ `char *` , která přijímá jeden argument typu `String`, nebo může jít o deklaraci objektu `aName` a provést jeho inicializaci hodnotou `s` přetypování na typ `String`.

Může-li být deklarace považována za platnou deklaraci funkce, je jako deklarace funkce zpracována. Pouze v případě, že o deklaraci funkce jít nemůže – tedy pokud by byla syntaxe chybná – je příkaz zkoumán, zda jde o přetypování podobné funkci. Proto kompilátor považuje příkaz za deklaraci funkce a ignoruje závorky okolo identifikátoru `s`. Na druhou stranu, příkazy:

```cpp
char *aName( (String)s );
```

and

```cpp
char *aName = String( s );
```

jsou jednoznačnou deklarací objektů a uživatelsky definovaný převod z typu `String` na typ `char *` se vyvolá k inicializaci objektu `aName`.