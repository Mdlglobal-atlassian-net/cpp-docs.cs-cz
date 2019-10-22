---
title: CType &lt;char &gt; – třída
ms.date: 11/04/2016
f1_keywords:
- ctype<char>
- locale/std::ctype<char>
helpviewer_keywords:
- ctype<char> class
ms.assetid: ee30acb4-a743-405e-b3d4-13602092da84
ms.openlocfilehash: 08bf2c5c814eaed7b409295fcf50c66577f6a5d9
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688153"
---
# <a name="ctypeltchargt-class"></a>CType &lt;char &gt; – třída

Třída je explicitní specializace šablony třídy `ctype\<CharType>` k typu **char**, popisující objekt, který může sloužit jako omezující vlastnost národního prostředí pro charakterizaci různých vlastností znaku typu **char**.

## <a name="syntax"></a>Syntaxe

```cpp
template <>
class ctype<char>
: public ctype_base
{
public:
    typedef char _Elem;
    typedef _Elem char_type;
    bool is(
    mask _Maskval,
    _Elem _Ch) const;

    const _Elem* is(
    const _Elem* first,
    const _Elem* last,
    mask* dest) const;

    const _Elem* scan_is(
    mask _Maskval,
    const _Elem* first,
    const _Elem* last) const;

    const _Elem* scan_not(
    mask _Maskval,
    const _Elem* first,
    const _Elem* last) const;

    _Elem tolower(
    _Elem _Ch) const;

    const _Elem* tolower(
    _Elem* first,
    const _Elem* last) const;

    _Elem toupper(
    _Elem _Ch) const;

    const _Elem* toupper(
    _Elem* first,
    const _Elem* last) const;

    _Elem widen(
    char _Byte) const;

    const _Elem* widen(
    const char* first,
    const char* last,
    _Elem* dest) const;

    const _Elem* _Widen_s(
    const char* first,
    const char* last,
    _Elem* dest,
    size_t dest_size) const;

    _Elem narrow(
    _Elem _Ch,
    char _Dflt = '\0') const;

    const _Elem* narrow(
    const _Elem* first,
    const _Elem* last,
    char _Dflt,
    char* dest) const;

    const _Elem* _Narrow_s(
    const _Elem* first,
    const _Elem* last,
    char _Dflt,
    char* dest,
    size_t dest_size) const;

    static locale::id& id;
    explicit ctype(
    const mask* _Table = 0,
    bool _Deletetable = false,
    size_t _Refs = 0);

protected:
    virtual ~ctype();
//other protected members
};
```

## <a name="remarks"></a>Poznámky

Explicitní specializace se liší od šablony třídy několika způsoby:

- Objekt třídy CType < `char` > ukládá ukazatel na první prvek tabulky masky CType, pole prvků UCHAR_MAX + 1 typu `ctype_base::mask`. Také ukládá logický objekt, který označuje, zda má být pole smazáno (pomocí `operator delete[]`) při zničení objektu CType \< **Elem**>.

- Jeho jediný veřejný konstruktor umožňuje zadat `tab`, tabulku masek CType a `del`, objekt Boolean, který má hodnotu true, pokud má být pole smazáno, když je objekt CType < > `char` zničen, a také parametry referenčního počtu odkazu.

- Chráněná členská funkce `table` vrátí uloženou tabulku CType masek.

- Statický členský objekt `table_size` určuje minimální počet prvků v tabulce masek CType.

- Chráněná statická členská funkce `classic_table` (vrátí tabulku masek CType, která je vhodná pro národní prostředí "C".

- Neexistují žádné chráněné virtuální členské funkce [do_is](../standard-library/ctype-class.md#do_is), [do_scan_is](../standard-library/ctype-class.md#do_scan_is)nebo [do_scan_not](../standard-library/ctype-class.md#do_scan_not). Odpovídající veřejné členské funkce provádějí ekvivalentní operace sami.

Prvky členů [do_narrow](../standard-library/ctype-class.md#do_narrow) a [do_widen](../standard-library/ctype-class.md#do_widen) kopírování nezměnily.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<locale >

**Obor názvů:** std

## <a name="see-also"></a>Viz také:

\ [třídy omezující vlastnosti](locale-class.md#facet_class)
\ [třídy ctype_base](../standard-library/ctype-base-class.md)
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
