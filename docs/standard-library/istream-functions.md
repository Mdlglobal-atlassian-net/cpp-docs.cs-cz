---
title: '&lt;IStream&gt; funkce | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- istream/std::swap
- istream/std::ws
ms.assetid: 0301ea0d-4ded-4841-83dd-4253b55b3188
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1193e7ab65c49f0f79aeae52ca6563310296116d
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38953645"
---
# <a name="ltistreamgt-functions"></a>&lt;IStream&gt; funkce

|||
|-|-|
|[Prohození](#istream_swap)|[ws](#ws)|

## <a name="istream_swap"></a>  Prohození

Vymění prvky dvou objektů datového proudu.

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

*levé* datového proudu.

*správné* datového proudu.

## <a name="ws"></a>  ws

Přeskočí prázdné místo v datovém proudu.

```cpp
template class<Elem, Tr> basic_istream<Elem, Tr>& ws(basic_istream<Elem, Tr>& _Istr);
```

### <a name="parameters"></a>Parametry

*_Istr* datového proudu.

### <a name="return-value"></a>Návratová hodnota

Datový proud.

### <a name="remarks"></a>Poznámky

Manipulátor extrahuje a zahodí všechny prvky `ch` pro kterou [use_facet](../standard-library/basic-filebuf-class.md#open)< **ctype** \< **Elem**>> ( [getloc –](../standard-library/ios-base-class.md#getloc)). **je**( **ctype** \< **Elem**>:: **místo**, **ch**) má hodnotu true.

Volání funkcí [setstate](../standard-library/basic-ios-class.md#setstate)( **eofbit**), pokud dojde při extrahování prvků konec souboru. Vrátí *_Istr*.

### <a name="example"></a>Příklad

Zobrazit [operátor >>](../standard-library/istream-operators.md#op_gt_gt) pro příklad použití `ws`.

## <a name="see-also"></a>Viz také:

[\<IStream >](../standard-library/istream.md)<br/>
