---
title: gslice_array – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- valarray/std::gslice_array
dev_langs:
- C++
helpviewer_keywords:
- gslice_array class
ms.assetid: ad1b4514-b14a-4baf-a293-d5a8e8674c75
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0f88957ac4c9ce14d05a71c266607e499c512541
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50059035"
---
# <a name="gslicearray-class"></a>gslice_array – třída

Interní, pomocné šablony třídy, který podporuje obecné řez objektů zadáním mezi dílčí pole určené obecné řezu valarray – operace.

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

Tato třída popisuje objekt, který uchovává odkaz na objekt `va` třídy [valarray](../standard-library/valarray-class.md)**\<typ >**, spolu s objektem `gs` třídy [ gslice –](../standard-library/gslice-class.md) vystihuje řadu prvků, můžete vybírat z `valarray<Type>` objektu.

Můžete vytvořit `gslice_array<Type>` pouze v případě, že napíšeme výrazu v podobě [posouzení ohrožení zabezpečení&#91;gs&#93;](../standard-library/valarray-class.md#op_at). Členské funkce třídy gslice_array – potom chovají jako odpovídající funkce podpisy definované pro `valarray<Type>`, s tím rozdílem, že má vliv jenom pořadí vybraných elementů.

Třída šablony je nepřímo vytvořil určité valarray – operace a nelze jej použít přímo v aplikaci. Třídu šablony interní pomocné místo toho je používán operátor dolního indexu řez:

`gslice_array`\< **Typ** >  `valarray` \< **typ**>:: `operator[]` ( **constgslice &**).

Můžete vytvořit `gslice_array<Type>` pouze v případě, že napíšeme výrazu v podobě `va[gsl]`, řezu `gsl` z valarray `va`. Členské funkce třídy gslice_array – potom chovají jako odpovídající funkce podpisy definované pro `valarray<Type>`, s tím rozdílem, že má vliv jenom pořadí vybraných elementů. Sekvence řízenou parametrem gslice_array – je definován pomocí tří parametrů volanému konstruktoru řez, index prvního prvku v první řez počet prvků v každém řezu a vzdálenost mezi prvky v každém řezu.

V následujícím příkladu:

```cpp
const size_t lv[] = {2, 3};
const size_t dv[] = {7, 2};
const valarray<size_t> len(lv, 2), str(dv, 2);

// va[gslice(3, len, str)] selects elements with
//   indices 3, 5, 7, 10, 12, 14
```

Indexy musí být platný postup, jak platit.

## <a name="example"></a>Příklad

Podívejte se na příklad pro [gslice::gslice](../standard-library/gslice-class.md#gslice) příklad toho, jak deklarovat a použít slice_array –.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<valarray – >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
