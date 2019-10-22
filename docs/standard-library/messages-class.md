---
title: messages – třída
ms.date: 11/04/2016
f1_keywords:
- xlocmes/std::messages
- xlocmes/std::messages::char_type
- xlocmes/std::messages::string_type
- xlocmes/std::messages::close
- xlocmes/std::messages::do_close
- xlocmes/std::messages::do_get
- xlocmes/std::messages::do_open
- xlocmes/std::messages::get
- xlocmes/std::messages::open
helpviewer_keywords:
- std::messages [C++]
- std::messages [C++], char_type
- std::messages [C++], string_type
- std::messages [C++], close
- std::messages [C++], do_close
- std::messages [C++], do_get
- std::messages [C++], do_open
- std::messages [C++], get
- std::messages [C++], open
ms.assetid: c4c71f40-4f24-48ab-9f7c-daccd8d5bd83
ms.openlocfilehash: 704ee2ce40b4026cc066213181c96cf0f744d152
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2019
ms.locfileid: "72687689"
---
# <a name="messages-class"></a>messages – třída

Šablona třídy popisuje objekt, který může sloužit jako omezující vlastnost národního prostředí k načítání lokalizovaných zpráv z katalogu mezinárodních zpráv pro dané národní prostředí.

Je-li třída zpráv aktuálně implementována, nejsou k dispozici žádné zprávy.

## <a name="syntax"></a>Syntaxe

```cpp
template <class CharType>
class messages : public messages_base;
```

### <a name="parameters"></a>Parametry

*CharType* \
Typ používaný v rámci programu ke kódování znaků v národním prostředí.

## <a name="remarks"></a>Poznámky

Stejně jako u omezující vlastnosti národního prostředí má ID statického objektu počáteční uloženou hodnotu nula. První pokus o přístup k uložené hodnotě ukládá v ID jedinečnou kladnou hodnotu **.**

