---
title: slice_array – třída
ms.date: 11/04/2016
f1_keywords:
- valarray/std::slice_array
helpviewer_keywords:
- slice_array class
ms.assetid: a182d5f7-f35c-4e76-86f2-b5ac64ddc846
ms.openlocfilehash: cf33c5f627a88698c84947f9b803edaebccf5566
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68450405"
---
# <a name="slicearray-class"></a>slice_array – třída

Interní pomocná třída šablony, která podporuje objekty řezu tím, že poskytuje operace mezi podmnožinou polí definovaných v řezu valarray.

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

Třída popisuje objekt, který ukládá odkaz na objekt třídy [valarray](../standard-library/valarray-class.md) **\<typu >** společně s objektem [řezu](../standard-library/slice-class.md)třídy, který popisuje sekvenci prvků, které se mají vybrat z valarray. **\<Zadejte >** Object.

Třída šablony je vytvořena nepřímo některými valarray operacemi a nelze ji použít přímo v programu. Interní pomocná třída šablony, která je používána operátorem dolního indexu řezu:

`slice_array`\<**Typ** >  **Typ:** : (`operator[]` ). `valarray` <  `slice`

Objekt vytvoříte pouze tak, že zapíšete výraz ve formátu [VA&#91;SL&#93;](../standard-library/valarray-class.md#op_at)pro `sl` řez valarray `va`. `slice_array<Type>` Členské funkce třídy slice_array se pak chovají jako odpovídající signatury funkce definované pro `valarray<Type>`, s tím rozdílem, že jsou ovlivněny pouze sekvence vybraných elementů. Sekvence řízená slice_array je definována třemi parametry konstruktoru řezu, indexem prvního prvku v řezu, počtem prvků a vzdáleností mezi prvky. Slice_array vyjmutí z valarray `va` deklarovaného pomocí VA `slice`[(2, 5, 3)] vybere prvky s indexy 2, 5, 8, 11 a 14 z. `va` Indexy musí být platné, aby byl postup platný.

## <a name="example"></a>Příklad

Příklad, jak deklarovat a používat slice_array, naleznete v příkladu pro [průřez:: Slice](../standard-library/slice-class.md#slice) .

## <a name="requirements"></a>Požadavky

**Hlavička:** \<valarray >

**Obor názvů:** std

## <a name="see-also"></a>Viz také:

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
