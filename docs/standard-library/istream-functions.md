---
title: funkce &lt;IStream&gt;
ms.date: 11/04/2016
f1_keywords:
- istream/std::swap
- istream/std::ws
ms.assetid: 0301ea0d-4ded-4841-83dd-4253b55b3188
ms.openlocfilehash: fc512558969bc25d2b16afa2b93219e13d0b28ca
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78874800"
---
# <a name="ltistreamgt-functions"></a>funkce &lt;IStream&gt;

|||
|-|-|
|[adresu](#istream_swap)|[specifikace](#ws)|

## <a name="istream_swap"></a>adresu

Vyměňuje prvky dvou objektů streamu.

```cpp
template <class Elem, class Tr>
void swap(
    basic_istream<Elem, Tr>& left,
    basic_istream<Elem, Tr>& right);

template <class Elem, class Tr>
void swap(
    basic_iostream<Elem, Tr>& left,
    basic_iostream<Elem, Tr>& right);
```

### <a name="parameters"></a>Parametry

*levý*\
Datový proud.

*pravé*\
Datový proud.

## <a name="ws"></a>specifikace

Přeskočí prázdné znaky v datovém proudu.

```cpp
template class<Elem, Tr> basic_istream<Elem, Tr>& ws(basic_istream<Elem, Tr>& _Istr);
```

### <a name="parameters"></a>Parametry

*_Istr*\
Datový proud.

### <a name="return-value"></a>Návratová hodnota

Datový proud.

### <a name="remarks"></a>Poznámky

Manipulátor extrahuje a zahodí všechny prvky `ch`, pro které [use_facet](../standard-library/basic-filebuf-class.md#open)< **ctype**\< **elem**> > ( [getloc](../standard-library/ios-base-class.md#getloc)). **je**( **ctype**\< **elem**>:: **Space**, **ch**) má hodnotu true.

Funkce volá [setstate](../standard-library/basic-ios-class.md#setstate)( **eofbit**), pokud při extrakci prvků narazí na konec souboru. Vrátí *_Istr*.

### <a name="example"></a>Příklad

Příklad použití `ws`naleznete v tématu [operátor > >](../standard-library/istream-operators.md#op_gt_gt) .

## <a name="see-also"></a>Viz také

[\<IStream >](../standard-library/istream.md)
