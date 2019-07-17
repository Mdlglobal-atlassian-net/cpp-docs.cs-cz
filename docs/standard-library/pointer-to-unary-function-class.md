---
title: pointer_to_unary_function – třída
ms.date: 02/21/2019
f1_keywords:
- functional/std::pointer_to_unary
helpviewer_keywords:
- pointer_to_unary_function function
- pointer_to_unary_function class
ms.assetid: 05600207-b916-4759-beca-6b6facd2d6f6
ms.openlocfilehash: cff84f1f15eea34c60162f702dfe05350d1383d1
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2019
ms.locfileid: "68240468"
---
# <a name="pointertounaryfunction-class"></a>pointer_to_unary_function – třída

Převede ukazatel na jednočlennou funkci na přizpůsobitelnou jednočlennou funkci. Zastaralé v C ++ 11, v C ++ 17 odebrané.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Arg, class Result>
class pointer_to_unary_function
    : public unary_function<Arg, Result>
{
    explicit pointer_to_unary_function(Result(*pfunc)(Arg));
    Result operator()(Arg left) const;
};
```

### <a name="parameters"></a>Parametry

*pfunc*\
Binární funkce pro převod.

*doleva*\
Objekt, který  *\*pfunc* je volán na.

## <a name="return-value"></a>Návratová hodnota

Třída šablony ukládá kopie `pfunc`. Definuje jeho členskou funkci `operator()` jako vracející (\* **pfunc**) (_ *vlevo*).

## <a name="remarks"></a>Poznámky

Ukazatel na funkci unární je objekt funkce a může být předán s libovolným algoritmem standardní knihovny C++, který očekává unární funkci jako parametr, ale není přizpůsobitelné. Pro použití s adaptér, jako jsou k němu po navázání hodnoty nebo pomocí negator, je nutné zadat s vnořené typy `argument_type` a `result_type` , které umožňují tyto úpravy. Převod pomocí `pointer_to_unary_function` umožňuje adaptérů funkce pro práci s ukazateli binární funkce.

## <a name="example"></a>Příklad

Konstruktor třídy `pointer_to_unary_function` je zřídka se používá přímo. Viz pomocná funkce [ptr_fun –](../standard-library/functional-functions.md#ptr_fun) příklad toho, jak deklarovat a použít `pointer_to_unary_function` adaptér predikátu.