Tato omezující vlastnost v podstatě otevře katalog zpráv definovaný v základní třídě messages_base, načte požadované informace a katalog zavře.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[zprávy](#messages)|Funkce konstruktoru omezující vlastnosti zpráv.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[char_type](#char_type)|Typ znaku, který je používán pro zobrazení zpráv.|
|[string_type](#string_type)|Typ, který popisuje řetězec typu `basic_string` obsahující znaky typu `CharType`.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[close](#close)|Zavře katalog zpráv.|
|[do_close](#do_close)|Virtuální funkce volaná k zavření katalogu zpráv.|
|[do_get](#do_get)|Virtuální funkce volaná k načtení katalogu zpráv.|
|[do_open](#do_open)|Virtuální funkce volaná k otevření katalogu zpráv.|
|[get](#get)|Načte katalog zpráv.|
|[open](#open)|Otevře katalog zpráv.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<locale >

**Obor názvů:** std

## <a name="char_type"></a>zprávy:: char_type

Typ znaku, který je používán pro zobrazení zpráv.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr šablony **CharType**.

## <a name="close"></a>zprávy:: Close

Zavře katalog zpráv.

```cpp
void close(catalog _Catval) const;
```

### <a name="parameters"></a>Parametry

*_Catval* \
Katalog, který má být zavřen.

### <a name="remarks"></a>Poznámky

Členská funkce volá [do_close](#do_close)(_ *Catval*).

## <a name="do_close"></a>zprávy::d o_close

Virtuální funkce volaná k zavření katalogu zpráv.

```cpp
virtual void do_close(catalog _Catval) const;
```

### <a name="parameters"></a>Parametry

*_Catval* \
Katalog, který má být zavřen.

### <a name="remarks"></a>Poznámky

Chráněná členská funkce zavře katalog zpráv *_Catval*, který musí být otevřen starším voláním [do_open](#do_open).

*_Catval* se musí získat z dříve otevřeného katalogu, který není uzavřený.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [zavření](#close), který volá `do_close`.

## <a name="do_get"></a>zprávy::d o_get

Virtuální funkce volaná k načtení katalogu zpráv.

```cpp
virtual string_type do_get(
    catalog _Catval,
    int _Set,
    int _Message,
    const string_type& _Dfault) const;
```

### <a name="parameters"></a>Parametry

*_Catval* \
Identifikační hodnota určující katalog zpráv, který má být prohledán.

*_Nastavit* \
První identifikovaný, která se používá k vyhledání zprávy v katalogu zpráv.

*_Message* \
Druhá identifikovaná, která se používá k vyhledání zprávy v katalogu zpráv.

*_Dfault* \
Řetězec, který má být vrácen při selhání.

### <a name="return-value"></a>Návratová hodnota

Vrátí kopii *_Dfault* při selhání. V opačném případě vrátí kopii zadané posloupnosti zpráv.

### <a name="remarks"></a>Poznámky

Chráněná členská funkce se pokusí získat sekvenci zprávy z katalogu zpráv *_Catval*. V takovém případě může používat *_* , *_Message*a *_Dfault* .

### <a name="example"></a>Příklad

Podívejte se na příklad pro [Get](#get), který volá `do_get`.

## <a name="do_open"></a>zprávy::d o_open

Virtuální funkce volaná k otevření katalogu zpráv.

```cpp
virtual catalog do_open(
    const string& _Catname,
    const locale& _Loc) const;
```

### <a name="parameters"></a>Parametry

*_Catname* \
Název katalogu, který se má prohledat

*_Loc* \
Národní prostředí, které se v katalogu vyhledává.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu, která při selhání porovná méně než nulu. V opačném případě lze vrácenou hodnotu použít jako první argument pro pozdější volání metody [Get](#get).

### <a name="remarks"></a>Poznámky

Chráněná členská funkce se pokusí otevřít katalog zpráv, jehož název je *_Catname*. V takovém případě může použití národního prostředí *_Loc* .

Návratová hodnota by měla být použita jako argument na pozdějším volání [uzavření](#close).

### <a name="example"></a>Příklad

Podívejte se na příklad pro [Open](#open), který volá `do_open`.

## <a name="get"></a>zprávy:: Get

Načte katalog zpráv.

```cpp
string_type get(
    catalog _CatVal,
    int _Set,
    int _Message,
    const string_type& _Dfault) const;
```

### <a name="parameters"></a>Parametry

*_Catval* \
Identifikační hodnota určující katalog zpráv, který má být prohledán.

*_Nastavit* \
První identifikovaný, která se používá k vyhledání zprávy v katalogu zpráv.

*_Message* \
Druhá identifikovaná, která se používá k vyhledání zprávy v katalogu zpráv.

*_Dfault* \
Řetězec, který má být vrácen při selhání.

### <a name="return-value"></a>Návratová hodnota

Vrátí kopii *_Dfault* při selhání. V opačném případě vrátí kopii zadané posloupnosti zpráv.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí [do_get](#do_get)(`_Catval`, `_Set`, `_Message`, `_Dfault`).

## <a name="messages"></a>zprávy:: zprávy

Funkce konstruktoru omezující vlastnosti zpráv.

```cpp
explicit messages(
    size_t _Refs = 0);

protected: messages(
    const char* _Locname,
    size_t _Refs = 0);
```

### <a name="parameters"></a>Parametry

*_Refs* \
Celočíselná hodnota používaná k určení typu správy paměti pro daný objekt.

*_Locname* \
Název národního prostředí.

### <a name="remarks"></a>Poznámky

Možné hodnoty pro parametr *_Refs* a jejich význam jsou:

- 0: životnost objektu je spravována místními objekty, které jej obsahují.

- 1: životnost objektu musí být ručně spravovaná.

- \> 1: tyto hodnoty nejsou definovány.

Nejsou možné žádné přímé příklady, protože je destruktor chráněný.

Konstruktor inicializuje svůj základní objekt pomocí **locale::** [Face](../standard-library/locale-class.md#facet_class)(`_Refs`).

## <a name="open"></a>Messages:: Open

Otevře katalog zpráv.

```cpp
catalog open(
    const string& _Catname,
    const locale& _Loc) const;
```

### <a name="parameters"></a>Parametry

*_Catname* \
Název katalogu, který se má prohledat

*_Loc* \
Národní prostředí, které se v katalogu vyhledává.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu, která při selhání porovná méně než nulu. V opačném případě lze vrácenou hodnotu použít jako první argument pro pozdější volání metody [Get](#get).

### <a name="remarks"></a>Poznámky

Členská funkce vrátí [do_open](#do_open)(`_Catname`, `_Loc`).

## <a name="string_type"></a>zprávy:: string_type

Typ, který popisuje řetězec typu `basic_string` obsahující znaky typu `CharType`.

```cpp
typedef basic_string<CharType, Traits, Allocator> string_type;
```

### <a name="remarks"></a>Poznámky

Typ popisuje specializaci šablony třídy [basic_string](../standard-library/basic-string-class.md) , jejíž objekty mohou ukládat kopie sekvencí zpráv.

## <a name="see-also"></a>Viz také:

[\<locale >](../standard-library/locale.md) \
\ [třídy messages_base](../standard-library/messages-base-class.md)
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
