---
title: Řešení nejednoznačných deklarací (C++)
ms.date: 11/04/2016
ms.assetid: 3d773ee7-bbea-47de-80c2-cb0a9d4ec0b9
ms.openlocfilehash: 52e94f474d59505298cb4f78a477cedd21b90aad
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62403396"
---
# <a name="resolving-ambiguous-declarations-c"></a>Řešení nejednoznačných deklarací (C++)

Chcete-li provést explicitní převody z jednoho typu na jiný, je zapotřebí použít přetypování a určit název požadovaného typu. Některá přetypování způsobují nejednoznačnost syntaxe. Následující přetypování podobné funkci je nejednoznačné:

```cpp
char *aName( String( s ) );
```

Je jasné, jestli jde o deklaraci funkce nebo objektu s přetypovat jako inicializátor function-style: Může jít o deklaraci funkce vracející typ `char *` , která přijímá jeden argument typu `String`, nebo může jít o deklaraci objektu `aName` a provést jeho inicializaci hodnotou `s` přetypování na typ `String`.

Může-li být deklarace považována za platnou deklaraci funkce, je jako deklarace funkce zpracována. Pouze v případě, že o deklaraci funkce jít nemůže – tedy pokud by byla syntaxe chybná – je příkaz zkoumán, zda jde o přetypování podobné funkci. Proto kompilátor považuje příkaz za deklaraci funkce a ignoruje závorky okolo identifikátoru `s`. Na druhou stranu, příkazy:

```cpp
char *aName( (String)s );
```

and

```cpp
char *aName = String( s );
```

jsou jednoznačnou deklarací objektů a uživatelsky definovaný převod z typu `String` na typ `char *` se vyvolá k inicializaci objektu `aName`.