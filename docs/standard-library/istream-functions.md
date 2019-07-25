---
title: '&lt;funkce&gt; IStream'
ms.date: 11/04/2016
f1_keywords:
- istream/std::swap
- istream/std::ws
ms.assetid: 0301ea0d-4ded-4841-83dd-4253b55b3188
ms.openlocfilehash: fc512558969bc25d2b16afa2b93219e13d0b28ca
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68458763"
---
# <a name="ltistreamgt-functions"></a>&lt;funkce&gt; IStream

|||
|-|-|
|[swap](#istream_swap)|[ws](#ws)|

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

*zbývá*\
Datový proud.

*Kliknutím*\
Datový proud.

## <a name="ws"></a>  ws

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

Manipulátor extrahuje a zahodí `ch` všechny prvky, pro které [use_facet](../standard-library/basic-filebuf-class.md#open)< **CType** \< **elem**> > ( [getloc](../standard-library/ios-base-class.md#getloc)). **je** ( **CType** \< **elem**>:: **Space**, **ch**) má hodnotu true.

Funkce volá [setstate](../standard-library/basic-ios-class.md#setstate)( **eofbit**), pokud při extrakci prvků narazí na konec souboru. Vrátí *_Istr*.

### <a name="example"></a>Příklad

Příklad použití `ws`prvku naleznete v tématu [operátor > >](../standard-library/istream-operators.md#op_gt_gt) .

## <a name="see-also"></a>Viz také:

[\<IStream >](../standard-library/istream.md)
