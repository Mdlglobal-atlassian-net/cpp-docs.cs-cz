---
title: pointer_to_unary_function – třída
ms.date: 02/21/2019
f1_keywords:
- functional/std::pointer_to_unary
helpviewer_keywords:
- pointer_to_unary_function function
- pointer_to_unary_function class
ms.assetid: 05600207-b916-4759-beca-6b6facd2d6f6
ms.openlocfilehash: 2b6bf82faa39e22c5af584a9fc3ebf68f5851463
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689144"
---
# <a name="pointer_to_unary_function-class"></a>pointer_to_unary_function – třída

Převede ukazatel na jednočlennou funkci na přizpůsobitelnou jednočlennou funkci. Zastaralé v C++ 11, odebrané v C++ 17.

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

*pfunc* \
Binární funkce, která má být převedena.

*levý* \
Objekt, na kterém je volána *\*pfunc* .

## <a name="return-value"></a>Návratová hodnota

Šablona třídy uchovává kopii `pfunc`. Definuje jeho členskou funkci `operator()` jako vrácení (\* **pFunc**) (_ *vlevo*).

## <a name="remarks"></a>Poznámky

Unární ukazatel funkce je objekt funkce a může být předán jakémukoli C++ standardnímu algoritmu knihovny, který jako parametr očekává unární funkci, ale nelze jej upravit. Chcete-li ji použít s adaptérem, jako je například vazba hodnoty na ni nebo pomocí operátoru negace, musí být zadána s vnořenými typy `argument_type` a `result_type`, které tuto úpravu umožňují. Převod pomocí `pointer_to_unary_function` umožňuje adaptivním funkcím pracovat s ukazateli binárních funkcí.

## <a name="example"></a>Příklad

Konstruktor `pointer_to_unary_function` se zřídka používá přímo. Podívejte se na pomocnou funkci [ptr_fun](../standard-library/functional-functions.md#ptr_fun) , která ukazuje, jak deklarovat a použít predikát `pointer_to_unary_function` adaptér.
