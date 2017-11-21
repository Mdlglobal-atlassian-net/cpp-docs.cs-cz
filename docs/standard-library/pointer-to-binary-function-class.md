---
title: "pointer_to_binary_function – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: xfunctional/std::pointer_to_binary
dev_langs: C++
helpviewer_keywords:
- pointer_to_binary_function function
- pointer_to_binary_function class
ms.assetid: fb50599f-bcb3-4076-a669-6dcc3eb189a5
caps.latest.revision: "21"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 70c9d0a54976e8aa69175a730b1fcc747065d849
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="pointertobinaryfunction-class"></a>pointer_to_binary_function – třída
Převede ukazatel na binární funkci na přizpůsobitelnou binární funkci.  
  
## <a name="syntax"></a>Syntaxe  
  
```
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
  
#### <a name="parameters"></a>Parametry  
 `pfunc`  
 Binární funkce, které má být převeden.  
  
 `left`  
 Objekt levé straně, který  *\*pfunc* se volá na.  
  
 `right`  
 Právo objektu, který  *\*pfunc* se volá na.  
  
## <a name="return-value"></a>Návratová hodnota  
 Šablony třídy ukládá kopie **pfunc**. Definuje jeho – členská funkce `operator()` jako vrácení (\* **pfunc**) (_ *doleva*, \_ *vpravo*).  
  
## <a name="remarks"></a>Poznámky  
 Ukazatel na funkci binární je objekt funkce, může předat libovolný algoritmus standardní knihovna C++, která očekává binární funkce jako parametr, ale není přizpůsobitelné. Pro použití s adaptéru, jako je vytvoření vazby hodnotu nebo pomocí negator, je nutné zadat s vnořené typy **first_argument_type**, **second_argument_type**, a **result_type**  , umožňují takové přizpůsobit. Převod podle `pointer_to_binary_function` umožňuje adaptéry funkce pro práci s ukazatelů na funkce binární.  
  
## <a name="example"></a>Příklad  
 Konstruktoru `pointer_to_binary_function` je používána zřídka přímo. Najdete v článku o podpůrné funkci [ptr_fun –](../standard-library/functional-functions.md#ptr_fun) příklad toho, jak deklarace a používání `pointer_to_binary_function` adaptéru predikátu.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<funkční >  
  
 **Namespace:** – std  
  
## <a name="see-also"></a>Viz také  
 [Standardní C++ – referenční dokumentace knihoven](../standard-library/cpp-standard-library-reference.md)



