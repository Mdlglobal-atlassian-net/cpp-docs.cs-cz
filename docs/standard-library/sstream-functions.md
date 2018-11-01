---
title: '&lt;sstream&gt; funkce'
ms.date: 11/04/2016
f1_keywords:
- sstream/std::swap
ms.assetid: bc9607e8-7c6b-44ef-949b-19e917b450ad
ms.openlocfilehash: f22aec854b9a1d9b7b8360cacbb08760413fa22e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50458302"
---
# <a name="ltsstreamgt-functions"></a>&lt;sstream&gt; funkce

||
|-|
|[Prohození](#sstream_swap)|

## <a name="sstream_swap"></a>  Prohození

Vymění hodnoty mezi dvěma `sstream` objekty.

```cpp
template <class Elem, class Tr, class Alloc>
void swap(
    basic_stringbuf<Elem, Tr, Alloc>& left,
    basic_stringbuf<Elem, Tr, Alloc>& right);

template <class Elem, class Tr, class Alloc>
void swap(
    basic_istringstream<Elem, Tr, Alloc>& left,
    basic_istringstream<Elem, Tr, Alloc>& right);

template <class Elem, class Tr, class Alloc>
void swap(
    basic_ostringstream<Elem, Tr, Alloc>& left,
    basic_ostringstream<Elem, Tr, Alloc>& right);

template <class Elem, class Tr, class Alloc>
void swap(
    basic_stringstream<Elem, Tr, Alloc>& left,
    basic_stringstream<Elem, Tr, Alloc>& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*doleva*|Odkaz `sstream` objektu.|
|*doprava*|Odkaz `sstream` objektu.|

### <a name="remarks"></a>Poznámky

Funkce šablony provede `left.swap(right)`.

## <a name="see-also"></a>Viz také:

[\<sstream >](../standard-library/sstream.md)<br/>
