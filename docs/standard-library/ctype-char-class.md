---
title: ctype&lt;char&gt; třída | Microsoft Docs
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
ms.openlocfilehash: edbc96419e68cf584222e4008f58fd96169b2fb9
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33845996"
---
# <a name="ctypeltchargt-class"></a>ctype&lt;char&gt; – třída

Třída je explicitní specializace šablon třídy **ctype\<CharType**> na typ `char`, popisující objekt, který může sloužit jako omezující vlastnost národního prostředí a charakterizovat různé vlastnosti znaku typu `char`.

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

- Objekt ctype – třída < `char`> ukládá ukazatel na první prvek tabulky maska ctype, pole uchar_max – + 1 elementy typu **ctype_base::mask**. Ukládá také objekt logická hodnota určující, zda mají být odstraněny pole (pomocí `operator delete[]`) Pokud ctype\< **Elem**> zničena objektu.

- Jeho jediný konstruktor public, který umožňuje určit **kartě**, tabulce maska ctype a **del**, logická hodnota objektu, která je hodnota true, pokud by měl být pole odstraněna, když ctype < `char`> zničena objektu , a také parametr počet odkazů, odolný systém souborů.

- Chráněný člen funkce **tabulky** vrátí tabulku masky uložená ctype.

- Objekt statický člen **table_size** Určuje minimální počet elementů v tabulce ctype masky.

- Funkce chráněné statický člen **classic_table**(Tabulka maska ctype vrátí vhodné národního prostředí "C".

- Neexistují žádné chráněné virtuální členské funkce [do_is –](../standard-library/ctype-class.md#do_is), [do_scan_is –](../standard-library/ctype-class.md#do_scan_is), nebo [do_scan_not –](../standard-library/ctype-class.md#do_scan_not). Odpovídající veřejný členské funkce proveďte ekvivalentní operace sami.

Členské funkce [do_narrow –](../standard-library/ctype-class.md#do_narrow) a [do_widen –](../standard-library/ctype-class.md#do_widen) kopírovat prvky v nezměněném stavu.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<národní prostředí >

**Namespace:** – std

## <a name="see-also"></a>Viz také

[facet – třída](http://msdn.microsoft.com/Library/dd4f12f5-cb1b-457f-af56-2fb204216ec1)<br/>
[ctype_base – třída](../standard-library/ctype-base-class.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
