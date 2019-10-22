---
title: gslice_array – třída
ms.date: 11/04/2016
f1_keywords:
- valarray/std::gslice_array
helpviewer_keywords:
- gslice_array class
ms.assetid: ad1b4514-b14a-4baf-a293-d5a8e8674c75
ms.openlocfilehash: 68ce774128395e941ff80580a02c4ee28a74a4e4
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689600"
---
# <a name="gslice_array-class"></a>gslice_array – třída

Interní pomocná šablona třídy, která podporuje obecné objekty řezů poskytnutím operací mezi poli podmnožiny, které jsou definovány obecným řezem valarray.

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

Třída popisuje objekt, který ukládá odkaz na objekt `va` třídy [valarray](../standard-library/valarray-class.md)  **\<Type >** , společně s objektem `gs` třídy [gslice](../standard-library/gslice-class.md) , který popisuje sekvenci prvků, které se mají vybrat z objektu `valarray<Type>`.

Objekt `gslice_array<Type>` vytvoříte pouze pomocí zápisu výrazu ve formě [VA&#91;GS&#93;](../standard-library/valarray-class.md#op_at). Členské funkce třídy gslice_array se pak chovají stejně jako odpovídající signatura funkce definované pro `valarray<Type>`, s tím rozdílem, že jsou ovlivněny pouze sekvence vybraných elementů.

Šablona třídy je vytvořena nepřímo některými valarray operacemi a nelze ji použít přímo v programu. Místo toho se používá interní šablona pomocné třídy pro operátor dolního indexu řezu:

**typ** `gslice_array` \< >  `valarray` \< **typ**>:: `operator[]` ( **constgslice &** ).

Objekt `gslice_array<Type>` vytvoříte pouze tak, že zapíšete výraz `va[gsl]` formuláře pro průřez `gsl` `va` valarray. Členské funkce třídy gslice_array se pak chovají stejně jako odpovídající signatura funkce definované pro `valarray<Type>`, s tím rozdílem, že jsou ovlivněny pouze sekvence vybraných elementů. Sekvence řízená gslice_array je definována třemi parametry konstruktoru řezu, indexem prvního prvku v prvním řezu, počtem prvků v jednotlivých výsečích a vzdáleností mezi prvky v jednotlivých výsečích.

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

**Záhlaví:** \<valarray >

**Obor názvů:** std

## <a name="see-also"></a>Viz také:

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
