---
title: const_mem_fun1_ref_t – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- xfunctional/std::const_mem_fun1_ref_t
dev_langs:
- C++
helpviewer_keywords:
- const_mem_fun1_ref_t class
ms.assetid: 8220d373-fa1c-44be-a21d-96d49b3ea6bb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c465ce95ecbf2ecb50e79e6e4cbaafce8cf7a407
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="constmemfun1reft-class"></a>const_mem_fun1_ref_t – třída

Třídu adaptér, který umožňuje **const** – členská funkce, které přijímá jeden argument, která se má volat jako objekt binární funkce při inicializaci s argumentem odkaz.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Result, class Type, class Arg>
class const_mem_fun1_ref_t
 : public binary_function<Type, Arg, Result>
 {
    explicit const_mem_fun1_ref_t(Result (Type::* Pm)(Arg) const);
    Result operator()(const Type& left, Arg right) const;
 };
```

### <a name="parameters"></a>Parametry

`Pm` Ukazatel na funkci člena třídy **typ** má být převeden na objekt funkce.

`left` **Const** objektu, který `Pm` – členská funkce je volána v.

`right` Argument, který se na `Pm`.

## <a name="return-value"></a>Návratová hodnota

Přizpůsobitelné binární funkce.

## <a name="remarks"></a>Poznámky

Šablony třídy ukládá kopie `Pm`, která musí být ukazatel na funkci člena třídy **typu**, v objektu privátního člena. Definuje jeho – členská funkce `operator()` jako vrácení ( `left`.\* *PM*) ( `right`) **const**.

## <a name="example"></a>Příklad

Konstruktoru `const_mem_fun1_ref_t` se obvykle nepoužívá přímo; pomocné funkce `mem_fun_ref` slouží k přizpůsobení členské funkce. V tématu [mem_fun_ref –](../standard-library/functional-functions.md#mem_fun_ref) příklady, jak používat funkce adaptéry člen.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<funkční >

**Namespace:** – std

## <a name="see-also"></a>Viz také

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)<br/>
