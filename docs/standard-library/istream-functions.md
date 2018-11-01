---
title: '&lt;IStream&gt; funkce'
ms.date: 11/04/2016
f1_keywords:
- istream/std::swap
- istream/std::ws
ms.assetid: 0301ea0d-4ded-4841-83dd-4253b55b3188
ms.openlocfilehash: b590559b01bb8f5db21fca9f78d220d8bad5c27e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50537641"
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

*doleva*<br/>
Datový proud.

*doprava*<br/>
Datový proud.

## <a name="ws"></a>  ws

Přeskočí prázdné místo v datovém proudu.

```cpp
template class<Elem, Tr> basic_istream<Elem, Tr>& ws(basic_istream<Elem, Tr>& _Istr);
```

### <a name="parameters"></a>Parametry

*_Istr*<br/>
Datový proud.

### <a name="return-value"></a>Návratová hodnota

Datový proud.

### <a name="remarks"></a>Poznámky

Manipulátor extrahuje a zahodí všechny prvky `ch` pro kterou [use_facet](../standard-library/basic-filebuf-class.md#open)< **ctype** \< **Elem**>> ( [getloc –](../standard-library/ios-base-class.md#getloc)). **je**( **ctype** \< **Elem**>:: **místo**, **ch**) má hodnotu true.

Volání funkcí [setstate](../standard-library/basic-ios-class.md#setstate)( **eofbit**), pokud dojde při extrahování prvků konec souboru. Vrátí *_Istr*.

### <a name="example"></a>Příklad

Zobrazit [operátor >>](../standard-library/istream-operators.md#op_gt_gt) pro příklad použití `ws`.

## <a name="see-also"></a>Viz také:

[\<IStream >](../standard-library/istream.md)<br/>
