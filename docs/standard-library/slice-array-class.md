---
title: slice_array – třída
ms.date: 11/04/2016
f1_keywords:
- valarray/std::slice_array
helpviewer_keywords:
- slice_array class
ms.assetid: a182d5f7-f35c-4e76-86f2-b5ac64ddc846
ms.openlocfilehash: 9577447b2201c1c9e53192b99abad1979f45d15f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50467204"
---
# <a name="slicearray-class"></a>slice_array – třída

Třída interní, pomocné šablony, která podporuje objekty řez tím, že poskytuje operace mezi dílčí pole určené řezu valarray –.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Type>
class slice_array : public slice {
public:
    typedef Type value_type;
    void operator=(const valarray<Type>& x) const;
    void operator=(const Type& x) const;
    void operator*=(const valarray<Type>& x) const;
    void operator/=(const valarray<Type>& x) const;
    void operator%=(const valarray<Type>& x) const;
    void operator+=(const valarray<Type>& x) const;
    void operator-=(const valarray<Type>& x) const;
    void operator^=(const valarray<Type>& x) const;
    void operator&=(const valarray<Type>& x) const;
    void operator|=(const valarray<Type>& x) const;
    void operator<<=(const valarray<Type>& x) const;
    void operator>>=(const valarray<Type>& x) const;
    // The rest is private or implementation defined
}
```

## <a name="remarks"></a>Poznámky

Tato třída popisuje objekt, který uchovává odkaz na objekt třídy [valarray](../standard-library/valarray-class.md)**\<typ >**, spolu s objekt třídy [řez](../standard-library/slice-class.md), který Popisuje pořadí prvků, které mají vybrat z **valarray\<typ >** objektu.

Třída šablony je nepřímo vytvořil určité valarray – operace a nelze jej použít přímo v aplikaci. Interní, pomocné šablony třídy, který používá operátor dolního indexu řez:

`slice_array`\< **Typ**> `valarray`< **typ**:: `operator[]` ( `slice`).

Můžete vytvořit `slice_array<Type>` pouze v případě, že napíšeme výrazu v podobě [posouzení ohrožení zabezpečení&#91;sl&#93;](../standard-library/valarray-class.md#op_at), řezu `sl` z valarray `va`. Členské funkce třídy slice_array – potom chovají jako odpovídající funkce podpisy definované pro `valarray<Type>`, s tím rozdílem, že má vliv jenom pořadí vybraných elementů. Sekvence řízenou parametrem slice_array – je definován pomocí tří parametrů volanému konstruktoru řez, index prvního prvku v řez, počet prvků a vzdálenost mezi prvky. Slice_array – vyjmout z valarray `va` deklaroval **posouzení ohrožení zabezpečení**[ `slice`(2, 5, 3)] vybere prvků s indexy 2, 5, 8, 11 a 14 z `va`. Indexy musí být platný postup, jak platit.

## <a name="example"></a>Příklad

Podívejte se na příklad pro [slice::slice](../standard-library/slice-class.md#slice) příklad toho, jak deklarovat a použít slice_array –.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<valarray – >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
