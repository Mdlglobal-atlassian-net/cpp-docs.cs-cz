---
title: slice_array – třída
ms.date: 11/04/2016
f1_keywords:
- valarray/std::slice_array
helpviewer_keywords:
- slice_array class
ms.assetid: a182d5f7-f35c-4e76-86f2-b5ac64ddc846
ms.openlocfilehash: 358348a57b823fcea82cd296967c83778819361d
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688964"
---
# <a name="slice_array-class"></a>slice_array – třída

Interní pomocná šablona třídy, která podporuje objekty řezů poskytnutím operací mezi poli podmnožiny, které jsou definovány v řezu valarray.

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

Třída popisuje objekt, který ukládá odkaz na objekt třídy [valarray](../standard-library/valarray-class.md)  **\<Type >** spolu s objektem [řezu](../standard-library/slice-class.md)třídy, který popisuje sekvenci prvků, které se mají vybrat z **valarray \<Type >** objekt.

Šablona třídy je vytvořena nepřímo některými valarray operacemi a nelze ji použít přímo v programu. Interní šablona pomocné třídy, kterou používá operátor dolního indexu řezu:

**typ** `slice_array` \< >  `valarray` < **typ**:: `operator[]` (`slice`).

Objekt `slice_array<Type>` vytvoříte pouze tak, že zapíšete výraz ve formátu [VA&#91;SL&#93;](../standard-library/valarray-class.md#op_at)pro průřez `sl` valarray `va`. Členské funkce třídy slice_array se pak chovají stejně jako odpovídající signatura funkce definované pro `valarray<Type>`, s tím rozdílem, že jsou ovlivněny pouze sekvence vybraných elementů. Sekvence řízená slice_array je definována třemi parametry konstruktoru řezu, indexem prvního prvku v řezu, počtem prvků a vzdáleností mezi prvky. Slice_array vyjmuté z valarray `va` deklarované pomocí **VA**[`slice` (2, 5, 3)] vybere elementy s indexy 2, 5, 8, 11 a 14 z `va`. Indexy musí být platné, aby byl postup platný.

## <a name="example"></a>Příklad

Příklad, jak deklarovat a používat slice_array, naleznete v příkladu pro [průřez:: Slice](../standard-library/slice-class.md#slice) .

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<valarray >

**Obor názvů:** std

## <a name="see-also"></a>Viz také:

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
