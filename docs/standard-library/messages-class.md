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
ms.openlocfilehash: deb9eaedba3c99bb2fcb8399ac412ccedb11545f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375914"
---
# <a name="messages-class"></a>messages – třída

Šablona třídy popisuje objekt, který může sloužit jako omezující vlastnost národního prostředí pro načtení lokalizovaných zpráv z katalogu internacionalizovaných zpráv pro dané národní prostředí.

Je-li třída zpráv aktuálně implementována, nejsou k dispozici žádné zprávy.

## <a name="syntax"></a>Syntaxe

```cpp
template <class CharType>
class messages : public messages_base;
```

### <a name="parameters"></a>Parametry

*Typ znaku*\
Typ používaný v rámci programu ke kódování znaků v národním prostředí.

## <a name="remarks"></a>Poznámky

Stejně jako u omezující vlastnosti národního prostředí má ID statického objektu počáteční uloženou hodnotu nula. První pokus o přístup k jeho uložená hodnota ukládá jedinečnou kladnou hodnotu v **id.**

Tato omezující vlastnost v podstatě otevře katalog zpráv definovaný v základní třídě messages_base, načte požadované informace a katalog zavře.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[Zprávy](#messages)|Funkce konstruktoru omezující vlastnosti zpráv.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[char_type](#char_type)|Typ znaku, který je používán pro zobrazení zpráv.|
|[string_type](#string_type)|Typ, který popisuje řetězec `basic_string` typu obsahující znaky `CharType`typu .|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[Zavřete](#close)|Zavře katalog zpráv.|
|[do_close](#do_close)|Virtuální funkce volaná k zavření katalogu zpráv.|
|[do_get](#do_get)|Virtuální funkce volaná k načtení katalogu zpráv.|
|[do_open](#do_open)|Virtuální funkce volaná k otevření katalogu zpráv.|
|[get](#get)|Načte katalog zpráv.|
|[Otevřít](#open)|Otevře katalog zpráv.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<> národního prostředí

**Obor názvů:** std

## <a name="messageschar_type"></a><a name="char_type"></a>zprávy::char_type

Typ znaku, který je používán pro zobrazení zpráv.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymem pro parametr šablony **CharType**.

## <a name="messagesclose"></a><a name="close"></a>zprávy::zavřít

Zavře katalog zpráv.

```cpp
void close(catalog _Catval) const;
```

### <a name="parameters"></a>Parametry

*_Catval*\
Katalog, který má být uzavřen.

### <a name="remarks"></a>Poznámky

Členská funkce volá [do_close](#do_close)(_ *Catval*).

## <a name="messagesdo_close"></a><a name="do_close"></a>zprávy::do_close

Virtuální funkce volaná k zavření katalogu zpráv.

```cpp
virtual void do_close(catalog _Catval) const;
```

### <a name="parameters"></a>Parametry

*_Catval*\
Katalog, který má být uzavřen.

### <a name="remarks"></a>Poznámky

Chráněná členská funkce zavře katalog zpráv *_Catval*, který musí být otevřen dřívějším voláním [do_open](#do_open).

*_Catval* musí být získány z dříve otevřeného katalogu, který není uzavřen.

### <a name="example"></a>Příklad

Viz příklad pro [close](#close) `do_close`, který volá .

## <a name="messagesdo_get"></a><a name="do_get"></a>zprávy::do_get

Virtuální funkce volaná k načtení katalogu zpráv.

```cpp
virtual string_type do_get(
    catalog _Catval,
    int _Set,
    int _Message,
    const string_type& _Dfault) const;
```

### <a name="parameters"></a>Parametry

*_Catval*\
Identifikační hodnota určující katalog zpráv, který má být prohledán.

*_nastavit*\
První identifikovaný slouží k vyhledání zprávy v katalogu zpráv.

*_Message*\
Druhý identifikován slouží k vyhledání zprávy v katalogu zpráv.

*_Dfault*\
Řetězec, který má být vrácen při selhání.

### <a name="return-value"></a>Návratová hodnota

Vrátí kopii *_Dfault* při selhání. V opačném případě vrátí kopii zadané sekvence zpráv.

### <a name="remarks"></a>Poznámky

Chráněná členská funkce se pokusí získat posloupnost zpráv z katalogu zpráv *_Catval*. Může k tomu využít *_Set*, *_Message*a *_Dfault.*

### <a name="example"></a>Příklad

Viz příklad pro [get](#get) `do_get`, který volá .

## <a name="messagesdo_open"></a><a name="do_open"></a>zprávy::do_open

Virtuální funkce volaná k otevření katalogu zpráv.

```cpp
virtual catalog do_open(
    const string& _Catname,
    const locale& _Loc) const;
```

### <a name="parameters"></a>Parametry

*_Catname*\
Název katalogu, který má být prohledán.

*_Loc*\
Národní prostředí vyhledávané v katalogu.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu, která porovnává méně než nula na selhání. V opačném případě vrácená hodnota může být použit jako první argument na pozdější volání [získat](#get).

### <a name="remarks"></a>Poznámky

Chráněná členská funkce se pokusí otevřít katalog zpráv, jehož název je *_Catname*. Může k tomu využít *národní hod_Loc*

Vrácená hodnota by měla být použita jako argument pro pozdější volání k [uzavření](#close).

### <a name="example"></a>Příklad

Viz příklad pro [otevření](#open) `do_open`, který volá .

## <a name="messagesget"></a><a name="get"></a>zprávy::získat

Načte katalog zpráv.

```cpp
string_type get(
    catalog _CatVal,
    int _Set,
    int _Message,
    const string_type& _Dfault) const;
```

### <a name="parameters"></a>Parametry

*_Catval*\
Identifikační hodnota určující katalog zpráv, který má být prohledán.

*_nastavit*\
První identifikovaný slouží k vyhledání zprávy v katalogu zpráv.

*_Message*\
Druhý identifikován slouží k vyhledání zprávy v katalogu zpráv.

*_Dfault*\
Řetězec, který má být vrácen při selhání.

### <a name="return-value"></a>Návratová hodnota

Vrátí kopii *_Dfault* při selhání. V opačném případě vrátí kopii zadané sekvence zpráv.

### <a name="remarks"></a>Poznámky

Členská funkce [do_get](#do_get)vrátí `_Catval` `_Set`do_get `_Message` `_Dfault`( , , ).

## <a name="messagesmessages"></a><a name="messages"></a>zprávy::zprávy

Funkce konstruktoru omezující vlastnosti zpráv.

```cpp
explicit messages(
    size_t _Refs = 0);

protected: messages(
    const char* _Locname,
    size_t _Refs = 0);
```

### <a name="parameters"></a>Parametry

*_Refs*\
Celá hodnota používaná k určení typu správy paměti pro objekt.

*_Locname*\
Název národního prostředí.

### <a name="remarks"></a>Poznámky

Možné hodnoty parametru *_Refs* a jejich význam jsou:

- 0: Životnost objektu je spravována národními prostředími, které jej obsahují.

- 1: Životnost objektu musí být spravována ručně.

- \>1: Tyto hodnoty nejsou definovány.

Nejsou možné žádné přímé příklady, protože destruktor je chráněn.

Konstruktor inicializuje svůj základní objekt pomocí **národního prostředí::**[omezující stolku](../standard-library/locale-class.md#facet_class)( `_Refs`).

## <a name="messagesopen"></a><a name="open"></a>zprávy::otevřít

Otevře katalog zpráv.

```cpp
catalog open(
    const string& _Catname,
    const locale& _Loc) const;
```

### <a name="parameters"></a>Parametry

*_Catname*\
Název katalogu, který má být prohledán.

*_Loc*\
Národní prostředí vyhledávané v katalogu.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu, která porovnává méně než nula na selhání. V opačném případě vrácená hodnota může být použit jako první argument na pozdější volání [získat](#get).

### <a name="remarks"></a>Poznámky

Členská funkce vrátí `_Catname` `_Loc` [do_open](#do_open)( , ).

## <a name="messagesstring_type"></a><a name="string_type"></a>zprávy::string_type

Typ, který popisuje řetězec `basic_string` typu obsahující znaky `CharType`typu .

```cpp
typedef basic_string<CharType, Traits, Allocator> string_type;
```

### <a name="remarks"></a>Poznámky

Typ popisuje specializaci šablony třídy [basic_string,](../standard-library/basic-string-class.md) jejichž objekty mohou ukládat kopie sekvencí zpráv.

## <a name="see-also"></a>Viz také

[\<>národního prostředí](../standard-library/locale.md)\
[messages_base třída](../standard-library/messages-base-class.md)\
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
