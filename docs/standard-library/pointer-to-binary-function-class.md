---
title: pointer_to_binary_function – třída
ms.date: 02/21/2019
f1_keywords:
- functional/std::pointer_to_binary
helpviewer_keywords:
- pointer_to_binary_function function
- pointer_to_binary_function class
ms.assetid: fb50599f-bcb3-4076-a669-6dcc3eb189a5
ms.openlocfilehash: 88d38be258c6ceb1054e0d31cc52e4d8d25186ec
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62370316"
---
# <a name="pointertobinaryfunction-class"></a>pointer_to_binary_function – třída

Převede ukazatel na binární funkci na přizpůsobitelnou binární funkci. Zastaralé v C ++ 11, v C ++ 17 odebrané.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Arg1, class Arg2, class Result>
class pointer_to_binary_function
    : public binary_function <Arg1, Arg2, Result>
{
public:
    explicit pointer_to_binary_function(
        Result(*pfunc)(Arg1, Arg2));
    Result operator()(Arg1 left, Arg2 right) const;
};
```

### <a name="parameters"></a>Parametry

*pfunc*<br/>
Binární funkce pro převod.

*doleva*<br/>
Levé straně objekt, který  *\*pfunc* je volán na.

*doprava*<br/>
Vpravo objekt, který  *\*pfunc* je volán na.

## <a name="return-value"></a>Návratová hodnota

Třída šablony ukládá kopie `pfunc`. Definuje jeho členskou funkci `operator()` jako vracející `(* pfunc)(Left, right)`.

## <a name="remarks"></a>Poznámky

Ukazatel na binární funkci je objekt funkce a může být předán s libovolným algoritmem standardní knihovny C++, který očekává binární funkci jako parametr, ale není přizpůsobitelné. Pro použití s adaptér, jako jsou k němu po navázání hodnoty nebo pomocí negator, je nutné zadat s vnořené typy `first_argument_type`, `second_argument_type`, a `result_type` , které umožňují tyto úpravy. Převod pomocí `pointer_to_binary_function` umožňuje adaptérů funkce pro práci s ukazateli binární funkce.

## <a name="example"></a>Příklad

Konstruktor třídy `pointer_to_binary_function` je zřídka se používá přímo. Viz pomocná funkce [ptr_fun –](../standard-library/functional-functions.md#ptr_fun) příklad toho, jak deklarovat a použít `pointer_to_binary_function` adaptér predikátu.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<funkční >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)<br/>
