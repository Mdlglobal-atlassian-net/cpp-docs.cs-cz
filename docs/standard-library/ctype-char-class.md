---
title: Třída&lt;CType&gt; char
ms.date: 11/04/2016
f1_keywords:
- ctype<char>
- locale/std::ctype<char>
helpviewer_keywords:
- ctype<char> class
ms.assetid: ee30acb4-a743-405e-b3d4-13602092da84
ms.openlocfilehash: 7fe1eef32741d63e7b2e2c2320d18f445784c44f
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68455456"
---
# <a name="ctypeltchargt-class"></a>Třída&lt;CType&gt; char

Třída je explicitní specializace třídy `ctype\<CharType>` šablony pro typ **char**, popisující objekt, který může sloužit jako omezující vlastnost národního prostředí pro charakterizaci různých vlastností znaku typu **char**.

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

Explicitní specializace se liší od třídy šablony několika způsoby:

- Objekt třídy CType < `char`> ukládá ukazatel na první prvek tabulky masky CType, pole UCHAR_MAX + 1 prvky typu. `ctype_base::mask` Také ukládá logický objekt, který označuje, zda má být pole smazáno (pomocí `operator delete[]`), když je\< objekt CType **elem**> zničen.

- Jeho jediný veřejný konstruktor umožňuje zadat `tab`, tabulku masky CType a `del`objekt Boolean, který má hodnotu true, pokud má být pole smazáno při zničení objektu CType < `char`> a také podle počtu odkazů. parametry ReFS.

- Chráněná členská `table` funkce vrátí uloženou tabulku CType masek.

- Statický členský objekt `table_size` určuje minimální počet prvků v tabulce CType masek.

- Chráněná statická členská `classic_table`funkce (vrátí tabulku masek CType, která je vhodná pro národní prostředí "C".

- Neexistují žádné chráněné virtuální členské funkce [do_is](../standard-library/ctype-class.md#do_is), [do_scan_is](../standard-library/ctype-class.md#do_scan_is)nebo [do_scan_not](../standard-library/ctype-class.md#do_scan_not). Odpovídající veřejné členské funkce provádějí ekvivalentní operace sami.

Prvky členů [do_narrow](../standard-library/ctype-class.md#do_narrow) a [do_widen](../standard-library/ctype-class.md#do_widen) kopírování nezměnily.

## <a name="requirements"></a>Požadavky

**Hlavička:** \<> národního prostředí

**Obor názvů:** std

## <a name="see-also"></a>Viz také:

[Face – třída](locale-class.md#facet_class)\
[ctype_base – třída](../standard-library/ctype-base-class.md)\
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
