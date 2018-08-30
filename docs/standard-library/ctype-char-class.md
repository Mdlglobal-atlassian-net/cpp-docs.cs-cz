---
title: ctype&lt;char&gt; třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- ctype<char>
- locale/std::ctype<char>
dev_langs:
- C++
helpviewer_keywords:
- ctype<char> class
ms.assetid: ee30acb4-a743-405e-b3d4-13602092da84
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: faed3af6595b37146bfd565e09e9ceeea3ca5d73
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43217651"
---
# <a name="ctypeltchargt-class"></a>ctype&lt;char&gt; třídy

Explicitní specializace šablony třídy je třída `ctype\<CharType>` na typ **char**, popisující objekt, který může sloužit jako omezující vlastnost národního prostředí k charakterizaci různých vlastností znaku typu **char**.

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

- Objekt třídy ctype < `char`> uchovává ukazatel na první prvek ctype maska tabulku, pole UCHAR_MAX + 1 prvků typu `ctype_base::mask`. Také ukládá logická objekt, který označuje, zda pole by měla být odstraněna (pomocí `operator delete[]`) při ctype\< **Elem**> objekt zničen.

- Jeho jediný veřejný konstruktor umožňuje určit `tab`, maska tabulce ctype a `del`, Booleovským objektem, který má hodnotu true, pokud má být pole odstranit, když ctype < `char`> objekt je zničen, a také počet odkazů Parametr odolný systém souborů.

- Chráněný člen funkce `table` vrátí tabulku masky uložená ctype.

- Statický člen objektu `table_size` Určuje minimální počet prvků v tabulce maska ctype.

- Chráněné statickou členskou funkci `classic_table`(Tabulka maska ctype vrátí odpovídající národní prostředí "C".

- Neexistují žádné chráněná virtuální členská funkce [do_is –](../standard-library/ctype-class.md#do_is), [do_scan_is –](../standard-library/ctype-class.md#do_scan_is), nebo [do_scan_not –](../standard-library/ctype-class.md#do_scan_not). Odpovídající veřejné členské funkce provádět ekvivalentní operace sami.

Členské funkce [do_narrow –](../standard-library/ctype-class.md#do_narrow) a [do_widen –](../standard-library/ctype-class.md#do_widen) kopírovat prvky v nezměněném stavu.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<národní prostředí >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[facet – třída](locale-class.md#facet_class)<br/>
[ctype_base – třída](../standard-library/ctype-base-class.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
