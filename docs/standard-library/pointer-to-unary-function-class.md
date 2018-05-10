---
title: pointer_to_unary_function – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- xfunctional/std::pointer_to_unary
dev_langs:
- C++
helpviewer_keywords:
- pointer_to_unary_function function
- pointer_to_unary_function class
ms.assetid: 05600207-b916-4759-beca-6b6facd2d6f6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9f431542ab85b4ae540622651967f3a5520ff5f7
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="pointertounaryfunction-class"></a>pointer_to_unary_function – třída

Převede ukazatel na jednočlennou funkci na přizpůsobitelnou jednočlennou funkci.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Arg, class Result>
class pointer_to_unary_function
    : public unary_function<Arg, Result>
{
public:
    explicit pointer_to_unary_function(Result(*pfunc)(Arg));
    Result operator()(Arg left) const;
};
```

### <a name="parameters"></a>Parametry

`pfunc` Binární funkce, které má být převeden.

`left` Objekt,  *\*pfunc* se volá na.

## <a name="return-value"></a>Návratová hodnota

Šablony třídy ukládá kopie **pfunc**. Definuje jeho – členská funkce `operator()` jako vrácení (\* **pfunc**) (_ *doleva*).

## <a name="remarks"></a>Poznámky

Ukazatel na funkci unární je objekt funkce, může předat libovolný algoritmus standardní knihovna C++, který očekává unární funkce jako parametr, ale není přizpůsobitelné. Pro použití s adaptéru, jako je vytvoření vazby hodnotu nebo pomocí negator, je nutné zadat s vnořené typy **argument_type** a **result_type** , umožňují takové přizpůsobit. Převod podle `pointer_to_unary_function` umožňuje adaptéry funkce pro práci s ukazatelů na funkce binární.

## <a name="example"></a>Příklad

Konstruktoru `pointer_to_unary_function` je používána zřídka přímo. Najdete v článku o podpůrné funkci [ptr_fun –](../standard-library/functional-functions.md#ptr_fun) příklad toho, jak deklarace a používání `pointer_to_unary_function` adaptéru predikátu.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<funkční >

**Namespace:** – std

## <a name="see-also"></a>Viz také

[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)<br/>
