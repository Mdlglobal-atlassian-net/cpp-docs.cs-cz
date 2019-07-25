---
title: gslice_array – třída
ms.date: 11/04/2016
f1_keywords:
- valarray/std::gslice_array
helpviewer_keywords:
- gslice_array class
ms.assetid: ad1b4514-b14a-4baf-a293-d5a8e8674c75
ms.openlocfilehash: 37c54d09fdfe920c832c4baa7984fee4e090d04a
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68448922"
---
# <a name="gslicearray-class"></a>gslice_array – třída

Interní pomocná třída šablony, která podporuje obecné objekty řezů tím, že poskytuje operace mezi podmnožinami, které jsou definovány v obecné výseči valarray.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Type>
class gslice_array : public gsplice {
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

Třída popisuje objekt `va` , který ukládá odkaz na objekt třídy [valarray](../standard-library/valarray-class.md) **\<typu >** společně s objektem `gs` třídy [gslice](../standard-library/gslice-class.md) , který popisuje sekvenci prvků, ze kterých se má vybírat. `valarray<Type>` objekt.

Objekt vytváříte pouze pomocí zápisu výrazu ve formě [VA&#91;GS&#93;.](../standard-library/valarray-class.md#op_at) `gslice_array<Type>` Členské funkce třídy gslice_array se pak chovají jako odpovídající signatury funkce definované pro `valarray<Type>`, s tím rozdílem, že jsou ovlivněny pouze sekvence vybraných elementů.

Třída šablony je vytvořena nepřímo některými valarray operacemi a nelze ji použít přímo v programu. Operátor dolního indexu řezu používá místo toho interní pomocnou třídu:

`gslice_array`\<**Typ** >  **Zadejte >** : :`operator[]` ( **constgslice &** ). `valarray` \<

Objekt vytvoříte pouze tak, že zapíšete výraz formuláře `va[gsl]`pro řez `gsl` valarray `va`. `gslice_array<Type>` Členské funkce třídy gslice_array se pak chovají jako odpovídající signatury funkce definované pro `valarray<Type>`, s tím rozdílem, že jsou ovlivněny pouze sekvence vybraných elementů. Sekvence řízená gslice_array je definována třemi parametry konstruktoru řezu, indexem prvního prvku v prvním řezu, počtem prvků v jednotlivých výsečích a vzdáleností mezi prvky v jednotlivých výsečích.

V následujícím příkladu:

```cpp
const size_t lv[] = {2, 3};
const size_t dv[] = {7, 2};
const valarray<size_t> len(lv, 2), str(dv, 2);

// va[gslice(3, len, str)] selects elements with
//   indices 3, 5, 7, 10, 12, 14
```

Indexy musí být platné, aby byl postup platný.

## <a name="example"></a>Příklad

Příklad, jak deklarovat a používat slice_array, naleznete v příkladu pro [gslice:: gslice](../standard-library/gslice-class.md#gslice) .

## <a name="requirements"></a>Požadavky

**Hlavička:** \<valarray >

**Obor názvů:** std

## <a name="see-also"></a>Viz také:

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
