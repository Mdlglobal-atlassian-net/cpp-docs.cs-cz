---
title: "const_mem_fun_ref_t – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- xfunctional/std::const_mem_fun_ref_t
dev_langs:
- C++
helpviewer_keywords:
- const_mem_fun_ref_t class
ms.assetid: 316ddbaa-9f46-4931-8eba-ea4ca66360ef
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5ca482ce3de30b83ebe8f44c6d05a2b33f278328
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="constmemfunreft-class"></a>const_mem_fun_ref_t – třída
Třídu adaptér, který umožňuje **const** – členská funkce, které nepřijímá žádné argumenty, která se má volat jako objekt funkce unární při inicializaci s argumentem odkaz.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class Result, class Type>
class const_mem_fun_ref_t
 : public unary_function<Type, Result>  
{
    explicit const_mem_fun_t(Result (Type::* Pm)() const);
    Result operator()(const Type& left) const;
 };
```  
  
#### <a name="parameters"></a>Parametry  
 `Pm`  
 Ukazatel na funkci člena třídy **typ** má být převeden na objekt funkce.  
  
 `left`  
 Objekt, `Pm` – členská funkce je volána v.  
  
## <a name="return-value"></a>Návratová hodnota  
 Přizpůsobitelné unární funkce.  
  
## <a name="remarks"></a>Poznámky  
 Šablony třídy ukládá kopie `Pm`, která musí být ukazatel na funkci člena třídy **typu**, v objektu privátního člena. Definuje jeho – členská funkce `operator()` jako vrácení ( **levém**.\* `Pm`) () **const**.  
  
## <a name="example"></a>Příklad  
 Konstruktoru `const_mem_fun_ref_t` se obvykle nepoužívá přímo; pomocné funkce `mem_fun_ref` slouží k přizpůsobení členské funkce. V tématu [mem_fun_ref –](../standard-library/functional-functions.md#mem_fun_ref) příklad použití členské funkce adaptéry.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<funkční >  
  
 **Namespace:** – std  
  
## <a name="see-also"></a>Viz také  
 [Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)



