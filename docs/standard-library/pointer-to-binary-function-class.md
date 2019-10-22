---
title: pointer_to_binary_function – třída
ms.date: 02/21/2019
f1_keywords:
- functional/std::pointer_to_binary
helpviewer_keywords:
- pointer_to_binary_function function
- pointer_to_binary_function class
ms.assetid: fb50599f-bcb3-4076-a669-6dcc3eb189a5
ms.openlocfilehash: 890ebb7d4c2b8fbd51a4460e21efba3e763ead7e
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2019
ms.locfileid: "72687190"
---
# <a name="pointer_to_binary_function-class"></a>pointer_to_binary_function – třída

Převede ukazatel na binární funkci na přizpůsobitelnou binární funkci. Zastaralé v C++ 11, odebrané v C++ 17.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Arg1, class Arg2, class Result>
class pointer_to_binary_function
    : public binary_function <Arg1, Arg2, Result>
{
    explicit pointer_to_binary_function(
        Result(*pfunc)(Arg1, Arg2));
    Result operator()(Arg1 left, Arg2 right) const;
};
```

### <a name="parameters"></a>Parametry

*pfunc* \
Binární funkce, která má být převedena.

*levý* \
Levý objekt, na kterém je volána *\*pfunc* .

*pravé* \
Pravý objekt, na kterém je volána *\*pfunc* .

## <a name="return-value"></a>Návratová hodnota

Šablona třídy uchovává kopii `pfunc`. Definuje jeho členskou funkci `operator()` jako vrácení `(* pfunc)(Left, right)`.

## <a name="remarks"></a>Poznámky

Ukazatel binární funkce je objekt funkce a může být předán jakémukoli C++ standardnímu algoritmu knihovny, který jako parametr očekává binární funkci, ale nelze ji upravit. Chcete-li ji použít s adaptérem, jako je například vazba hodnoty na ni nebo pomocí operátoru negace, musí být zadána s vnořenými typy `first_argument_type`, `second_argument_type` a `result_type`, které tuto úpravu umožňují. Převod pomocí `pointer_to_binary_function` umožňuje adaptivním funkcím pracovat s ukazateli binárních funkcí.

## <a name="example"></a>Příklad

Konstruktor `pointer_to_binary_function` se zřídka používá přímo. Podívejte se na pomocnou funkci [ptr_fun](../standard-library/functional-functions.md#ptr_fun) , která ukazuje, jak deklarovat a použít predikát `pointer_to_binary_function` adaptér.
