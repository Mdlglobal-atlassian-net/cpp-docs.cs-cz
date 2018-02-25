---
title: "pointer_to_unary_function – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- xfunctional/std::pointer_to_unary
dev_langs:
- C++
helpviewer_keywords:
- pointer_to_unary_function function
- pointer_to_unary_function class
ms.assetid: 05600207-b916-4759-beca-6b6facd2d6f6
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 60aba05ea86b27b4ece5eff78ed4c28f8ac39255
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="pointertounaryfunction-class"></a>pointer_to_unary_function – třída
Převede ukazatel na jednočlennou funkci na přizpůsobitelnou jednočlennou funkci.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class Arg, class Result>
class pointer_to_unary_function
    : public unary_function<Arg, Result>
{
public:
    explicit pointer_to_unary_function(Result(*pfunc)(Arg));
    Result operator()(Arg left) const;
};
```  
  
#### <a name="parameters"></a>Parametry  
 `pfunc`  
 Binární funkce, které má být převeden.  
  
 `left`  
 Objekt,  *\*pfunc* se volá na.  
  
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
 [Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)



